---
title: OptiScaler and DLSS 5
description: Install OptiScaler on SPT and optionally enable DLSS 5 neural rendering.
published: true
date: 2026-08-30T12:00:00.000Z
tags: guide, graphics, dlss
editor: markdown
dateCreated: 2026-08-30T12:00:00.000Z
---

> This page applies to SPT version `4.1`
{.is-info}

> **SPT only.** Do not install any of this into live Escape from Tarkov. BattlEye will treat injectors as a ToS issue.
{.is-warning}

> This is an unofficial community setup. It is **not** an SPT, Forge, NVIDIA, OptiScaler, ReShade, or RenoDX project. The SPT team does not support it.
{.is-warning}

This page documents a working graphics stack for SPT:

1. **[OptiScaler](https://github.com/optiscaler/OptiScaler)** as `dxgi.dll` so the game's DLSS actually initialises.
2. **[ReShade](https://reshade.me)** with add-on support as `ReShade64.dll`, loaded *by* OptiScaler.
3. **[dlss5-dx11-bridge](https://github.com/NIGos/dlss5-dx11-bridge)** plus RenoDX DLSS 5, so neural rendering can run on Tarkov's DirectX 11 client.

An installer that downloads the official packages (and never overwrites `winhttp.dll`) is here: [spt-dlss5-setup](https://github.com/KaRRyerETPA/spt-dlss5-setup).

## Why ReShade as `dxgi.dll` fails

Tarkov is DirectX 11. Unity's `DLSSImporter.dll` calls `InitDLSS`. With ReShade wrapping `dxgi.dll`, that init loads `nvngx_dlss.dll` and **unloads it in about 150ms**. You then get:

- `CreateFeature calls: 0`
- RenoDX overlay: `HOOKS ARMED - NO DLSS CREATE SEEN`

The [dx11 bridge](https://github.com/NIGos/dlss5-dx11-bridge) only forwards DLSS **after** the game (or a mod) has already created a feature. No init, no neural rendering.

Tarkov also **does not load Streamline**. Dropping `sl.interposer.dll` or listing Streamline DLLs under ReShade `[ADDON]` does nothing, and `sl.interposer.dll` fights OptiScaler for `dxgi.dll`.

OptiScaler as `dxgi.dll` is what makes DLSS evaluate (for example `1706x960 -> 2560x1440` at Quality). ReShade must load as a plugin after that.

## Requirements

- A working SPT 4.1 install (Doorstop `winhttp.dll` present).
- An NVIDIA RTX GPU. Neural rendering is native on 50-series. 40-series needs the Ada `nvngx_dlssnr.dll` from the RenoDX Discord.
- [7-Zip](https://www.7-zip.org/).
- From RenoDX Discord `#dlss5` (not redistributed here):
  - `renodx-dlss5.addon64`
  - `nvngx_dlssnr.dll` version `310.8.0.0`

**Never overwrite** `[game folder]\winhttp.dll`. That file is BepInEx Doorstop. Replacing it breaks SPT.

The ReShade setup tool **blocks** `EscapeFromTarkov.exe` on purpose. Install ReShade by extracting `ReShade64.dll` from the add-on setup exe with 7-Zip, or use the installer linked above.

## Easy install

1. Download the [spt-dlss5-setup](https://github.com/KaRRyerETPA/spt-dlss5-setup) source zip.
2. Put `renodx-dlss5.addon64` and `nvngx_dlssnr.dll` into its `extras` folder.
3. Run `install.bat` (or `.\install.ps1 -SptPath "[game folder]"`).
4. Launch SPT. In **Settings / Graphics**, set `NVIDIA DLSS` to `Quality`.
5. Start a raid.
6. Press <kbd>Insert</kbd> for OptiScaler. You want `D3D11 | DLSS | Input: DLSS`.
7. Press <kbd>Home</kbd> for ReShade. Under **Add-ons**, enable `DLSS 5 DX11 Bridge` and `DLSS 5 Neural Rendering`.
8. Enable neural rendering in the RenoDX panel.

If the game does not boot, rename `[game folder]\dxgi.dll` to `winmm.dll`. Both names are documented for SPT on the [OptiScaler wiki](https://github.com/optiscaler/OptiScaler/wiki/Escape-from-Tarkov-(SPT)).

Uninstall with `uninstall.bat` in that same repo. It never deletes `winhttp.dll`.

## Manual install

Place files **next to** `EscapeFromTarkov.exe`:

| File | Role |
| - | - |
| `dxgi.dll` | OptiScaler 0.9.4 (rename from `OptiScaler.dll`) |
| `nvngx_dlss.dll` | DLSS 310.8 next to the exe |
| `OptiScaler.ini` | See values below |
| `ReShade64.dll` | ReShade 6.8+ **with add-on support** |
| `renodx-dlss5.addon64` | RenoDX neural rendering |
| `nvngx_dlssnr.dll` | Neural model 310.8 |
| `dlss5-dx11-bridge.addon64` | [NIGos releases](https://github.com/NIGos/dlss5-dx11-bridge/releases) |
| `winhttp.dll` | Leave the existing Doorstop file alone |

In `OptiScaler.ini`:

```
Dx11Upscaler=dlss
LoadReshade=true
```

In `ReShade.ini`:

```
[ADDON]
DisabledAddons=
LoadFromDllMain=renodx-dlss5.addon64,dlss5-dx11-bridge.addon64
```

Do not set `AddonPath` to `EscapeFromTarkov_Data\Plugins\x86_64`. That folder is Unity native plugins, not ReShade add-ons.

Do not install ReShade as `dxgi.dll` while using this stack.

## In-raid checks

OptiScaler is working when <kbd>Insert</kbd> shows something like:

- `D3D11 | DLSS 310.8.0 | Input: DLSS | Spoof: Off`
- Internal resolution scaling to your display (Quality is typically 1.5x)

If the overlay says `Presets are overridden externally`, set NVIDIA App DLSS override to `Use the 3D application setting`, and in-game `DLSS Preset` to `Default` or `Latest`. Then OptiScaler's preset dropdown can apply.

DLSS 5 is working when RenoDX shows `creates` and `evaluations` increasing, and `Successful NR frames` is above 0. `[game folder]\dlss5-dx11-bridge.log` must show `CreateFeature calls` above 0. If `nvngx_dlss.dll` still unloads in ~150ms, ReShade is owning DXGI or DLSS never inited.

## Risks

Neural rendering is expensive. Expect a large FPS drop versus OptiScaler DLSS alone.

The bridge author has seen **GPU device-removed** on Tarkov. If the world freezes or the driver resets, delete `ReShade64.dll`, `renodx-dlss5.addon64`, `nvngx_dlssnr.dll`, and `dlss5-dx11-bridge.addon64`. OptiScaler DLSS can stay.

## What does not work

| Approach | Result |
| - | - |
| ReShade as `dxgi.dll` + bridge + RenoDX | `InitDLSS` fails, 0 creates |
| ReShade as `d3d11.dll` instead | Same unload |
| Streamline `sl.*.dll` in the game folder | Tarkov never loads them |
| Listing Streamline files in `[ADDON] OverlayCollapsed` | Overlay only |
| Editing `dlss5-dx11-bridge.cfg` before CreateFeature exists | Those keys run only after DLSS inits |

The bridge cfg defaults (`stage=3`, `flags=-1`) are fine. Do not set `flags=107` (that was Baldur's Gate 3).

# See also

[Performance Tuning](/SPT_4x/Performance_Tuning)
<br>
[OptiScaler SPT wiki entry](https://github.com/optiscaler/OptiScaler/wiki/Escape-from-Tarkov-(SPT))
<br>
[spt-dlss5-setup installer](https://github.com/KaRRyerETPA/spt-dlss5-setup)
