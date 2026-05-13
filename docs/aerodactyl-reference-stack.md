# Aerodactyl Reference Stack

This page is the main part of the guide.

Its job is simple: show the public `TwistedVision518` commits that matter most when building Lunaris for the Nothing Phone 2a / 2a Plus family, while also pointing out a few related commits in other Lunaris repos.

## Last Verified

- branch: `lunaris/23.2`
- date: `2026-05-13`

## What This Page Assumes

- you are building Lunaris `23.2`
- you already have a usable Aerodactyl tree
- you want the public commit order, not a full bring-up tutorial
- you only want `TwistedVision518` commits here, plus the one extra health fix needed for charging control

## Charging Limit Note

The charging-limit fix is split across two places:

- the actual device-side behavior fix is in [`7ce0d7c`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/7ce0d7c68d33ad27df216c98705f857f78c268c4), where the Aerodactyl tree sets the correct charging node, inverted values, and toggle-only support
- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) only fixes the Health HAL Soong selector types so the charging-control config can build correctly

So if someone is looking for the real charging-limit behavior fix, the important Aerodactyl-side change is `7ce0d7c`.

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
| `android_device_nothing_Aerodactyl` | [`9f0537e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9f0537e8398ae822ba2ef6ad85f5879bd0448bcb) | `Required` | Clean Lunaris bring-up base. | Combines the early AVB workaround, Lunaris-specific setup, refresh-rate categories, and build-flag cleanup into one cleaner bring-up commit. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`ee4944e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ee4944e06e6ec2016d78d9dd3cd8e83fbc10ba56) | `Required` | Defines the partition filesystem type. | Fixes the missing filesystem-type case that can break product parsing during lunch and dumpvars. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`dfa4c8e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/dfa4c8e1478ae707a8763aaf54a50b55a47fbcc2) | `Required` | Fixes product parsing for lunch. | Cleans up product parsing and removes the duplicated virtual A/B block. | `Yes` |
| `android_device_nothing_Aerodactyl` | [`7ce0d7c`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/7ce0d7c68d33ad27df216c98705f857f78c268c4) | `Required` | Fixes charging limit behavior. | Adds the real device-side charging-limit fix for `/proc/charger/usb_charger_en`. | `Maybe` |

## Recommended Same-Device Commits

These are the commits that make the build feel better, cleaner, or more complete on the same device family.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`8944529`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/89445290853279b09b8e19982f3e983f91a45bfb) | `Recommended` | First main optimization batch. | Pulls in the first larger set of performance-focused tweaks. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`d5d80ac`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d5d80ac2b26802a5e226443db64477261aeb3d92) | `Recommended` | Adds memory and network tuning. | Switches zram to zstd, enables dexpreopt, and turns on TCP Fast Open. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`cdcce68`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cdcce68e42ac202620773b688b72c087e2e6c025) | `Recommended` | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |
| `android_device_nothing_Aerodactyl` | [`6e84748`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/6e8474872911e89ee3bc3c43791cd0a3599bf546) | `Recommended` | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| `android_device_nothing_Aerodactyl` | [`2ff4860`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/2ff4860c228dc48367c77d8016e125e1b338edb3) | `Recommended` | Wires ViPER4AndroidFX support. | Inherits the ViPER config and exposes the vendor audio effect hook-up. | `Partly` |
| `android_device_nothing_Aerodactyl` | [`54db2cf`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/54db2cf497fdf12d7704c1d9676a6208f3cda09c) | `Recommended` | Rebalances haptics and display transitions. | Tunes the default haptic overlays and enables the higher performance transition path. | `Maybe` |

## Optional Device Tuning

These are more preference-based or taste-based commits.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `android_device_nothing_Aerodactyl` | [`b5e3672`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b5e36727aca990aa38bc11567d2e9ced56aad09e) | `Optional` | Cleans up haptic mapping. | Makes vibration effects feel more consistent. | `Maybe` |
| `android_device_nothing_Aerodactyl` | [`aa87659`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/aa8765948d270517b63e2ee90281e1fcf73ee28e) | `Optional` | Fixes DOUBLE_CLICK completion timing. | Waits for the second pulse to finish before reporting the haptic callback as complete. | `Yes` |

## Related Lunaris-Side Commits In Other Repos

These are not part of the Aerodactyl bring-up order itself, but they are still public `TwistedVision518` commits that same-device Lunaris builders may care about.

| Repo | Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- | --- |
| `packages_apps_Launcher3` | [`988373b`](https://github.com/LunarisPacman/packages_apps_Launcher3/commit/988373bab5e969b3967c9fee3af78322f7e865fc) | `Optional` | Polishes close-to-home animations. | Makes the home return animation feel tighter and more stable. | `Yes` |

## Cherry-Pick Order

If you want the safest order for the Aerodactyl stack, use this:

1. `8ea0fab` in `android_hardware_lineage_interfaces` - fixes Health HAL Soong selector types
2. `9f0537e` - adds the clean Lunaris bring-up base
3. `8944529` - brings in the first optimization batch
4. `d5d80ac` - adds memory and network tuning
5. `cdcce68` - pushes UI responsiveness further
6. `ee4944e` - defines the partition filesystem type
7. `dfa4c8e` - fixes product parsing for lunch and dumpvars
8. `6e84748` - cleans up metadata and duplicate props
9. `2ff4860` - wires ViPER4AndroidFX support
10. `7ce0d7c` - fixes charging limit behavior
11. `54db2cf` - rebalances haptics and display transitions

## Cherry-Pick Commands

These commands assume a clean and compatible Lunaris `23.2` tree. If your tree already differs, you may need to resolve cherry-pick conflicts manually.

```bash
git -C hardware/lineage/interfaces cherry-pick 8ea0fab29d6adba69a5692aa929b19a81b9a15fc

git cherry-pick 9f0537e 8944529 d5d80ac cdcce68 ee4944e
git cherry-pick dfa4c8e 6e84748 2ff4860
# includes the actual device-side charging-limit fix
git cherry-pick 7ce0d7c 54db2cf
```

If you also want the related Lunaris-side app work:

```bash
git -C packages/apps/Launcher3 cherry-pick 988373bab5e969b3967c9fee3af78322f7e865fc
```

## Commits That Can Also Help Other ROMs

These are the commits from this guide that are more likely to be useful outside Lunaris too:

- [`8944529`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/89445290853279b09b8e19982f3e983f91a45bfb): brings in a larger optimization-focused base
  warning: read it line by line before reusing it
- [`d5d80ac`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d5d80ac2b26802a5e226443db64477261aeb3d92): adds memory and network tuning
  warning: tune this against your own RAM size and network stack
- [`cdcce68`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cdcce68e42ac202620773b688b72c087e2e6c025): improves UI responsiveness
  warning: scheduler and GPU tuning do not transfer equally well to every device
- [`ee4944e`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ee4944e06e6ec2016d78d9dd3cd8e83fbc10ba56): makes build config more explicit
  warning: only useful if your product setup has the same ambiguity
- [`988373b`](https://github.com/LunarisPacman/packages_apps_Launcher3/commit/988373bab5e969b3967c9fee3af78322f7e865fc): polishes close-to-home animations
  warning: check your Launcher3 base before picking it directly

## Do Not Pick These Blindly

- older broken experiments are not part of this guide
- the public `23.2` branch also has later haptics tuning from another author, but this page intentionally tracks `TwistedVision518` commits only
- if a commit is not listed here, do not assume it belongs in the stack
- start with the `Required` section first, then move to `Recommended`, then `Optional`

## Closing Note

This is the public Lunaris commit stack I would point same-device builders to first, plus the related app commits that are worth checking when they fit the feature set you are shipping.
