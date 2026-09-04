---
title: Mod Changes - 4.1.4 onwards
description: What might break for client and server mods after SPT 4.1.4, and how to fix it.
published: true
date: 2026-09-04T00:00:00.000Z
tags: modding, migration
editor: markdown
dateCreated: 2026-09-04T00:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

> If your mod names any of the fields in the table below, it has to be updated for 4.1.4. Direct references break the build. Lookups by string fail at runtime instead.
{.is-warning}

A short list of changes after 4.1.4 that can break a mod, client or server. Most mods won't need any changes at all.

## Serialized field names are being reverted

### Why the names are changing

Unity writes field names into the asset bundles. On load, the name in the bundle has to match the name of the field in the assembly. If it doesn't, the value is dropped. There is no exception and no log line. The component just loads with an empty field and does nothing.

The tool that produces the deobfuscated assembly was renaming fields it should have left alone. In most cases it replaced a real name with one derived from the field's type. `AmbianceAffectedComponent.MethodName` became `String`, so every bundle carrying that component deserialised without a method name and never invoked anything. That is why the shooting range poppers and rail target controls never energize. See [server-csharp#23](https://github.com/SP-Tushonka/server-csharp/issues/23).

### The renames

| Type | Up to 4.1.3 | 4.1.4 |
| --- | --- | --- |
| `EFT.Hideout.MultiObjectAmbiance+AmbianceAffectedComponent` | `String` | `MethodName` |
| `EFT.Quests.ConditionArenaPreset` | `String` | `classIds` |
| `WsRequestJson` | `String` | `Method` |
| `WsResponseJson` | `String` | `Method` |
| `EFT.Skill` | `ESkillClass` | `Class` |
| `EFT.Settings.Sound.SoundSettingsGroup` | `_gameSetting` | `InterfaceVolume` |
| `DebugBotProfilesStructContainer` | `DebugBotProfilesStruct` | `Struct` |
| `RuntimeInspector.Debugger` | `Texture2D` | `ClassTex` |
| `RuntimeInspector.Debugger` | `Texture2D_1` | `MethodTex` |
| `RuntimeInspector.Debugger` | `Texture2D_2` | `classTex` |
| `RuntimeInspector.Debugger` | `Texture2D_3` | `methodTex` |
| `RuntimeInspector.Debugger` | `GUIStyle` | `ClassTypeStyle` |
| `RuntimeInspector.Debugger` | `GUIStyle_1` | `ClassTypeStyle2` |
| `RuntimeInspector.Debugger` | `GUIStyle_2` | `ClassTypeStyleSelected` |
| `EFT.HealthSystem.EffectsSettings+ZombieInfectionSettings` | `СumulativeTime` | `float_0` ⚠ |

### Updating your mod

Direct references are a rename.

```diff
- component.String = methodName;
+ component.MethodName = methodName;
```

Reflection by string name needs finding by hand. It compiles either way and only fails when the code runs.

```diff
- AccessTools.Field(typeof(AmbianceAffectedComponent), "String")
+ AccessTools.Field(typeof(AmbianceAffectedComponent), "MethodName")
```

If your mod ships its own asset bundles containing any of these components, they were built against the 4.1.3 names and will hit the same dropped-field problem in 4.1.4. Rebuild them against the 4.1.4 assemblies.
