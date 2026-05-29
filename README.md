# Pixel 9 Boot Chain Exploration

## Overview

This project explores the Android boot process on a Pixel 9 device with a damaged display and restricted access.

The goal is to understand and interact with the early boot chain and progressively turn the device into a functional Linux-based system.

A full technical journal is available in [`journal.md`](./journal.md).

## What This Project Achieves

* Control of early Android userspace (`initramfs`)
* Analysis of boot chain (`boot.img`, `init_boot.img`)
* Custom `/init` experimentation in early boot
* Timing-based debugging (“sleep debugging”) due to lack of logs/UI
* USB gadget interfaces:

  * Serial console (ACM / ttyGS0)
  * Mass storage (userdata partition)
* Deployment of a minimal Debian ARM64 root filesystem
* Transition into Linux userspace via `chroot`

## Key Idea

Achieve a standard Linux environment on a Pixel 9 by taking control of early boot and replacing Android userspace with Debian.

## Highlights

* Early boot execution without display or logs
* Interactive shell over USB during init stage
* Repurposed `userdata` as Linux root filesystem
* Bridged Android boot chain into standard Linux userspace

## Limitations

* No `devtmpfs` → manual device management required
* No GPU acceleration (Android graphics stack remains proprietary)
* Debugging relies heavily on indirect signals (timing / USB behavior)

## Details

See [`journal.md`](./journal.md) for the full step-by-step technical log.

## Summary

A hands-on exploration of the Android boot chain that progressively transforms a locked-down mobile device into a controllable Linux system.

