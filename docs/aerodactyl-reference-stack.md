# Aerodactyl Reference Stack

This page is the main part of the guide.

Its job is simple: show the public `TwistedVision518` commits that matter most when building Lunaris for the Nothing Phone 2a / 2a Plus family, while also pointing out a few related commits in other Lunaris repos.

## Last Verified

- branch: `lunaris/23.2`
- date: `2026-04-23`

## What This Page Assumes

- you are building Lunaris `23.2`
- you already have a usable Aerodactyl tree
- you want the public commit order, not a full bring-up tutorial
- you only want `TwistedVision518` commits here, plus the one extra health fix needed for charging control

## Charging Limit Note

The charging-limit fix is split across two places:

- the actual device-side behavior fix is in [`86bf9e7`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/86bf9e7ed5de183d178f2f9afabca9f2f2a14028), where the Aerodactyl tree sets the correct charging node, inverted values, and toggle-only support
- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) only fixes the Health HAL Soong selector types so the charging-control config can build correctly

So if someone is looking for the real charging-limit behavior fix, the important Aerodactyl-side change is `86bf9e7`.

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
| `android_device_nothing_Aerodactyl` | [`1c6e163`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/1c6e16343b89432d0da7edea22d941e5b3e66d0c) | `Required` | Temporary fix for PacmanPro AVB. | Keeps the Plus variant moving while AVB setup is still being sorted out. | `No` |
| `android_device_nothing_Aerodactyl` | [`ae010f2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ae010f2a3113a0b957e47430cc33d2aa536456f5) | `Required` | Adds Lunaris-specific setup. | Brings in the product-side setup for Lunaris on this device family. | `No` |
| `android_device_nothing_Aerodactyl` | [`b510af3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b510af3b72c644fc2a14ead5388609800fcfd3d2) | `Required` | Defines the partition filesystem type. | Fixes the missing filesystem-type case that can break product parsing during lunch and dumpvars. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`f93e2c4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/f93e2c4b63332f8c6b1a129415da3b937a5a0c19) | `Required` | Fixes parsing and haptics timing. | Cleans up product parsing, keeps the haptics callback timing sane, and rolls back the earlier thermal bump. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`86bf9e7`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/86bf9e7ed5de183d178f2f9afabca9f2f2a14028) | `Required` | Fixes charging limit behavior. | Adds the real device-side charging-limit fix and also rebalances haptics and display transitions. | `Maybe` |

## Recommended Same-Device Commits

These are the commits that make the build feel better, cleaner, or more complete on the same device family.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc891accd7d94255ed63cda0d51b332f184e3) | `Recommended` | Improves refresh-rate handling. | Sets saner refresh-rate categories so the device feels smoother. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`a13fc5a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/a13fc5a687160d238b7eec1a027089ab5a92444f) | `Recommended` | First main optimization batch. | Pulls in the first larger set of performance-focused tweaks. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`16a963a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/16a963ae65f68b366768d48f15c60017af185c1c) | `Recommended` | Adds memory and network tuning. | Improves the stack further with ZRAM, DEX preopt, and TCP tuning. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`61a518c`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/61a518c53adb9f724142591b739e0316d7664d43) | `Recommended` | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`bffc8e2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/bffc8e2b9e531d05421ecd027a498d6c394265b7) | `Recommended` | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| `android_device_nothing_Aerodactyl` | [`ef219d3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ef219d3dd57f6a79c8d961f7c10e99157c0c463f) | `Recommended` | Adds ViPER and FaceUnlock plumbing. | Wires ViPER4AndroidFX and FaceUnlock support. The emoji part of this commit is not important for this guide and can be ignored. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`b566cb0`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b566cb0d6d5d55ccd77e073333226176ab80040c) | `Recommended` | Cleans up old build flags. | Removes product flags that are no longer used and centralizes the maintainer property. | `Yes` |

## Optional Device Tuning

These are more preference-based or taste-based commits.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`e91aac4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/e91aac4e0d41f176eac55e68221ad39cbcb10fec) | `Optional` | Relaxes thermal limits a bit. | Lets the device hold performance longer before throttling. | `Maybe` |
| `android_device_nothing_Aerodactyl` | [`178453b`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/178453bbac7081c6856ee4b908f3ef32a5192d45) | `Optional` | Cleans up haptic mapping. | Makes vibration effects feel more consistent. | `Maybe` |

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
2. `1c6e163` - temporary PacmanPro AVB workaround
3. `ae010f2` - adds Lunaris-specific product setup
4. `4e0bc89` - improves refresh-rate handling
5. `a13fc5a` - brings in the first optimization batch
6. `16a963a` - adds memory and network tuning
7. `61a518c` - pushes UI responsiveness further
8. `b510af3` - defines the partition filesystem type
9. `f93e2c4` - fixes parsing and haptics timing
10. `bffc8e2` - cleans up metadata and duplicate props
11. `ef219d3` - adds ViPER and FaceUnlock plumbing
12. `86bf9e7` - fixes charging limit behavior and rebalances haptics
13. `b566cb0` - cleans up old build flags

## Cherry-Pick Commands

These commands assume a clean and compatible Lunaris `23.2` tree. If your tree already differs, you may need to resolve cherry-pick conflicts manually.

```bash
git -C hardware/lineage/interfaces cherry-pick 8ea0fab29d6adba69a5692aa929b19a81b9a15fc

git cherry-pick 1c6e163 ae010f2 4e0bc89 a13fc5a 16a963a
git cherry-pick 61a518c b510af3 f93e2c4 bffc8e2 ef219d3
# includes the actual device-side charging-limit fix
git cherry-pick 86bf9e7 b566cb0
```

If you also want the related Lunaris-side app work:

```bash
git -C packages/apps/FaceUnlock cherry-pick 730850086a74419465d34ef6ec8bcf8ae900654f
git -C packages/apps/Launcher3 cherry-pick 988373bab5e969b3967c9fee3af78322f7e865fc
```

## Commits That Can Also Help Other ROMs

These are the commits from this guide that are more likely to be useful outside Lunaris too:

- [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc891accd7d94255ed63cda0d51b332f184e3): improves refresh-rate behavior
  warning: check whether your display stack uses the same refresh-rate logic
- [`a13fc5a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/a13fc5a687160d238b7eec1a027089ab5a92444f): brings in a larger optimization-focused base
  warning: read it line by line before reusing it
- [`16a963a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/16a963ae65f68b366768d48f15c60017af185c1c): adds memory and network tuning
  warning: tune this against your own RAM size and network stack
- [`61a518c`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/61a518c53adb9f724142591b739e0316d7664d43): improves UI responsiveness
  warning: scheduler and GPU tuning do not transfer equally well to every device
- [`b510af3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b510af3b72c644fc2a14ead5388609800fcfd3d2): makes build config more explicit
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
