# Aerodactyl Reference Stack

This page is the main part of the guide.

Its job is simple: show the public `TwistedVision518` commits that matter most when building Lunaris for the Nothing Phone 2a / 2a Plus family, while also pointing out a few related commits in other Lunaris repos.

## Last Verified

- branch: `lunaris/23.2`
- date: `2026-04-26`

## What This Page Assumes

- you are building Lunaris `23.2`
- you already have a usable Aerodactyl tree
- you want the public commit order, not a full bring-up tutorial
- you only want `TwistedVision518` commits here, plus the one extra health fix needed for charging control

## Charging Limit Note

The charging-limit fix is split across two places:

- the actual device-side behavior fix is in [`4b66e80`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4b66e804fdd7eb32e774b3720016a14e64f27d3f), where the Aerodactyl tree sets the correct charging node, inverted values, and toggle-only support
- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) only fixes the Health HAL Soong selector types so the charging-control config can build correctly

So if someone is looking for the real charging-limit behavior fix, the important Aerodactyl-side change is `4b66e80`.

## How To Read This

- `Required` means the commit is part of the core stack for this guide
- `Recommended` means the commit is useful, but not absolutely essential
- `Optional` means the commit is more preference-based or feature-based
- `Can help other ROMs` marks commits that may be useful outside Lunaris too

## Required For Lunaris Bring-Up

These are the commits that form the core same-device stack.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_hardware_lineage_interfaces` | [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) | `Required if missing` | Fixes Health HAL Soong selector types. | Lets charging-control config build correctly when toggle support is enabled. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`c83307f`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c83307fdf23876468a43d65f38a898624eb0730f) | `Required` | Clean Lunaris bring-up base. | Combines the early AVB workaround, Lunaris-specific setup, refresh-rate categories, and build-flag cleanup into one cleaner bring-up commit. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`f5cb9d3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/f5cb9d315ad9d1247c73115a68f5d9575671ce6b) | `Required` | Defines the partition filesystem type. | Fixes the missing filesystem-type case that can break product parsing during lunch and dumpvars. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`01fc06b`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/01fc06bcabba5e5156ca50b93235157a43f51662) | `Required` | Fixes product parsing for lunch. | Cleans up product parsing and removes the duplicated virtual A/B block. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`4b66e80`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4b66e804fdd7eb32e774b3720016a14e64f27d3f) | `Required` | Fixes charging limit behavior. | Adds the real device-side charging-limit fix for `/proc/charger/usb_charger_en`. | `Maybe` |

## Recommended Same-Device Commits

These are the commits that make the build feel better, cleaner, or more complete on the same device family.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`91aa60a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/91aa60af0d8702472bb2ddb916a2d0b406f67f58) | `Recommended` | First main optimization batch. | Pulls in the first larger set of performance-focused tweaks. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`a130fc3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/a130fc3bc5e87c70cf3114a6708a29c4b15c065d) | `Recommended` | Adds memory and network tuning. | Switches zram to zstd, enables dexpreopt, and turns on TCP Fast Open. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`aa8ce1a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/aa8ce1a37bd3d6d939e7df30a60a001e2e8502c4) | `Recommended` | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`6eec657`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/6eec6577e777cf7e724a61f6138e2a62c82ea20d) | `Recommended` | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| `android_device_nothing_Aerodactyl` | [`9d219df`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9d219df8d695cb6079e04595e0d85ea1c2930d8a) | `Recommended` | Wires ViPER4AndroidFX support. | Inherits the ViPER config and exposes the vendor audio effect hook-up. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`816900c`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/816900c70778d56db2f159f8ed03ab57ec8a350c) | `Recommended` | Pins FaceUnlock to the front camera. | Forces FaceUnlock to use the correct selfie camera ID on this device family. | `Yes, if you ship FaceUnlock` |
| `android_device_nothing_Aerodactyl` | [`94a60d1`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/94a60d171c282085c8c76811bd6a717d29db0b17) | `Recommended` | Rebalances haptics and display transitions. | Tunes the default haptic overlays and enables the higher performance transition path. | `Maybe` |

## Optional Device Tuning

These are more preference-based or taste-based commits.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`3e88490`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/3e884903ab9e7b91aa5c9e9f2b94bbd8f46d5f21) | `Optional` | Cleans up haptic mapping. | Makes vibration effects feel more consistent. | `Maybe` |
| `android_device_nothing_Aerodactyl` | [`7cc8d55`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/7cc8d55ca906a78035da7e74b55ba6be9e9ed435) | `Optional` | Fixes DOUBLE_CLICK completion timing. | Waits for the second pulse to finish before reporting the haptic callback as complete. | `Yes` |

## Related Lunaris-Side Commits In Other Repos

These are not part of the Aerodactyl bring-up order itself, but they are still public `TwistedVision518` commits that same-device Lunaris builders may care about.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_packages_apps_FaceUnlock` | [`7308500`](https://github.com/LunarisPacman/android_packages_apps_FaceUnlock/commit/730850086a74419465d34ef6ec8bcf8ae900654f) | `Recommended if used` | Improves FaceUnlock reliability. | Makes FaceUnlock authentication behave more reliably. | `Yes, if you ship this app` |
| `packages_apps_Launcher3` | [`988373b`](https://github.com/LunarisPacman/packages_apps_Launcher3/commit/988373bab5e969b3967c9fee3af78322f7e865fc) | `Optional` | Polishes close-to-home animations. | Makes the home return animation feel tighter and more stable. | `Yes` |

## DynamicBar Commits That Can Help Other ROMs

These are not part of the Aerodactyl `23.2` bring-up order. They live on `frameworks_base` feature branches, but they are still useful to look at if your ROM already ships DynamicBar.

| Repo | Branch | Commit | Short note | What it does |
| --- | --- | --- | --- | --- |
| `frameworks_base` | `lockscreen-media-dynamic-bar` | [`3c905da`](https://github.com/LunarisPacman/frameworks_base/commit/3c905da8f397c33345cbe342f3e0d911e55c99eb) | Refines keyguard media layout. | Tightens the lockscreen DynamicBar media panel. |
| `frameworks_base` | `dynamicbar-refresh` | [`81661ad`](https://github.com/LunarisPacman/frameworks_base/commit/81661ad0ee970b0a5d319dd8056a08ac4dcecf3e) | Refines status bar surfaces. | Cleans up the DynamicBar status bar surfaces and structure. |
| `frameworks_base` | `dynamicbar-refresh` | [`8a747c8`](https://github.com/LunarisPacman/frameworks_base/commit/8a747c844ebf92f2fd3975557f68724f252b099d) | Polishes the compact pill. | Makes the smaller keyguard DynamicBar pill feel cleaner. |
| `frameworks_base` | `dynamicbar-refresh` | [`1128a3e`](https://github.com/LunarisPacman/frameworks_base/commit/1128a3ed03c6b2533c5ccdc2179a6ed1ada87bc2) | Refines expanded media. | Polishes the expanded keyguard DynamicBar media view. |

## Cherry-Pick Order

If you want the safest order for the Aerodactyl stack, use this:

1. `8ea0fab` in `android_hardware_lineage_interfaces` - fixes Health HAL Soong selector types
2. `c83307f` - adds the clean Lunaris bring-up base
3. `91aa60a` - brings in the first optimization batch
4. `a130fc3` - adds memory and network tuning
5. `aa8ce1a` - pushes UI responsiveness further
6. `f5cb9d3` - defines the partition filesystem type
7. `01fc06b` - fixes product parsing for lunch and dumpvars
8. `6eec657` - cleans up metadata and duplicate props
9. `9d219df` - wires ViPER4AndroidFX support
10. `816900c` - pins FaceUnlock to the front camera
11. `4b66e80` - fixes charging limit behavior
12. `94a60d1` - rebalances haptics and display transitions

## Cherry-Pick Commands

These commands assume a clean and compatible Lunaris `23.2` tree. If your tree already differs, you may need to resolve cherry-pick conflicts manually.

```bash
git -C hardware/lineage/interfaces cherry-pick 8ea0fab29d6adba69a5692aa929b19a81b9a15fc

git cherry-pick c83307f 91aa60a a130fc3 aa8ce1a f5cb9d3
git cherry-pick 01fc06b 6eec657 9d219df 816900c
# includes the actual device-side charging-limit fix
git cherry-pick 4b66e80 94a60d1
```

If you also want the related Lunaris-side app work:

```bash
git -C packages/apps/FaceUnlock cherry-pick 730850086a74419465d34ef6ec8bcf8ae900654f
git -C packages/apps/Launcher3 cherry-pick 988373bab5e969b3967c9fee3af78322f7e865fc
```

## Commits That Can Also Help Other ROMs

These are the commits from this guide that are more likely to be useful outside Lunaris too:

- [`91aa60a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/91aa60af0d8702472bb2ddb916a2d0b406f67f58): brings in a larger optimization-focused base
  warning: read it line by line before reusing it
- [`a130fc3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/a130fc3bc5e87c70cf3114a6708a29c4b15c065d): adds memory and network tuning
  warning: tune this against your own RAM size and network stack
- [`aa8ce1a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/aa8ce1a37bd3d6d939e7df30a60a001e2e8502c4): improves UI responsiveness
  warning: scheduler and GPU tuning do not transfer equally well to every device
- [`f5cb9d3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/f5cb9d315ad9d1247c73115a68f5d9575671ce6b): makes build config more explicit
  warning: only useful if your product setup has the same ambiguity
- [`7308500`](https://github.com/LunarisPacman/android_packages_apps_FaceUnlock/commit/730850086a74419465d34ef6ec8bcf8ae900654f): improves FaceUnlock reliability
  warning: only useful if your ROM actually ships the same FaceUnlock app
- [`988373b`](https://github.com/LunarisPacman/packages_apps_Launcher3/commit/988373bab5e969b3967c9fee3af78322f7e865fc): polishes close-to-home animations
  warning: check your Launcher3 base before picking it directly
- DynamicBar commits in `frameworks_base`: useful if your ROM already ships DynamicBar
  warning: these live on feature branches, not the Aerodactyl bring-up stack

## Do Not Pick These Blindly

- older broken experiments are not part of this guide
- the public `23.2` branch also has later haptics tuning from another author, but this page intentionally tracks `TwistedVision518` commits only
- if a commit is not listed here, do not assume it belongs in the stack
- start with the `Required` section first, then move to `Recommended`, then `Optional`

## Closing Note

This is the public Lunaris commit stack I would point same-device builders to first, plus the related app and DynamicBar commits that are worth checking when they fit the feature set you are shipping.
