---
title: Known SPT 4.0 Issues
description: Known SPT issues and possible fixes for SPT 4.0.
published: true
date: 2026-08-10T16:41:41.237Z
tags: 
editor: markdown
dateCreated: 2026-08-08T11:23:14.018Z
---

> This page applies to SPT version `4.0`
{.is-info}

## [Github tracked issues](<https://github.com/sp-tarkov/build/wiki/Known-SPT-issues>)

## The server has unexpectedly stopped... : Decoded string is not a valid IDN name.
Remove any trailing symbols from your PC's name (e.g.: `My-PC-` > `My-PC`).
The 15th character of your PC name can't be a symbol either. 
Your PC name should also not use any special characters. Only `a-z`, `A-Z`, `0-9` and `-` are valid (e.g.: `My-PÇ` > `My-PC`). 
You can rename your PC by searching for `View your PC name` in the Start menu, and clicking on `Rename this PC`.

## Server mods don't appear in the SPT Launcher
[Update your SPT.](/SPT_4x/Updating_SPT)
Note that [Client mods](/SPT_4x/Mod_Types) won't show up in the SPT Server nor Launcher.

## There are little to no PMCs in your Scav runs
[Update your SPT](/SPT_4x/Updating_SPT), and make sure you don't have an extended raid timer, as the game's spawning system tends to break with them.

## Empty flea with `404 not found` errors
[Update your SPT](/SPT_4x/Updating_SPT).

## Server doesn't launch or closes immediately

From [here](https://dotnet.microsoft.com/en-us/download/dotnet/9.0) download the latest version of **both**:
- `ASP.NET Core Runtime`
- `.NET Desktop Runtime`

If it tells you that you already have them installed, then use the repair option. Restart your PC after.

<div style="margin-top: 20px;"></div>
<img src="/runtimes.png" alt=".NET runtimes" width=400 style="display: block; margin: 0 auto;">

If that didn't help, verify that your SPT install path doesn't have any special characters (`;,[]{}` etc.).

## Kollontay still spawns on high level Ground Zero
[Update your SPT.](/SPT_4x/Updating_SPT)

## Crisis does not unlock new crafts
[Update your SPT.](/SPT_4x/Updating_SPT)

## SPT Launcher doesn't do anything when you click Play
[Update your SPT.](/SPT_4x/Updating_SPT)

## `Not a valid Win32 FileTime` when using the Hijri calendar
[Update your SPT.](/SPT_4x/Updating_SPT)

## Festive Airdrops have no loot
No known fix.

## `Enable Bosses` being disabled stops spawning PMC bots
[Update your SPT.](/SPT_4x/Updating_SPT)

## Loading in as a PMC when you selected scav
[Update your SPT.](/SPT_4x/Updating_SPT)

## `Access to the path '\\?\C:\Users\[username]\OneDrive\Desktop\SPT\SPT\user\profiles\backups\[date] is denied.`
You have moved SPT onto your OneDrive enabled desktop. Move it to a folder like `C:\Games\SPT 4.0`, and delete the profile backup mentioned in the error message.


# See also
[Frequently Asked Questions for SPT 4.0](/SPT_40/FAQs_40)