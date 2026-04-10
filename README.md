# Lunaris Build Guide

This repo is a commit guide for people building Lunaris on the Nothing Phone 2a / 2a Plus family.

It exists to answer one practical question:

which public Aerodactyl commits should I pick for Lunaris, and in what order?

This is not a source repo and it is not a full bring-up tutorial. It is a guide to the public commit stack.

## Start Here

- If you are building Lunaris for `Pacman` or `PacmanPro`, follow this guide.
- If your tree already builds or boots, start with the commit list.
- If you are from another ROM, only use the reusable commits section.

## Who This Is For

- people building Lunaris for `Pacman` (`Nothing Phone 2a`)
- people building Lunaris for `PacmanPro` (`Nothing Phone 2a Plus`)
- people using the common tree `Aerodactyl`

## What This Repo Actually Does

- lists the public Aerodactyl `23.2` commits made by `TwistedVision518`
- explains each commit in simple language
- separates the stack into `Required`, `Recommended`, and `Optional`
- gives a clean pick order with ready-to-use cherry-pick commands
- points out which commits may also help other ROMs

## What This Repo Assumes

- you are building on Lunaris `23.2`
- you already have the device tree, vendor side, and basic bring-up in place
- you want a guide to the commit stack, not a full device bring-up manual

## What This Repo Does Not Do

- it does not replace your device tree
- it does not contain the source changes themselves
- it does not explain full Android bring-up from scratch

## Main Guide

See [docs/aerodactyl-reference-stack.md](docs/aerodactyl-reference-stack.md).

If someone asks what this repo is for, the short answer is:

this is a commit guide for building Lunaris on the Nothing Phone 2a / 2a Plus family.
