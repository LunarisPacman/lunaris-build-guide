# Lunaris Build Guide

This repo is a commit guide for people building Lunaris for the Nothing Phone 2a / 2a Plus family.

It exists to answer one practical question:

which public commits should I pick for Lunaris, and in what order?

This is not a source repo and it is not a full bring-up tutorial. It is a guide to the public commit stack.

## Start Here

- If you are building Lunaris for `Pacman` or `PacmanPro`, follow this guide.
- If your tree already builds or boots, start with the commit list.
- If you are building for another ROM, only use the reusable commits section.

## Who This Is For

- people building Lunaris for `Pacman` (`Nothing Phone 2a`)
- people building Lunaris for `PacmanPro` (`Nothing Phone 2a Plus`)
- people using the common tree `Aerodactyl`
- people who want to see the related Lunaris-side commits in `FaceUnlock`, `Launcher3`, and `frameworks_base`

## What This Repo Actually Does

- lists the public `TwistedVision518` commits that matter most for this device family
- calls out the extra `android_hardware_lineage_interfaces` commit needed for the charging-limit stack
- separates the Aerodactyl bring-up stack from related Lunaris-side work in other repos
- explains each commit in simple language
- separates the stack into `Required`, `Recommended`, and `Optional`
- gives a clean pick order with ready-to-use cherry-pick commands
- points out which commits may also help other ROMs, including DynamicBar work

## Important Note About Charging Limit

The charging-limit fix is split across two repos:

- [`8ea0fab`](https://github.com/LunarisPacman/android_hardware_lineage_interfaces/commit/8ea0fab29d6adba69a5692aa929b19a81b9a15fc) in `android_hardware_lineage_interfaces` fixes the Health HAL build-side Soong selector issue
- [`5f725da`](https://github.com/LunarisPacman/android_device_nothing_Aerodactyl/commit/5f725da678e8b35c26fe6b6e658f05d2a97cde15) in `android_device_nothing_Aerodactyl` fixes the actual device-side charging-limit behavior

## What This Repo Assumes

- you are building on Lunaris `23.2`
- you already have the device tree, vendor side, and basic bring-up in place
- you want a guide to the commit stack, not a full device bring-up manual
- you are okay with the guide focusing on `TwistedVision518` commits, plus the one extra health commit needed for charging control

## What This Repo Does Not Do

- it does not replace your device tree
- it does not contain the source changes themselves
- it does not explain full Android bring-up from scratch

## Main Guide

See [docs/aerodactyl-reference-stack.md](docs/aerodactyl-reference-stack.md).

If someone asks what this repo is for, the short answer is:

this is a commit guide for building Lunaris on the Nothing Phone 2a / 2a Plus family, with a small index of related commits from other Lunaris repos.
