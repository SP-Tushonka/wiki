---
title: FAQs for SPT 4.0
description: Answers to frequently asked questions.
published: true
date: 2026-09-08T19:07:53.990Z
tags: 
editor: markdown
dateCreated: 2026-08-08T11:22:51.246Z
---

> This page applies to SPT version `4.0`
{.is-info}

## Why are there so many files in the new `\SPT` folder?
To allow modders to use method patching, all the DLLs need to be 'loose' and not stored inside the server executable.

## Why are `SPT.Launcher` and `SPT.Server` shortcuts?
As part of the restructuring explained above.
The actual exe files are in your `[game folder]\SPT` folder, and the installer creates shortcuts in your `[game folder]` for your convenience.

## Where is my `user` folder?
Also in `[game folder]\SPT`.

## What client version of the game is SPT running?
Version `0.16.9.0.40087`, released 2 October 2025.

## Is (insert content here) in SPT now?
Refer to the previous question. If you're curious about something specific, please see the official [live game changelog](https://escapefromtarkov.fandom.com/wiki/Changelog).

## Is Labyrinth in `4.0`?
Yes. See the [official wiki](https://escapefromtarkov.fandom.com/wiki/The_Labyrinth) on how to access it.

## Is the Softcore/Hardcore wipe in SPT? 
No. The hardcore wipe only made changes to the PVP mode. SPT `4.0` is using game version `0.16.9.0.40087` which came before the softcore wipe changes were added to PVE.
You can easily recreate either using mods.

## Will `4.0` be updated to include the latest live game patches?
No. Live game patches made after the release of SPT `4.0` will only be available in SPT `4.1`.

## Is performance better in `4.0` than in `3.11`?
Short answer: A bit.
Long answer: The game received optimised culling on several maps, and alongside other changes, did somewhat improve performance between game version `0.16.1.3.35392` and `0.16.9.0.40087`. It's most noticeable if your SPT is GPU limited and will vary. The [Performance Tuning](/SPT_4x/Performance_Tuning) guide is still relevant even on `4.0`.

## Can I use my profile and mods from `3.11`?
***If*** the `3.11` profile was ***un-modded***, yes. Otherwise A new profile will be required. None of your `3.11` mods are compatible.
See the guide on [Updating SPT](/SPT_4x/Updating_SPT) for more details.

## When is (insert mod here) going to update to `4.0`?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

## Will a mod marked compatible for `4.0.0` work on future versions of `4.0`?
Mods made for previous patch versions should work on the latest version. Those that don't might have received an update to address that.
Mods known to be incompatible with be stated in [Known Mod Issues](/SPT_40/Known_Mod_Issues_40).
For an explanation of how SPT versions work and how to update your SPT, read through the [Updating SPT](/SPT_4x/Updating_SPT) Wiki page.

## Bot spawns
SPT uses the game's PvE bot spawning system. Bots will continuously spawn up to a map-specific limit. When enough are killed, more will spawn to replace them. Bot spawns aren't checked for the distance to you or other bots which can let bots can spawn next to you. 
Use a bot spawning mod like [ABPS](https://sp-mod.com/mod/2097/abps-acids-bot-placement-system) to change this system.

## Need space on your drive? Don't play live?
After you install SPT, you cannot completely uninstall your retail copy, but you can delete the `_Data` folder from your live game folder if you really need the space.

You **will** have to validate files through the retail game launcher if you need to reinstall SPT again by going into the launcher's `Game Settings` and clicking on `Integrity check`. 
On Steam right click the game and open `Properties...`, and in `Installed Files` press `Verify integrity of game files`.

## Why are bots not moving from their spawn location?
Bots are not programmed to move from their spawn location outside of combat. Only PMC bots are given tasks to loot areas, if they spawned near them. By design, bots will stand where they spawned until they spot the player. This is a design decision made by the game's developers and not SPT.

[SAIN](https://sp-mod.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement) **doesn't** make bots move around the map, as it *only* affects combat behaviour.

## SPT `5.0` for Live `1.1`
SPT wasn't going be updated to `1.0` and beyond. However, recent developments have changed that. SPT `5.0` is in development for version `1.1` of the game.
### Will all content from the `1.0` release be included?
Yes.
### Will mods made for `4.0` or `4.1` work on `5.0`?
No.
### Will there be as many mods for `5.0` as there are for `4.1`?
Definitively not. With `1.0` the game switched over to IL2CPP, which will make client mods extremely difficult to make.
### What is IL2CPP?
It's a newer, modern way of coding Unity games. The Live game switched over to it predominantly for performance improvements, **not** to hamper the development of SPT.
### Should I pester mod authors to update their mods for `5.0`?
**Absolutely not**. Most mod authors will not be porting or making mods for `5.0`. **Anyone pestering mod authors about mod updates will receive warnings, removals, or bans based on their behaviour.**

<br>

# Troubleshooting tips
- Do not install mods until you've launched SPT at least once. Verify your SPT install works, then install mods.
- Do not install out of date mods.
- Do not install multiple mods at once (unless they're dependencies). Install mods one at a time or in small batches. That way when something goes wrong, you'll know exactly what mod is responsible.
- Read mod pages. Not only is it just common courtesy to read the mod page __before__ asking for help, chances are the mod page has exactly the information you need. What the mod does, how to install it, how to use it, and known issues or incompatibility with other mods.

##### "I'm still having issues and it wasn't the last mod I installed, what do I do?" 
Start removing mods one at a time, or if you have a lot of mods, follow the [50/50 Method](/SPT_4x/5050-method>).
If none of that helps, then it's time to create a support ticket. Join our [Discord Server](https://discord.sp-tushonka.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions.

# How much free space is necessary to install SPT?
This is the current space requirements (compounding) to install SPT:
- Patcher: 8GB (Always `C:\` drive)
- Client: 70GB
- Extract/Copy Patcher: 14GB
- Post-patcher: ~35GB

So while the final install size is ~60GB, the maximum allocated for SPT and associated install files *during the install process* is ~100GB combined.

# Using 7-Zip
7-Zip is the recommended tool for opening archives. Unlike WinRAR or Windows, it will not randomly corrupt the extracted files.
You can download and install 7-Zip from [here](https://www.7-zip.org/).
### To set 7-Zip as the default program for opening archives:
1. Right click on a mod archive (`.7z`, `.zip`, `.rar`) and click `Open with`.
  - On Windows 11, you might need to click on `Show more options`.
2. Click `Choose another app`.
3. Select `7-Zip File Manager` and `Always`.
  - If 7-Zip is not on the list, click `Choose an app on your PC`, navigate to `C:\Program Files\7-Zip` and select `7zFM.exe`.

For a modern take on 7-Zip, try [NanaZip](https://github.com/rescenic/nanazip).

# Known Issues
- [Known Live Issues for SPT 4.0](/SPT_40/Known_Live_Issues_40)
- [Known SPT Issues for SPT 4.0](/SPT_40/Known_SPT_Issues_40)
- [Known Mod Issues for SPT 4.0](/SPT_40/Known_Mod_Issues_40)
