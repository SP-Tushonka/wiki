---
title: Maunal Installation Instructions for SPT
description: 
published: true
date: 2026-08-25T23:02:44.294Z
tags: 
editor: markdown
dateCreated: 2026-08-08T11:24:29.696Z
---

> This page applies to SPT version `4.1`
{.is-info}

## What you need to do before you manually installing SPT

Verify that your retail game copy works, and that you can load up to at least the main menu or stash.
This is particularly important if you have just installed the game so all necessary files can be generated.

## Manually installing and running SPT

1. Download the patcher from one of the two links in either the `4.1` or `4.0` section [here](https://patcher.sp-tushonka.com/mirrors.json).
	- If your retail game copy is newer than the above downgrade patch, **please wait**, a new downgrade patch will be created eventually.
	- If your retail game copy is older than the above downgrade patch, update your game through the official Launcher or Steam.

<br>
<img src="/matching_patcher.png" alt="matching patcher" width=400 style="display: block; margin: 0 auto;">
<div style='text-align: center;'>
Example of matching game version and patcher.
</div>


2. Create a new folder for SPT. A good location would be `C:\Games\SPT 4.1` or `C:\Games\SPT 4.0`.
3. Copy the contents of your live game folder (For Steam, the files inside the `build` folder) into your `SPT` folder.
	- **DO NOT** delete the original retail game installation to save space, it must remain in the original install location for SPT to function.
4. Extract the patcher you downloaded in step 1 to your `SPT` folder (requires [7zip](https://www.7-zip.org/)).
5. Run the `patcher.exe` and wait for it to finish.
6. Download the SPT release archive:
	- For SPT 4.1: From the Direct Download link on [this](<https://github.com/sp-tushonka/build/releases/latest>) page.
	- For SPT 4.0: From [here](https://github.com/sp-tarkov/build/releases/download/4.0.13/SPT-4.0.13-40087-2891fd4.7z).
7. Extract the contents of the SPT release archive into your `SPT` folder.
8. Open your `\SPT 4.1\SPT_Runtime` or `\SPT 4.0\SPT` folder.
9. Run `SPT.Server`.
 - Wait for the green text that says `Server has started, happy playing`.
10. Run `SPT.Launcher` and follow the onscreen instructions.
 - You can use any username you want. It is recommend that you **do not** use your retail copy account username. Especially if you plan on recording or streaming SPT.
 - Select your desired game version. Each version has a description box summarising what is included. Once you have picked your chosen game version click `Register`. You can pick *any* game version you want from the profile list, you do not need to own the corresponding retail game version. Once chosen, you cannot change the edition a profile is using.
11. To make it easier to launch SPT in the future, you can right click `SPT.Server` and `SPT.Launcher`, select `Send to > Desktop (create shortcut)`.
12. Click `Start Game` and load into the main menu.

Once you have completed the above, you can now play SPT and install mods found on [The Forge](https://sp-mod.com/). You can find a guide on how to correctly install SPT mods on the [Installing Mods](/SPT_4x/Installing_Mods) Wiki page. **Make sure to only install versions of mods made for your installed version of SPT.**



## Common Installation and Start-up Issues
Below you can find some common issues that users encounter when installing or first starting SPT, along with the solution to fixing it. If your issue is not listed then join our [Discord Server](https://discord.sp-tushonka.com/) and ask in the [`#spt-support`](https://discord.com/channels/875684761291599922/1172730102119944222) channel.


<details>
<summary>SPT Server crashing instantly or not opening up at all?</summary>

For SPT 4.0 see [here](/SPT_40/Known_SPT_Issues_40#server-doesnt-launch-or-closes-immediately)  
For SPT 4.1 see [here](/SPT_41/Known_SPT_Issues_41#server-doesnt-launch-or-closes-immediately)

If it tells you that you already have them installed, then use the repair option. Restart your PC after.

<div style="margin-top: 20px;"></div>
<img src="/runtimes.png" alt=".NET runtimes" width=400 style="display: block; margin: 0 auto;">

If that didn't help, verify that your SPT install path doesn't have any special characters (`;,[]{}` etc.).

</details>


<details>
<summary>The application had a critical error and failed to run "Watermark" error.</summary>

<img src="/failedshortcuts.png" style="border: 2px solid grey;" alt="Watermark Error">

This happens because you have moved the `SPT.Server.exe` and/or the `SPT.Launcher.exe`, out of your their folder. 
You will need to move these back into your `\SPT_Runtime` folder for SPT 4.1 or `\SPT` for SPT 4.0 and create desktop shortcuts of these. You can do this by right-clicking the executables and then Send To > Desktop (Shortcut). The shortcuts to the two are made by the installer automatically, which you can find in the root folder of your SPT install.
</details>

## Old mods and profiles
You cannot use any of your old mod files in a newer SPT version. If you want to use the same mods, you need to download updated versions of them once they have been updated to the latest SPT version.

Some old profiles can work. See the [version numbers](/SPT_4x/Updating_SPT#version-numbers) section for more details.

# See also
[How SPT Works](/SPT_4x/How_SPT_Works)
[System Requirements](/SPT_4x/system-requirements)
[Updating SPT](/SPT_4x/Updating_SPT)
[Installing Mods](/SPT_4x/Installing_Mods)