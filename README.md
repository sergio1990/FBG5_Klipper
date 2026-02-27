# FBG5 Klipper Configuration

This repository contains Klipper-related configuration and notes for a modified Flying Bear Ghost 5 printer.

## Printer Overview

- Flying Bear Ghost 5
- MKS Robin Nano v1.2 motherboard
- Direct drive mod
- Filament sensor enabled

## Control and Web Interfaces

- OctoPrint as one web interface option for printer control and monitoring
- Klipper with Fluidd as an alternative web interface stack

## Host Device

- Raspberry Pi 4 (4-core CPU, 8 GB RAM)
- Hosts OctoPrint and Klipper services
- Connected to the printer over USB serial

## Repository Files

- `printer.cfg` - main Klipper printer configuration
- `macroses.cfg` - START/END and related Klipper macros

## OrcaSlicer Configuration

See the detailed OrcaSlicer profile and machine G-code setup here:

- [ORCA_SLICER_FBG5_KLIPPER.md](./ORCA_SLICER_FBG5_KLIPPER.md)

