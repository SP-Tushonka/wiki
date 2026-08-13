---
title: FAQs for SPT 4.1
description: Answers to frequently asked questions.
published: true
date: 2026-08-13T18:10:36.341Z
tags: 
editor: markdown
dateCreated: 2026-08-08T15:06:51.667Z
---

> This page applies to SPT version `4.1`
{.is-info}

# Quick troubleshooting tips
- Do not install mods until you've launched SPT at least once. Verify your SPT install works, then install mods.
- Do not install out of date mods.
- Do not install multiple mods at once (unless they're dependencies). Install mods one at a time or in small batches. That way when something goes wrong, you'll know exactly what mod is responsible.
- Read mod pages. Not only is it just common courtesy to read the mod page __before__ asking for help, chances are the mod page has exactly the information you need. What the mod does, how to install it, how to use it, and known issues or incompatibility with other mods.

- "I'm still having issues and it wasn't the last mod I installed, what do I do?" 
Start removing mods one at a time, or if you have a lot of mods, follow the [50/50 Method](/SPT_4x/5050-method). When you've identified the mod responsible, check the mod page to see if it's actually an issue or an intended feature. Check the comments section to see if anyone else reported the same problem you're experiencing. 
If none of that helps, then it's time to create a support ticket. Join our [Discord Server](https://discord.sp-tushonka.com/) and read through the [#support-guidelines](https://discord.com/channels/875684761291599922/1172733248317694022) for instructions.


## What client version of the game is SPT 4.1 running?
Version `0.16.9.5.40743`, released 22nd October 2025.

## Can I use my profile and mods from 4.0?
***If*** the `4.0` profile was ***un-modded***, yes. Otherwise a new profile will be required. None of your `4.0` mods are compatible.
See the guide on [Updating SPT](/SPT_4x/Updating_SPT) for more details.

## I miss 4.0, can I re-download it?
Yes. Simply select `4.0` in the SPT Installer. See the [Installation Guide](/SPT_4x/Installation_Guide) for instructions.

## When is (insert mod here) going to update to 4.1?
Nobody knows when certain mods are going to update, not even the authors themselves. Do not pester mod authors about updates to their mods.

## Why are `SPT.Launcher` and `SPT.Server` shortcuts?
SPT files were relocated in SPT 4.0 for better modding support. The actual exe files are in your `\SPT_Runtime` folder, and the installer creates shortcuts in your main folder for your convenience.

## Where is my `user` folder?
Also in `\SPT_Runtime`.

## Will a mod marked compatible for `4.1.X` work on future versions of `4.1`?
Mods made for previous hotfix versions should work on the latest version. Those that don't might have received an update to address that.
Mods known to be incompatible with be stated in [Known Mod Issues for 4.1](/SPT_41/Known_Mod_Issues_41).
For an explanation of how SPT versions work and how to update your SPT, read through the [Updating SPT](/SPT_4x/Updating_SPT>) Wiki page.

## How much free space is necessary to install SPT?
This is the current space requirements (compounding) to install SPT:
- Patcher: 8GB (Always `C:\` drive)
- Client: 70GB
- Extract/Copy Patcher: 14GB
- Post-patcher: ~35GB

So while the final install size is ~60GB, the maximum allocated for SPT and associated install files *during the install process* is ~100GB combined.

## Bot spawns
SPT uses the game's PvE bot spawning system. Bots will continuously spawn up to a map-specific limit. When enough are killed, more will spawn to replace them. Bot spawns aren't checked for the distance to you or other bots which can let bots can spawn next to you. 
Use a bot spawning mod like [ABPS](https://sp-mod.com/mod/2097/abps-acids-bot-placement-system) to change this system.

## The 1.0 Update
### Will we have `1.0` soon in SPT?
There is no active development effort targeting the retail game's `1.0` update.
### Is it possible to install SPT with `1.0`?
Yes. You can [install SPT](/SPT_4x/Installation_Guide>) while having `1.0` installed.
### Is it possible to install SPT with the Steam copy of the retail game?
Yes. See the [install guide](/SPT_4x/Installation_Guide).
### Can I update my retail copy or will that break my existing SPT install?
The installer makes a **copy** of your game client files to a **separate** location. Update your retail copy as much as you want.

## Need space on your drive? Don't play live?
After you install SPT, you cannot completely uninstall your retail copy, but you can delete the `_Data` folder from your live game folder if you really need the space.

You **will** have to validate files through the retail game launcher if you need to reinstall SPT again by going into the launcher's `Game Settings` and clicking on `Integrity check`. 
On Steam right click the game and open `Properties...`, and in `Installed Files` press `Verify integrity of game files`.

## Do I need to keep my server running to get my insurance back?
**No.**

SPT uses your system clock for things like insurance, crafts, upgrades, etc. When one of these timers start, a completion timestamp will be generated. 
When you start your server, and load a profile, it will automatically compare your current system clock to the completion timestamp and then update the timer. 
Once your system clock matches or surpasses the timestamp that timer will mark as complete and you will receive the outcome.

*Once insurance is complete, the claim timer will only start on your next login.*

This is so you do not need to keep your `SPT.Server.exe` open while you are not playing.

# Known Issues
- [Known Live Issues for SPT 4.1](/SPT_41/Known_Live_Issues_41)
- [Known SPT Issues for SPT 4.1](/SPT_41/Known_SPT_Issues_41)
- [Known Mod Issues for SPT 4.1](/SPT_41/Known_Mod_Issues_41)




















