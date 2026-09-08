# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a KiCad 10.0 project for an ATM90E26A single-phase energy metering evaluation board. The ATM90E26 is a Microchip high-precision energy metering IC that measures voltage, current, power, and energy for single-phase two-wire or three-wire configurations.

## Key Components

- **ATM90E26-YU**: Main energy metering IC (SSOP-28 package)
- **ZMPT101K**: Voltage transformer (1000:1000, 2mA:2mA) for AC voltage sensing
- **MIC5209-3.3YS-TR**: 3.3V LDO voltage regulator
- **10-pin header (J1)**: MCU interface connector for SPI communication

## Project Files

- `ATM90E26_EVAL.kicad_sch` - Schematic (A3 paper size)
- `ATM90E26_EVAL.kicad_pcb` - PCB layout
- `ATM90E26_EVAL.kicad_pro` - Project configuration

## External Resources

- Custom symbol library for MIC5209-3.3YS-TR located at `../symbols/ul_MIC5209-3-3YS-TR/KiCADv6/`
- Related ZMPT101B voltage transformer data at `../../ZMPT101B.pdf` and `.xlsx` files
- Reference firmware at `../../ATAK51005-V1-Software/` (ATAK51005 evaluation kit software)

## Design Notes

The board uses:
- Default track width: 0.2mm
- Default via: 0.6mm diameter, 0.3mm drill
- Minimum clearance: 0.2mm
- Teardrop pads enabled for PTH, SMD pads, and vias

The `.history/` folder contains KiCad's automatic local backup snapshots (File > Local History menu).
