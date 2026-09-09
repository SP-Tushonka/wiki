---
title: Bleeding Edge Install Instructions for SPT 5.0
description: SPT Bleeding Edge installation instructions for project testing.
published: true
date: 2026-09-09T16:49:10.794Z
tags: 
editor: markdown
dateCreated: 2026-09-09T13:41:16.788Z
---

> This page applies to `BLEEDING EDGE` SPT versions. 
{.is-warning}

## Testing Only

Bleeding Edge installations are for testing only! If you are attempting to install a Bleeding Edge version to play casually, you are going to have a very bad time. Please do yourself a favour and instead use a [stable released version](/SPT_4x/Installation_Guide).

## No Support

This document is the **only support** that you will find for installing the Bleeding Edge version. If you attempt to contact the SPT support team, staff members, moderators, or the general Discord community about installing the Bleeding Edge version, you may end up blocked from downloading Bleeding Edge versions in the future with no warning. We use this version for fast iteration of core development and we do not have the resources to support users on these versions.

## Prerequisites

- A system above the [minimum system requirements](/SPT_4x/system-requirements). The Live install must remain (80GB) as well as a complete copy (+80GB).
- You must have the latest version of the Live game installed using either the Launcher or Steam.
- You must have started the Live game and loaded the main menu.
- You must be willing to submit bugs to the [GitHub issues board](https://github.com/sp-tushonka/server-csharp/issues) or to the [#BE-Testing](https://discord.com/channels/875684761291599922/980558564693274694) channel on Discord.

## Software Requirements
- [7-Zip](https://www.7-zip.org/)
- `.NET Desktop Runtime` and `ASP.NET Core Runtime` from [here](https://dotnet.microsoft.com/en-us/download/dotnet/10.0).

<div style="margin-top: 20px;"></div>
<img src="/runtimes.png" alt=".NET runtimes" width=400 style="display: block; margin: 0 auto;">


## Installation Instructions for 5.0 BE

> These instructions are specific and tedious. **Do no more or no less than what is written.** If for any reason something doesn't work, delete what you have and start over. *Slower.*
{.is-warning}

SPT 5.0 has no installer and no downgrade patcher. It runs on the current Live client, so the install is a copy of your Live game with the Bleeding Edge archive extracted over it.

1. Create a new empty folder outside of any protected location (E.g.: `C:\Games\SPT-5.0-BE`). Do not use Downloads, Desktop or Program Files.
2. Copy the **entire contents** of your Live folder into that new folder.
	- Copy, do not move. Your Live install stays where it is and stays untouched.
	- The copy must be complete. Wait for it to finish before continuing.
3. Download the Bleeding Edge SPT version from the [`#be-testing`](https://discord.com/channels/875684761291599922/980558564693274694) channel from our [Discord Server](https://discord.sp-tushonka.com/).
	- You can gain access to that channel by getting the `BE Tester Role` in the [`#info-other`](https://discord.com/channels/875684761291599922/875758493351694396) channel.
	- Each Bleeding Edge archive is built for one Live client build. The build it targets is in the post. If your Live game has updated past it, wait for the next archive.
4. Extract the contents of this 7z archive into the root of your `SPT-5.0-BE` directory, replacing files when asked.
5. Run `SPT.Server` from the `SPT_Runtime` folder and wait for the green text that says the server has started.
6. Run `SPT.Launcher` from the same folder, register a profile and click `Start Game`.

At this point, you should have a fully installed Bleeding Edge version of SPT 5.0 installed on your system.

## Common Questions

Remember, this document is your only avenue of support for Bleeding Edge builds.
<details>
<summary>I was playing the game normally, no mods, fresh profile, and I encountered an error</summary>
We are extremely interested in these types of clean issues. Please submit these types of bugs to the <a href="https://github.com/sp-tushonka/server-csharp/issues">GitHub issues board</a> or to the <a href="https://discord.com/channels/875684761291599922/980558564693274694">#be-testing</a> channel on Discord. Thank you for helping us build SPT.
</details>

<details>
<summary>The server doesn't start</summary>
Delete everything and start over. Read slower.
</details>

<details>
<summary>The launcher doesn't start</summary>
Delete everything and start over. Read slower.
</details>

<details>
<summary>The game does not load to the main menu</summary>
Check that your Live game is on the build the archive was made for. If it is, delete everything and start over. Read slower.
</details>

<details>
<summary>My Live game updated and now SPT does not start</summary>
It's not supposed to. Wait for an archive built for the new client, then copy your Live game again and extract that archive over the copy.
</details>

<details>
<summary>My SPT 4.x profile does not work</summary>
It's not supposed to.
</details>

<details>
<summary>I tried to install a mod and it won't work</summary>
It's not supposed to.
</details>

Thank you for your help testing and making SPT better for everyone.
- Developers & Staff
