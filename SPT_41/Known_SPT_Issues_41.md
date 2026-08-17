---
title: Known SPT 4.1 Issues
description: Known SPT issues and possible fixes for SPT 4.1.
published: true
date: 2026-08-17T18:41:29.118Z
tags: 
editor: markdown
dateCreated: 2026-08-08T15:19:39.611Z
---

> This page applies to SPT version `4.1`
{.is-info}

## [Github tracked issues](<https://github.com/sp-tarkov/build/wiki/Known-SPT-issues>)
<br>

## After moving your SPT 4.1.x install, you get `Game check failed: Unknown error occured, please report to SPT`
[Update your SPT](/SPT_4x/Updating_SPT).

## Server doesn't launch or closes immediately
From [here](https://dotnet.microsoft.com/en-us/download/dotnet/10.0) download the latest version of **both**:
- `ASP.NET Core Runtime`
- `.NET Desktop Runtime`

If it tells you that you already have them installed, then use the repair option. Restart your PC after.

<div style="margin-top: 20px;"></div>
<img src="/runtimes.png" alt=".NET runtimes" width=400 style="display: block; margin: 0 auto;">

If that didn't help, verify that your SPT install path doesn't have any special characters (`;,[]{}` etc.).

## The game closes instantly when pressing Start Game

If you have BitDefender installed add SPT to the exceptions list in both the "Antivirus" as well as "Advanced Threat Defense".
Reportedly Malwarebytes also has this issue. 


## SPT Launcher doesn't start, `Exception Info: System.Text.Json.JsonException: 'X' is an invalid start of a value.` Error in Event Viewer
Delete your `SPT_Runtime\user\launcher\launchersettings.json`.