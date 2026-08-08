---
title: FAQs for SPT 4.0
description: Answers to frequently asked questions.
published: true
date: 2026-08-08T15:45:45.340Z
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
Mods made for previous hotfix versions should work on the latest version. Those that don't might have received an update to address that.
Mods known to be incompatible with be stated in the `Mod compatibility` section of SPT's [Release page](https://github.com/sp-tarkov/build/releases/tag/4.0.13) and in [Known Mod Issues](/SPT_40/Known_Mod_Issues_40).
For an explanation of how SPT versions work and how to update your SPT, read through the [Updating SPT](/SPT_4x/Updating_SPT) Wiki page.

## Bot spawns
SPT uses the game's PvE bot spawning system. Bots will continuously spawn up to a map-specific limit. When enough are killed, more will spawn to replace them. Bot spawns aren't checked for the distance to you or other bots which can let bots can spawn next to you. 
Use a bot spawning mod like [ABPS](https://sp-mod.com/mod/2097/abps-acids-bot-placement-system) to change this system.

## Need space on your drive? Don't play live?
After you install SPT, you cannot completely uninstall your retail copy, but you can delete the `_Data` folder from your live game folder if you really need the space.

You **will** have to validate files through the retail game launcher if you need to reinstall SPT again by going into the launcher's `Game Settings` and clicking on `Integrity check`. 
On Steam right click the game and open `Properties...`, and in `Installed Files` press `Verify integrity of game files`.

## RAM Usage
It's [recommended](/SPT_4x/system-requirements) to have at least 32gb of RAM to play SPT without issues.
The game has over the years become more demanding on system resources. In the past, 16gb was just enough to play without issue. Nowadays it's not.

Some people are still able to play SPT with 16gb of RAM. That's due to the pagefile, which is a cache located on your storage device. If your RAM is filling up, Windows will start moving files to and from it. It will lead to stuttering and overall lower performance, as even the fastest NVMe SSD is much slower than RAM.

For an even smaller subset of people there’s an underlying issue with their Windows install, where the pagefile does not work as intended. While this should be fixed, it can be [set manually as a temporary fix](/SPT_4x/Performance_Tuning#pagefile>).

## Why are bots not moving from their spawn location?
Bots are not programmed to move from their spawn location outside of combat. Only PMC bots are given tasks to loot areas, if they spawned near them. By design, bots will stand where they spawned until they spot the player. This is a design decision made by the game's developers and not SPT.

[SAIN](https://sp-mod.com/mod/791/sain-solarints-ai-modifications-full-ai-combat-system-replacement) **doesn't** make bots move around the map, as it *only* affects combat behaviour.

# The 1.0 Update
### Will we have `1.0` soon in SPT?
There is no active development effort targeting the retail game's `1.0` update.
### Is it possible to install SPT with `1.0`?
Yes. You can [install SPT](/SPT_4x/Installation_Guide>) while having `1.0` installed.
### Is it possible to install SPT with the Steam copy of the retail game?
Yes. See the [install guide](/SPT_4x/Installation_Guide).
### Can I update my retail copy or will that break my existing SPT install?
The installer makes a **copy** of your game client files to a **separate** location. Update your retail copy as much as you want.


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

# Known Issues
- [Known Live Game Issues for SPT 4.0](/SPT_40/Known_Live_Issues_40)
- [Known SPT Issues for SPT 4.0](/SPT_40/Known_SPT_Issues_40)
- [Known Mod Issues for SPT 4.0](/SPT_40/Known_Mod_Issues_40)
