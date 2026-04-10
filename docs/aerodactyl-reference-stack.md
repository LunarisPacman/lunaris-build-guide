# Aerodactyl Reference Stack

This page lists the public `23.2` Aerodactyl commits made by `TwistedVision518` for the Nothing Phone 2a / 2a Plus family.

It is written for people building Lunaris on the same device family, so the descriptions are kept short and easy to follow.

## How To Read This

- `Short note` gives the quick reason for the commit
- `What it does` gives a slightly clearer explanation
- `Can help other ROMs` marks the commits that may be useful outside Lunaris too

## Commit Order For Same-Device Builders

These are listed in the same order they appear in the current public `23.2` history after `ecc640e`.

| Commit | Short note | What it does | Can help other ROMs |
| --- | --- | --- | --- |
| [`1c6e163`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/1c6e163f5543bcf67e7a4d3d5a360bb451ec2fd2) | Temporary fix for PacmanPro AVB. | Keeps the Plus variant moving while AVB setup is still being sorted out. | `No` |
| [`ae010f2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ae010f21508b8442f4ad7854d75e24efa0d48d1c) | Adds Lunaris-specific setup. | Brings in the product-side changes needed for Lunaris. | `No` |
| [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc) | Improves refresh-rate handling. | Tunes display refresh-rate behavior so the phone feels smoother. | `Yes` |
| [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a) | Makes blur less expensive. | Reduces the performance cost of heavy blur effects. | `Yes` |
| [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7) | First main optimization batch. | Pulls in the first larger set of performance-focused changes. | `Yes, review first` |
| [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09) | Adds memory and network tuning. | Improves the stack further with ZRAM, DEX preopt, and TCP tuning. | `Yes, review first` |
| [`084aed6`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/084aed6c7b1f0f50d76a64542380628ba706b5fd) | Relaxes thermal limits a bit. | Lets the device hold performance longer before throttling. | `Maybe` |
| [`43b0496`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/43b0496356d4436f413f7903ec2e9b4e4ed21829) | Cleans up haptic mapping. | Makes vibration effects feel more consistent. | `Maybe` |
| [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582) | Pushes UI responsiveness further. | Tunes CPU and GPU behavior to make the UI feel snappier. | `Yes, review first` |
| [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2) | Defines the partition filesystem type. | Makes the product config clearer and safer during build setup. | `Yes` |
| [`d8c3530`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d8c3530b71ca01fba47ceb02b135390de5870510) | Fixes parsing and haptics timing. | Corrects product config handling and a haptics completion issue. | `Partly` |
| [`cd3011d`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cd3011d2e3a0b9694400df4e23fb9091bde65b6e) | Cleans up metadata and props. | Fixes duplicate props and tidies up product information. | `No` |
| [`9827b49`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9827b49f7223f1dc1a64707c21b24795a934579d) | Adds ViPER config. | Pulls in the config side of ViPER4AndroidFX support. | `No` |
| [`e5d8faa`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/e5d8faa556af49900c76828254b3381b2b37f761) | Wires Lunaris extras. | Adds the Lunaris-side plumbing for ViPER, FaceUnlock, and emoji features. | `No` |
| [`92471ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/92471aea06fb377e24b078a0c8684cf9122d50c8) | Final UX balance pass. | Rebalances haptics and display transitions after the earlier tuning work. | `Maybe` |

## Quick Pick Order

If you only want the short version for the same device family, use this order:

1. `1c6e163`
2. `ae010f2`
3. `4e0bc89`
4. `0ca4cde`
5. `c7c74d4`
6. `0e586ab`
7. `084aed6`
8. `43b0496`
9. `c6396f4`
10. `b3a65b2`
11. `d8c3530`
12. `cd3011d`
13. `9827b49`
14. `e5d8faa`
15. `92471ae`

## Commits That Can Also Help Other ROMs

These are the commits from this stack that are more likely to be useful outside Lunaris too:

- [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc): improves refresh-rate behavior
- [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a): reduces the cost of blur effects
- [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7): brings in a larger performance-focused base
- [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09): adds memory and network tuning
- [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582): improves UI responsiveness
- [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2): makes build config more explicit

These are the ones most likely to transfer cleanly, but they should still be reviewed before being reused on another device or ROM.
