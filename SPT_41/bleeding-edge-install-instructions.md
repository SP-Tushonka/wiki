---
title: Bleeding Edge Install Instructions for SPT 4.1
description: SPT Bleeding Edge installation instructions for project testing.
published: true
date: 2026-08-16T16:43:07.078Z
tags: 
editor: markdown
dateCreated: 2026-08-08T11:23:55.251Z
---

> This page applies to `BLEEDING EDGE` SPT versions. 
{.is-warning}

## Testing Only

Bleeding Edge installations are for testing only! If you are attempting to install a Bleeding Edge version to play casually, you are going to have a very bad time. Please do yourself a favour and instead use a [stable released version](/SPT_4x/Installation_Guide).

## No Support

This document is the **only support** that you will find for installing the Bleeding Edge version. If you attempt to contact the SPT support team, staff members, moderators, or the general Discord community about installing the Bleeding Edge version, you may end up blocked from downloading Bleeding Edge versions in the future with no warning. We use this version for fast iteration of core development and we do not have the resources to support users on these versions.

## Prerequisites

- A system above the [minimum system requirements](/SPT_4x/system-requirements). The live Escape From Tarkov install must remain (80GB) as well as a complete copy (+80GB).
- You must have the latest version of the Live game installed using either the Launcher or Steam.
- You must have started the Live game and loaded the main menu.
- You must be willing to submit bugs to the [GitHub issues board](https://github.com/sp-tarkov/server-csharp/issues/new/choose) or to the [#BE-Testing](https://discord.com/channels/875684761291599922/980558564693274694) channel on Discord.

## Software Requirements
- [7-Zip](https://www.7-zip.org/)
- `.NET Desktop Runtime` and `ASP.NET Core Runtime` from [here](https://dotnet.microsoft.com/en-us/download/dotnet/10.0).

<div style="margin-top: 20px;"></div>
<img src="/runtimes.png" alt=".NET runtimes" width=400 style="display: block; margin: 0 auto;">


## Installation Instructions for 4.1 BE

> These instructions are specific and tedious. **Do no more or no less than what is written.** If for any reason something doesn't work, delete what you have and start over. *Slower.*
{.is-warning}

1. Install SPT 4.1 per the [Installation Guide](/SPT_4x/Installation_Guide) in a new folder (E.g.: `C:\Games\SPT-4.1-BE`).
2. Download the Bleeding Edge SPT version from the [`#be-testing`](https://discord.com/channels/875684761291599922/980558564693274694) channel from our [Discord Server](https://discord.com/invite/Xn9msqQZan).
	- You can gain access to that channel by getting the `BE Tester Role` in the [`#info-other`](https://discord.com/channels/875684761291599922/875758493351694396) channel.
3. Extract the contents of this 7z archive into the root of your `SPT-4.1-BE` directory.

At this point, you should have a fully installed Bleeding Edge version of SPT 4.1 installed on your system.

## Common Questions

Remember, this document is your only avenue of support for Bleeding Edge builds.
<details>
<summary>I was playing the game normally, no mods, fresh profile, and I encountered an error</summary>
We are extremely interested in these types of clean issues. Please submit these types of bugs to the <a href="https://github.com/sp-tarkov/server-csharp/issues/new/choose">GitHub issues board</a> or to the <a href="https://discord.com/channels/875684761291599922/980558564693274694">#be-testing</a> channel on Discord. Thank you for helping us build SPT.
</details>

<details>
<summary>Why is there a watermark on my screen? Can I get rid of it?</summary>
If I could reach through my monitor and slap you, I would. No, you can't get rid of it. We put it there. We want it there. This build is for testing. Go eat some glue or something.
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
Delete everything and start over. Read slower.
</details>

<details>
<summary>My SPT 4.0 profile does not work</summary>
It's not supposed to.
</details>

<details>
<summary>I tried to install a mod and it won't work</summary>
It's not supposed to.
</details>

Thank you for your help testing and making Single Player Tarkov better for everyone.
&mdash; Developers & Staff