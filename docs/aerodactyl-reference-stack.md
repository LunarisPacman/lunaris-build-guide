# Aerodactyl Reference Stack

This page is the main part of the guide.

Its job is simple:

show the public `23.2` Aerodactyl commits made by `TwistedVision518` that builders may want when making Lunaris for the Nothing Phone 2a / 2a Plus family.

## Last Verified

- branch: `lunaris/23.2`
- date: `2026-04-11`

## What This Page Assumes

- you are building Lunaris `23.2`
- you already have a usable Aerodactyl tree
- you want to know which commits are worth picking and in what order

## Charging Limit Note

The charging-limit fix is split across two places:

- the actual device-side behavior fix is in [`92471ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/92471aea06fb377e24b078a0c8684cf9122d50c8), where the Aerodactyl tree sets the correct charging node, inverted values, and toggle support
- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) only fixes the Health HAL Soong selector types so the charging-control config can build correctly

So if someone is looking for the real charging-limit behavior fix, the important Aerodactyl-side change is the one carried by `92471ae`.

## How To Read This

- `Required` means the commit is part of the core stack for this guide
- `Recommended` means the commit is useful, but not absolutely essential
- `Optional` means the commit is more device-taste or tuning related
- `Can help other ROMs` marks commits that may be useful outside Lunaris too

## Required For Lunaris Bring-Up

These are the commits that form the main stack for this guide.

| Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- |
| [`1c6e163`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/1c6e163f5543bcf67e7a4d3d5a360bb451ec2fd2) | `Required` | Temporary fix for PacmanPro AVB. | Keeps the Plus variant moving while AVB setup is still being sorted out. | `No` |
| [`ae010f2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ae010f21508b8442f4ad7854d75e24efa0d48d1c) | `Required` | Adds Lunaris-specific setup. | Brings in the product-side changes needed for Lunaris. | `No` |
| [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2) | `Required` | Defines the partition filesystem type. | Makes the product config clearer and safer during build setup. | `Yes` |
| [`d8c3530`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d8c3530b71ca01fba47ceb02b135390de5870510) | `Required` | Fixes parsing and haptics timing. | Corrects product config handling and a haptics completion issue. | `Partly` |
| [`cd3011d`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cd3011d2e3a0b9694400df4e23fb9091bde65b6e) | `Required` | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| [`9827b49`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9827b49f7223f1dc1a64707c21b24795a934579d) | `Required` | Adds ViPER config. | Pulls in the config side of ViPER4AndroidFX support. | `No` |
| [`e5d8faa`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/e5d8faa556af49900c76828254b3381b2b37f761) | `Required` | Wires Lunaris extras. | Adds the Lunaris-side plumbing for ViPER, FaceUnlock, and emoji features. | `No` |
| [`92471ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/92471aea06fb377e24b078a0c8684cf9122d50c8) | `Required` | Fixes charging limit behavior. | Adds the real device-side charging-limit fix for `/proc/charger/usb_charger_en` and also rebalances haptics and display transitions. | `Maybe` |

## Recommended Improvements

These are the commits that make the build feel better or behave better on the same device family.

| Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- |
| [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc) | `Recommended` | Improves refresh-rate handling. | Tunes display refresh-rate behavior so the phone feels smoother. | `Yes` |
| [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a) | `Recommended` | Makes blur less expensive. | Reduces the performance cost of heavy blur effects. | `Yes` |
| [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7) | `Recommended` | First main optimization batch. | Pulls in the first larger set of performance-focused changes. | `Yes, review first` |
| [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09) | `Recommended` | Adds memory and network tuning. | Improves the stack further with ZRAM, DEX preopt, and TCP tuning. | `Yes, review first` |
| [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582) | `Recommended` | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |

## Optional Device Tuning

These are more taste-dependent or device-tuning commits.

| Commit | Level | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- | --- |
| [`084aed6`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/084aed6c7b1f0f50d76a64542380628ba706b5fd) | `Optional` | Relaxes thermal limits a bit. | Lets the device hold performance longer before throttling. | `Maybe` |
| [`43b0496`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/43b0496356d4436f413f7903ec2e9b4e4ed21829) | `Optional` | Cleans up haptic mapping. | Makes vibration effects feel more consistent. | `Maybe` |

## Cherry-Pick Order

If you want the safest order, use the same order as the public `23.2` history:

1. `1c6e163` - temporary PacmanPro AVB workaround
2. `ae010f2` - adds Lunaris-specific product setup
3. `4e0bc89` - improves refresh-rate handling
4. `0ca4cde` - reduces the cost of blur effects
5. `c7c74d4` - brings in the first larger optimization batch
6. `0e586ab` - adds memory and network tuning
7. `084aed6` - relaxes thermal limits a bit
8. `43b0496` - cleans up haptic mapping
9. `c6396f4` - pushes UI responsiveness further
10. `b3a65b2` - defines the partition filesystem type
11. `d8c3530` - fixes parsing and haptics timing
12. `cd3011d` - cleans up metadata and props
13. `9827b49` - adds ViPER config
14. `e5d8faa` - wires Lunaris extras
15. `92471ae` - fixes charging limit behavior and does the final UX balance pass

## Cherry-Pick Commands

These commands assume a clean and compatible Lunaris `23.2` Aerodactyl tree. If your tree already differs, you may need to resolve cherry-pick conflicts manually.

```bash
git cherry-pick 1c6e163 ae010f2 4e0bc89 0ca4cde c7c74d4
git cherry-pick 0e586ab 084aed6 43b0496 c6396f4 b3a65b2
# includes the actual device-side charging-limit fix
git cherry-pick d8c3530 cd3011d 9827b49 e5d8faa 92471ae
```

## Commits That Can Also Help Other ROMs

These are the commits from this same stack that are more likely to be useful outside Lunaris too:

- [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc): improves refresh-rate behavior
  warning: check whether your display stack uses the same refresh-rate logic
- [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a): reduces the cost of blur effects
  warning: only useful if your ROM actually uses the same blur-heavy paths
- [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7): brings in a larger performance-focused base
  warning: read it line by line before reusing it
- [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09): adds memory and network tuning
  warning: tune this against your own RAM size and network stack
- [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582): improves UI responsiveness
  warning: scheduler and GPU tuning do not transfer equally well to every device
- [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2): makes build config more explicit
  warning: only useful if your product setup has the same ambiguity

## Do Not Pick These Blindly

- older broken experiments are not part of this guide
- if a commit is not listed here, do not assume it belongs in the stack
- start with the `Required` section first, then move to `Recommended`, then `Optional`

## Closing Note

This is the public Aerodactyl commit stack I would point same-device builders to first when building Lunaris on this device family.
