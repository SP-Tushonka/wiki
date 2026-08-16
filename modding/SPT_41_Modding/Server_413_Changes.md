---
title: Server Mod Changes - 4.1.3 onwards
description: What might break for server mods after SPT 4.1.3, and how to fix it.
published: true
date: 2026-08-14T00:00:00.000Z
tags: modding, migration
editor: markdown
dateCreated: 2026-08-14T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

> If your mod adds custom items, check the first section. Adding an item too late now throws instead of quietly producing broken profiles.
{.is-warning}

A short list of changes after 4.1.3 that can break a server mod. Most mods won't need any changes at all.

## The nuget packages are now SPTushonka.*

The packages are published under `SPTushonka.*` rather than `SPTarkov.*`. Update the package references in your csproj:

```diff
- <PackageReference Include="SPTarkov.Server.Core" Version="..." />
+ <PackageReference Include="SPTushonka.Server.Core" Version="..." />
```

The same applies to `SPTushonka.Common`, `SPTushonka.DI`, `SPTushonka.Reflection`, `SPTushonka.Server.Assets` and `SPTushonka.Server.Web`.

Only the package names changed. The assemblies and namespaces are still `SPTarkov.*`, so no `using` needs touching and no code changes are needed.

## Custom items must be added before profiles load

`CustomItemService` now refuses to add an item once profile loading has started.

Adding an item late used to appear to work. The item went into the database, but on the next restart the profiles would not be able to find the item as it was added later.

You now get an exception at the point of the mistake:

```
Unable to add item: <id>, items must be added before profiles load.
Lower the mods TypePriority where items are added to OnLoadOrder.Preload
```

Move the work to `Preload`:

```csharp
[Injectable(TypePriority = OnLoadOrder.Preload)]
public class MyItems(CustomItemService customItemService) : IOnLoad
{
    public Task OnLoadAsync(CancellationToken cancellationToken)
    {
        customItemService.CreateItemFromClone(/* ... */);

        return Task.CompletedTask;
    }
}
```

The database is fully loaded by `Preload`, so there's nothing to wait for. If you were registering items at `PostLoad` because that's what 4.0 needed, that's the change to make.

## Extension data is created when you use it

The `ExtensionData` dictionary woven onto every model type used to be allocated in the constructor. It's now created the first time something reads the property.

Reading and writing are unchanged. The property is never null, and a write through it persists:

```csharp
item.AddToExtensionData("myKey", myValue);   // works as before
var data = item.GetExtensionData();          // works as before
```

What changed is `TryGetExtensionData`. Reading the property is what creates the dictionary, so the method now always returns `true` and hands back an empty dictionary rather than reporting that there wasn't one.

**Before**
```csharp
if (item.TryGetExtensionData(out var data))
{
    // only ran when the item actually carried extension data
}
```

**Now**
```csharp
if (item.TryGetExtensionData(out var data) && data!.Count > 0)
{
    // check the count instead
}
```

## AddPaymentToOutput is deprecated

`PaymentService` now spends the specific money stacks the client asked to pay with before falling back to anything else, which needs the stack ids passing through.

The old overload is marked obsolete and forwards to the new one with a null stack list, so existing calls keep working and you'll see a compiler warning rather than an error:

```diff
- AddPaymentToOutput(pmcData, currencyTpl, amountToPay, sessionID, output)
+ AddPaymentToOutput(pmcData, currencyTpl, amountToPay, sessionID, output, requestedStackIds)
```

Pass the stack ids from the request if you have them, or `null` if you don't. It'll be removed in a later version.

## The largest routes are streamed instead of returning a string

Thirteen routes no longer build their response as a JSON string. They hand the payload to the response stream and it's serialised as it's written, which is where most of the server's memory use was going. `/client/items` alone dropped from 73 MB per request to 5 MB.

The affected routes:

```
/client/items                        /client/settings
/client/dialogue                     /client/game/profile/list
/client/locale/{lang}                /client/hideout/production/recipes
/client/locations                    /client/achievement/list
/client/globals                      /client/trading/api/traderSettings
/client/customization                /client/hideout/areas
/client/handbook/templates
```

Their callbacks return `StreamedJsonBody` rather than `string`:

```diff
- public ValueTask<string> GetTemplateItems(string url, EmptyRequestData _, MongoId sessionID)
+ public ValueTask<StreamedJsonBody> GetTemplateItems(string url, EmptyRequestData _, MongoId sessionID)
  {
-     return new ValueTask<string>(httpResponseUtil.GetUnclearedBody(templateTable.Items));
+     return new ValueTask<StreamedJsonBody>(httpResponseUtil.GetStreamedBody(templateTable.Items));
  }
```

If you call one of these callbacks directly, you get a `StreamedJsonBody` and no longer a finished string. There is no string form to fall back to, by design: the whole point is that the response never exists in memory all at once.

The part that will catch people out is chaining. Registering a `RouteAction` on one of these URLs to read the previous route's output and edit it no longer works, because a streamed payload is never written to the output the next route sees:

```csharp
// output is always empty on a streamed route, so there is nothing to edit
new RouteAction<EmptyRequestData>(
    "/client/items",
    async (url, info, sessionID, output, cancellationToken) => Tweak(output)
),
```

Replacing one of these routes outright still works as it always did. A route registered after the streamed one wins, and its string is what gets sent.

If you were editing the output rather than replacing it, change the underlying data instead. Every one of these routes serialises a database table or a freshly built object, so editing `templateTable.Items` (or whatever the route returns) at load time has exactly the effect editing the JSON did, and it works for every consumer rather than one route.

Routes with responses under about 100 KB were deliberately left alone, so most routes are unaffected.

## GetResponseAsync is gone

`HttpRouter.GetResponseAsync` and `SptHttpListener.GetResponseAsync` have been removed rather than deprecated. They returned a `string`, which a streamed route cannot produce.

```diff
- var response = await httpRouter.GetResponseAsync(request, sessionId, body, cancellationToken);
+ var response = await httpRouter.GetResponseObjectAsync(request, sessionId, body, cancellationToken);
```

`GetResponseObjectAsync` returns `object`, which is either the JSON string as before or a `StreamedJsonBody`. Check the type if you need to tell them apart.

## Smaller changes

- Ragfair searches no longer throw when a search request omits `neededSearchId`. The check that read it was unreachable and has been removed.
- With tiered flea enabled, ragfair searches copy only the offers they return rather than every offer in the database. Offers handed to you are still copies, so writing to them can't corrupt the shared cache.
- `JsonUtil` gained `DeserializeFromStreamAsync`, for deserialising from any stream rather than a file path or `MemoryStream`.
- `FindAndReturnChildrenByAssort(MongoId, IEnumerable<Item>)` is obsolete. It rebuilds a lookup over the whole assort on every call, so use the overload taking one built once with `CreateParentIdLookupCache`.
- `GetItemWithChildren` gained an overload taking that same prebuilt lookup, for the same reason. The original signature is unchanged.
- The obsolete `AddPaymentToOutput` overload is covered in its own section above.
