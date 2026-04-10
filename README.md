# Lunaris Build Guide

This repo exists for one reason:

to help builders making Lunaris for the Nothing Phone 2a and 2a Plus understand which Aerodactyl commits they should pick, in what order, and why those commits matter.

This is not a source repo and it is not a full bring-up tutorial. It is a guide to the public commit stack.

## Who This Is For

- people building Lunaris for `Pacman` (`Nothing Phone 2a`)
- people building Lunaris for `PacmanPro` (`Nothing Phone 2a Plus`)
- people using the common tree `Aerodactyl`

## What This Repo Actually Does

- lists the public Aerodactyl `23.2` commits made by `TwistedVision518`
- gives each commit a short, simple description
- shows a sensible pick order for builders on the same device family
- points out which commits may also help other ROMs

## What This Repo Does Not Do

- it does not replace your device tree
- it does not contain the source changes themselves
- it does not explain full Android bring-up from scratch

## How To Use This Repo

1. Start from a clean Lunaris `23.2` source tree.
2. Open [docs/aerodactyl-reference-stack.md](docs/aerodactyl-reference-stack.md).
3. Go through the commits in the order shown there.
4. Read the short description first.
5. Open the linked commit when you want the exact patch.

If someone asks what this repo is for, the short answer is:

this is a commit guide for building Lunaris on the Nothing Phone 2a / 2a Plus family.
