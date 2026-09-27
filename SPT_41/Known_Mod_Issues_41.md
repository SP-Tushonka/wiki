---
title: Known Mod Issues for SPT 4.1
description: Known EFT issues and possible fixes for SPT 4.1.
published: true
date: 2026-09-27T21:09:51.397Z
tags: 
editor: markdown
dateCreated: 2026-08-08T15:13:45.705Z
---

> This page applies to SPT version `4.1`
{.is-info}

## [FieldKit](https://sp-mod.com/mod/2856/fieldkit-dev-toolkit-weapon-control-lootentity-browser-spawning-esp>) does not function at all
The current version of the mod is broken. Wait for an update from the mod author.

## All item stacks are set to 1
You installed a mod made for SPT 4.0 to your SPT 4.1 install. [Uninstall it](/SPT_4x/Uninstalling_Mods). Only install versions of mods marked compatible for your version of SPT.

## Greed couldn't find `ServerValueModifier.dll` under `SPT/user/mods/[SVM] Server Value Modifier`
You didn't install SVM correctly. It's installed like any other mod. See the [Installing Mods](/SPT_4x/Installing_Mods) page on how you should install your mods.

## My flea prices are extreme when using [Live Flea Prices](https://sp-mod.com/mod/1131/live-flea-prices)
Those are the prices of items on the Live flea right now. You can check the Live flea [here](<https://tarkov.dev/>).
By default, SPT uses the base handbook price of items +/- some variance when simulating the flea.
To get "normal" flea prices:
- Wait for the Live flea prices to stabilise.
- Set `"pvePrices"` to `true` inside Live Flea Prices' config file to use the PvE Live flea prices instead.
- [Uninstall](/SPT_4x/Uninstalling_Mods) Live Flea Prices.

## When looting bodies only duplicated empty tactical rig slot appears
Update [Foldables](<https://sp-mod.com/mod/2422/foldables>).

## `[UNHANDLED][/sain/_______` errors in the Server
[Update SPT](/SPT_4x/Updating_SPT).

## Server instantly closes
It can have a number of causes:
- Update [SVM](https://sp-mod.com/mod/236/server-value-modifier-svm)
- Update [ISB Aishi](https://sp-mod.com/mod/2478/isb-aishi)
- Uninstall [23x75mm Volna-R Cartridge](https://sp-mod.com/mod/2902/23x75mm-volnar-cartridge)
- See [here](/SPT_41/Known_SPT_Issues_41#server-doesnt-launch-or-closes-immediately)

## Can only list FIR items on the Flea with [The Blacklist](https://sp-mod.com/mod/755/the-blacklist-flea-market-enhancements) installed
Set `"enableFIRFleaSelling"` to `false` in its config.


## `Unable to add item: [id], items must be added before profiles load. Lower the mods TypePriority where items are added to OnLoadOrder.Preload`
Issue present with [BensBurnedWaffles' custom ammo mods](https://sp-mod.com/user/120002/bensburnedwaffles#mods). [Uninstall](/SPT_4x/Uninstalling_Mods) them.

## [APBS](https://sp-mod.com/mod/1594/apbs-acids-progressive-bot-system)'s log grow uncontrollably in file size
Update the mod.

## `Requested value '[bot type]' was not found.` error on loading a raid
[Uninstall](/SPT_4x/Uninstalling_Mods) any outdated mods. Make sure to uninstall them from the `BepInEx\patchers` folder as well.

## Bots are frozen in place while using [ORBIT](https://sp-mod.com/mod/2706/orbit-20)
ORBIT is incompatible with any mod that limits or culls bots. [AI Limit](https://sp-mod.com/mod/1945/ai-limit) is entirely incompatible, while [ABPS](https://sp-mod.com/mod/2097/abps-acids-bot-placement-system)'s bot despawning needs to be turned off.

## `The given key '[id]' was not present in the dictionary.` server error when using [Item Info](https://sp-mod.com/mod/2430/odts-item-info-spt-40)
Add the `id` that's in the error message to `\SPT_Runtime\user\mods\ODT-ItemInfo-4.0\config\bsgblacklist.json`. Each entry should be in quotations `""`, and all entries except the last one should end with a comma `,`.

# See also
[Frequently Asked Questions for SPT 4.1](/SPT_41/FAQs_41)