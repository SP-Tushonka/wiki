---
title: Updating SPT
description: Learn how to update your SPT installation.
published: true
date: 2026-08-30T14:33:13.035Z
tags: guide
editor: markdown
dateCreated: 2026-08-08T11:23:51.525Z
---

> This page applies to any SPT version
{.is-info}

> This method can only be used to update to a new patch. An update from ex. `4.0.13 > 4.1.0` requires a new install of SPT.
{.is-warning}


1. Download the appropriate release files:
 - For updating SPT 4.1: From the Direct Download link on [this](https://github.com/sp-tushonka/build/releases/latest) page.
 - For updating SPT 4.0: From [here](https://github.com/sp-tarkov/build/releases/download/4.0.13/SPT-4.0.13-40087-2891fd4.7z).
2. Close your game, launcher, and server.
3. Open the downloaded SPT files using [7zip](https://www.7-zip.org/).
4. Copy contents of the 7z file into your **existing** folder, **overwrite all files**.
5. **Update all of your mods to their latest versions marked compatible with your version of SPT.**
 - Mods made for previous hotfix versions should work on the latest version. Those that don't might have received an update to address that.
> This will only overwrite base SPT files. It will __not__ overwrite or remove your profile(s), mods or mod configs.
{.is-info}

### Replacing files

When you drag and drop a folder into a directory, which has the same named folders/files, it will merge them and overwrite only duplicate files. **It will not delete any non-duplicates.**

&nbsp;
<video width="450" height="297" controls style="display: block; margin: 0 auto;">
	<source src="https://i.imgur.com/Wy5bijG.mp4" type="video/mp4">
</video>

## Version numbers
SPT follows the [Semantic Versioning](https://semver.org/) schema for its version numbers, which works as follows:

`SPT Version X.Y.Z`

`X` = Major update
- A large refactor of SPT or the retail game
- Requires reinstalling SPT anew
- Old mods **won't work**
- Unmodded old profiles *might* work

`Y` = Minor update
- A new version of the retail game is being used
- Requires reinstalling SPT anew
- Old mods **won't work**
- Unmodded old profiles *might* work

`Z` = Patch
- Bug fixes for the previous Minor version
- Generally doesn't require a reinstall
- Generally works with mods made for the previous hotfix version
- Old profiles **will work**
- **Can be used to update your SPT if it's on the same Minor version**


# See also
[New to SPT? Start here!](/Beginners_Guide)
[Installing SPT](/SPT_4x/Installation_Guide)