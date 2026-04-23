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

- the actual device-side behavior fix is in [`080f319`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/080f319919312203e866f8923280f0ccad4a1645), where the Aerodactyl tree sets the correct charging node, inverted values, and toggle-only support
- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) only fixes the Health HAL Soong selector types so the charging-control config can build correctly

So if someone is looking for the real charging-limit behavior fix, the important Aerodactyl-side change is `080f319`.

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
| `android_device_nothing_Aerodactyl` | [`f5cb9d3`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/f5cb9d315ad9d1247c73115a68f5d9575671ce6b) | `Required` | Defines the partition filesystem type. | Fixes the missing filesystem-type case that can break product parsing during lunch and dumpvars. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`01fc06b`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/01fc06bcabba5e5156ca50b93235157a43f51662) | `Required` | Fixes product parsing for lunch. | Cleans up product parsing and removes the duplicated virtual A/B block. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`080f319`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/080f319919312203e866f8923280f0ccad4a1645) | `Required` | Fixes charging limit behavior. | Adds the real device-side charging-limit fix for `/proc/charger/usb_charger_en`. | `Maybe` |

## Recommended Same-Device Commits

These are the commits that make the build feel better, cleaner, or more complete on the same device family.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc891accd7d94255ed63cda0d51b332f184e3) | `Recommended` | Improves refresh-rate handling. | Sets saner refresh-rate categories so the device feels smoother. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`a13fc5a`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/a13fc5a687160d238b7eec1a027089ab5a92444f) | `Recommended` | First main optimization batch. | Pulls in the first larger set of performance-focused tweaks. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`122679e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/122679e4db9257f5f13e29327536745e52a24f8c) | `Recommended` | Adds memory and network tuning. | Switches zram to zstd, enables dexpreopt, and turns on TCP Fast Open. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`37ca756`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/37ca75644fe8f51941c8e57d52abfe04fea21849) | `Recommended` | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`397e328`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/397e328bff6673b1301f169e0dc299571e4b6199) | `Recommended` | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| `android_device_nothing_Aerodactyl` | [`cb84824`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cb848246235fd2a232f5298dd9cd5631dd56d7e4) | `Recommended` | Wires ViPER4AndroidFX support. | Inherits the ViPER config and exposes the vendor audio effect hook-up. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`531bd55`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/531bd5587802da9a50fa777d4d937ad0af0c3c4a) | `Recommended` | Pins FaceUnlock to the front camera. | Forces FaceUnlock to use the correct selfie camera ID on this device family. | `Yes, if you ship FaceUnlock` |
| `android_device_nothing_Aerodactyl` | [`5a1a0ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/5a1a0ae7cb39d0ff8e85cbe053afced206654354) | `Recommended` | Rebalances haptics and display transitions. | Tunes the default haptic overlays and enables the higher performance transition path. | `Maybe` |
| `android_device_nothing_Aerodactyl` | [`06e0110`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/06e01101c24c63df3784c9f740d596109b84306c) | `Recommended` | Cleans up old build flags. | Removes product flags that are no longer used and centralizes the maintainer property. | `Yes` |

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
2. `1c6e163` - temporary PacmanPro AVB workaround
3. `ae010f2` - adds Lunaris-specific product setup
4. `4e0bc89` - improves refresh-rate handling
5. `a13fc5a` - brings in the first optimization batch
6. `122679e` - adds memory and network tuning
7. `37ca756` - pushes UI responsiveness further
8. `f5cb9d3` - defines the partition filesystem type
9. `01fc06b` - fixes product parsing for lunch and dumpvars
10. `397e328` - cleans up metadata and duplicate props
11. `cb84824` - wires ViPER4AndroidFX support
12. `531bd55` - pins FaceUnlock to the front camera
13. `080f319` - fixes charging limit behavior
14. `5a1a0ae` - rebalances haptics and display transitions
15. `06e0110` - cleans up old build flags

## Cherry-Pick Commands

These commands assume a clean and compatible Lunaris `23.2` tree. If your tree already differs, you may need to resolve cherry-pick conflicts manually.

```bash
git -C hardware/lineage/interfaces cherry-pick 8ea0fab29d6adba69a5692aa929b19a81b9a15fc

git cherry-pick 1c6e163 ae010f2 4e0bc89 a13fc5a 122679e
git cherry-pick 37ca756 f5cb9d3 01fc06b 397e328 cb84824
# includes the actual device-side charging-limit fix
git cherry-pick 531bd55 080f319 5a1a0ae 06e0110
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
- [`122679e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/122679e4db9257f5f13e29327536745e52a24f8c): adds memory and network tuning
  warning: tune this against your own RAM size and network stack
- [`37ca756`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/37ca75644fe8f51941c8e57d52abfe04fea21849): improves UI responsiveness
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
