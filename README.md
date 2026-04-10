# Lunaris Build Guide

This repo is a reference guide for bringing up a new Lunaris build without having to piece everything together from scattered commit history.

Right now the notes are based on the current `23.2` bring-up work for the Nothing Phone 2a / 2a Plus family:

- `Pacman` (`Nothing Phone 2a`)
- `PacmanPro` (`Nothing Phone 2a Plus`)
- common tree: `Aerodactyl`

This is not a full Android bring-up tutorial and it is not meant to replace clean device, vendor, kernel, and sepolicy work. The point here is simpler: document the Lunaris-side source changes that mattered, link the exact commits, and call out which ones are safe to borrow for other ROMs or devices.

## How To Use This Repo

1. Start from a clean, current Lunaris `23.2` source tree.
2. Get your own device tree, kernel, vendor, and proprietary files into a buildable state first.
3. Go through the reference stack in [docs/aerodactyl-reference-stack.md](docs/aerodactyl-reference-stack.md).
4. Treat the `Reusable elsewhere` notes seriously. Some commits are generic improvements, some are Lunaris-only, and some are tightly tied to this device.
5. Do not blindly pick old experiments. The guide includes a short list of commits that were intentionally superseded because they caused regressions.

## What This Covers

- Lunaris-specific product integration
- source-side fixes that were needed outside the device tree
- the current Aerodactyl commit stack on `23.2`
- a quick read on what can be adapted by other ROM maintainers

## What This Does Not Cover

- kernel bring-up
- vendor extraction
- SELinux policy authoring from scratch
- generic AOSP/Lineage build setup

If you are using this as a base for another device, the safest approach is to copy the structure of the work, not blindly mirror every commit.
