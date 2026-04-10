# Lunaris Build Guide

This repo is a reference guide for bringing up a new Lunaris build without having to piece everything together from scattered commit history.

Right now the notes are based on the current `23.2` bring-up work for the Nothing Phone 2a / 2a Plus family:

- `Pacman` (`Nothing Phone 2a`)
- `PacmanPro` (`Nothing Phone 2a Plus`)
- common tree: `Aerodactyl`

This is mainly written for builders working on the same device family, not as a generic Android bring-up tutorial. The goal is simple: document the Lunaris-side source changes that mattered, link the exact commits, and give each one a short plain-English note so it is easier to see what is actually worth picking.

## How To Use This Repo

1. Start from a clean, current Lunaris `23.2` source tree.
2. If you are building for `Pacman` or `PacmanPro`, use the reference stack in [docs/aerodactyl-reference-stack.md](docs/aerodactyl-reference-stack.md) as your main checklist.
3. Read the short one-line note for each commit first, then open the link if you need the exact patch.
4. Treat the `Reusable elsewhere` notes seriously. Some commits are generally useful, some are Lunaris-only, and some only make sense for this device family.
5. Do not blindly pick old experiments. The guide includes a short list of commits that were intentionally superseded because they caused regressions.

## What This Covers

- Lunaris-specific product integration for the Nothing Phone 2a / 2a Plus family
- source-side fixes that were needed outside the device tree
- the current Aerodactyl commit stack on `23.2`, with short one-line descriptions
- a quick read on what can be adapted by other ROM maintainers

## What This Does Not Cover

- kernel bring-up
- vendor extraction
- SELinux policy authoring from scratch
- generic AOSP/Lineage build setup

If you are using this as a base for another device, the safest approach is to copy the structure of the work, not blindly mirror every commit.
