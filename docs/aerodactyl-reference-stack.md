# Aerodactyl Reference Stack

This is the source-side reference stack for the current Lunaris `23.2` bring-up of the Nothing Phone 2a / 2a Plus family.

This document is mainly for people building Lunaris on the same device family. It is meant to be a quick builder reference, not a deep technical write-up.

The goal is to make it easy to answer three questions:

1. Which commits were actually needed?
2. What does each commit do in plain English?
3. Which ones are worth looking at for other ROMs or devices?

## Base Assumption

These notes assume you are already building against the current Lunaris `23.2` branch and that your device tree itself is in a bootable state.

For Aerodactyl-based builds, the easiest way to use this page is:

1. Read the `Short note` column first.
2. Open the commit link if you need the exact patch.
3. Use the `Reusable elsewhere` column to decide whether a change is safe to copy into other ROMs.

## Source-Side Requirement Outside The Device Tree

This fix lives outside `android_device_nothing_Aerodactyl`, but it matters if you are working with the same charging-control path and an older source checkout.

| Repo | Commit | Short note | Why it matters | Reusable elsewhere |
| --- | --- | --- | --- | --- |
| `android_hardware_lineage_interfaces` | [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) | Fixes the Health Soong config type error. | Required if your source tree still errors on toggle-only charging control config. | `Yes`, if your tree does not already include it |

## Device Tree Reference Commits

These are listed in the same order they land in the current public `23.2` history after `ecc640e`.

| Commit | Short note | What it does | Scope | Reusable elsewhere |
| --- | --- | --- | --- | --- |
| [`1c6e163`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/1c6e163f5543bcf67e7a4d3d5a360bb451ec2fd2) | Temporary AVB workaround for the Plus SKU. | Temporarily comments out PacmanPro AVB flags while the SKU setup is still being aligned. | Device-specific | `No` |
| [`ae010f2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ae010f21508b8442f4ad7854d75e24efa0d48d1c) | Adds the Lunaris-side product hooks. | Adds Lunaris-specific product configuration. | Lunaris-specific | `No` |
| [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc) | Refines refresh-rate policy for smoother display behavior. | Sets SurfaceFlinger refresh-rate categories to make display behavior feel more deliberate. | Mostly generic tuning | `Yes, with review` |
| [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a) | Tells the system to treat blur as expensive. | Marks blur usage as expensive to cut down unnecessary UI cost. | Mostly generic tuning | `Yes, with review` |
| [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7) | Pulls in the first big optimization batch. | Pulls in a broader optimization set that became the base for later performance work. | Mixed | `Yes, but read it line by line` |
| [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09) | Adds memory and network tuning on top of the base stack. | Enables ZRAM zstd, DEX preopt tuning, and TCP Fast Open adjustments. | Mostly generic tuning | `Yes, with review` |
| [`084aed6`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/084aed6c7b1f0f50d76a64542380628ba706b5fd) | Loosens thermal throttling a bit for sustained performance. | Raises thermal skin thresholds for better sustained performance. | Device thermal tuning | `Maybe`, only after device validation |
| [`43b0496`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/43b0496356d4436f413f7903ec2e9b4e4ed21829) | Cleans up how haptic effects are mapped. | Refines haptic effect mapping. | Device-specific UX tuning | `Maybe`, if your haptics stack is similar |
| [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582) | Pushes UI responsiveness with scheduler and GPU tuning. | Improves UI responsiveness with CPU `uclamp` and GPU boost changes. | Mostly generic tuning | `Yes, with review` |
| [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2) | Makes the partition filesystem type explicit. | Explicitly defines `PRODUCT_SYSTEM_PARTITIONS_FILE_SYSTEM_TYPE`. | Build/config hygiene | `Yes` |
| [`d8c3530`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d8c3530b71ca01fba47ceb02b135390de5870510) | Fixes product parsing and a haptics timing bug. | Fixes product config parsing and corrects haptics completion timing. | Mixed | `Partly` |
| [`cd3011d`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cd3011d2e3a0b9694400df4e23fb9091bde65b6e) | Cleans up device metadata and duplicate props. | Cleans up SKU metadata and duplicate props. | Device-specific cleanup | `No` |
| [`63e90b8`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/63e90b8e5b1e12fec5523bf42c4407a2b56e2cf5) | Fixes fingerprint result parsing for this stack. | Parses fingerprint enumerate/remove results as FID arrays. | Device-side fingerprint fix | `Maybe`, for similar fingerprint stacks |
| [`d7d36f9`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d7d36f94e5278df42e53b5c4cfb592f270b61fbb) | Sends the needed speaker calibration values into ADSP. | Manually sends calibration values into TFA ADSP. | Audio hardware-specific | `No` |
| [`2f7a3db`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/2f7a3dbad16ad805ae978769c18ca856537de55b) | Drops sepolicy that is already covered by common policy. | Removes duplicated `sysfs_wakeup` policy now covered by common sepolicy. | Device policy cleanup | `Maybe`, if you have the same duplication |
| [`d40751b`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d40751b1ab190769f2f0d6f0e0d0533d8bf1bb28) | Restores overlays this device still depends on. | Restores some overlays from MSSI common overlays. | Device-specific | `No` |
| [`af8605f`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/af8605fdb0b05b01bb1e47b3af329f3b2c725fd9) | Adds NothingDirac support back into the tree. | Adds NothingDirac integration. | Device/vendor feature | `No` |
| [`5af6d70`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/5af6d70ed4a5142ee0d10b34ad10d1f9ef3504be) | Fixes the memtrack target naming mismatch. | Updates the memtrack target name to match current expectations. | Build integration fix | `Yes`, if you hit the same target-name mismatch |
| [`9827b49`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9827b49f7223f1dc1a64707c21b24795a934579d) | Pulls in the ViPER4AndroidFX config layer. | Inherits ViPER4AndroidFX config. | Lunaris feature integration | `Lunaris-only` |
| [`e5d8faa`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/e5d8faa556af49900c76828254b3381b2b37f761) | Wires Lunaris extras like ViPER, FaceUnlock, and emoji plumbing. | Wires ViPER4AndroidFX, FaceUnlock, and emoji-related plumbing. | Lunaris feature integration | `Lunaris-only` |
| [`92471ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/92471aea06fb377e24b078a0c8684cf9122d50c8) | Rebalances the final haptics and transition feel. | Balances haptics and display transitions after the earlier tuning work. | Device UX tuning | `Maybe`, only after device testing |

## Recommended Pick Order For Same-Device Builders

If you are building for the same device family and only want the practical order:

1. Apply the external Health fix first: [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) if your source tree still needs it.
2. Pick the Lunaris product and base commits: [`1c6e163`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/1c6e163f5543bcf67e7a4d3d5a360bb451ec2fd2) and [`ae010f2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/ae010f21508b8442f4ad7854d75e24efa0d48d1c).
3. Pick the main performance and UX stack in order: [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc), [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a), [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7), [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09), [`084aed6`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/084aed6c7b1f0f50d76a64542380628ba706b5fd), [`43b0496`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/43b0496356d4436f413f7903ec2e9b4e4ed21829), [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582).
4. Pick the cleanup and correctness fixes after that: [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2), [`d8c3530`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d8c3530b71ca01fba47ceb02b135390de5870510), [`cd3011d`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/cd3011d2e3a0b9694400df4e23fb9091bde65b6e), [`63e90b8`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/63e90b8e5b1e12fec5523bf42c4407a2b56e2cf5), [`d7d36f9`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d7d36f94e5278df42e53b5c4cfb592f270b61fbb), [`2f7a3db`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/2f7a3dbad16ad805ae978769c18ca856537de55b), [`d40751b`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/d40751b1ab190769f2f0d6f0e0d0533d8bf1bb28), [`af8605f`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/af8605fdb0b05b01bb1e47b3af329f3b2c725fd9), [`5af6d70`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/5af6d70ed4a5142ee0d10b34ad10d1f9ef3504be).
5. Finish with the Lunaris feature layer and the final balancing pass: [`9827b49`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/9827b49f7223f1dc1a64707c21b24795a934579d), [`e5d8faa`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/e5d8faa556af49900c76828254b3381b2b37f761), [`92471ae`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/92471aea06fb377e24b078a0c8684cf9122d50c8).

## Commits Other ROM Maintainers Should Look At First

If you are not building Lunaris itself and you only want the more transferable pieces, start here:

- [`4e0bc89`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/4e0bc8973f8c1dc60c9d6cd18b1842794b144ddc)
- [`0ca4cde`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0ca4cde05d7f663cfc6ea0f651dbdb38bf367a8a)
- [`c7c74d4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c7c74d463c1ed93b33d0d5b4a6317a076694c1c7)
- [`0e586ab`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/0e586ab613c6bdbec2836a8221b1125fcb0f4f09)
- [`c6396f4`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/c6396f47b23bbbf88ab3da533008e2c6ed93c582)
- [`b3a65b2`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b3a65b23acbb2bd9ec58f6777e126d235511f0e2)
- [`5af6d70`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/5af6d70ed4a5142ee0d10b34ad10d1f9ef3504be)

Even then, review them against your own kernel, thermal profile, GPU stack, and feature set before picking them.

## Known Superseded Commits

These older commits are worth mentioning because they look tempting in history, but they should not be reused as-is:

- [`879d147`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/879d147756d439ac04350d129baeab58374daf26)
  - switched charging control to `charging_control_enabled_path`
  - this was the wrong direction for the Aerodactyl charging node and was intentionally dropped from the cleaned public history
- [`b7b6539`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/b7b653924414789e99ecaf9ac2d60619f6d3fcd4)
  - advertised unsafe high sample rates on the built-in speaker path
  - this caused stutter and was not kept

## Final Note

The easiest mistake during bring-up is treating every performance or UX commit like a generic upgrade. It almost never works that cleanly. Use the commit list as a reference stack, not a blind cherry-pick queue.
