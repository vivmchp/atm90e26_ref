# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a KiCad 10.0 project for an ATM90E26A single-phase energy metering evaluation board. The ATM90E26 is a Microchip high-precision energy metering IC that measures voltage, current, power, and energy for single-phase two-wire or three-wire configurations.

## Project Structure

```
ATM90E26_Test/
├── ATM90E26_EVAL/ATM90E26_EVAL/   # Main KiCad project
│   ├── ATM90E26_EVAL.kicad_sch    # Schematic (A3 paper)
│   ├── ATM90E26_EVAL.kicad_pcb    # PCB layout
│   ├── ATM90E26_EVAL.kicad_pro    # Project configuration
│   └── .history/                   # KiCad automatic local backup (File > Local History)
├── symbols/                        # Custom component libraries
│   └── ul_MIC5209-3-3YS-TR/       # LDO regulator symbol/footprint
└── ZMPT101B.pdf, ZMPT101B_1.xlsx  # Voltage transformer reference data
```

## Key Components

- **ATM90E26-YU**: Main energy metering IC (SSOP-28)
- **ZMPT101K**: Voltage transformer (1000:1000, 2mA:2mA) for AC voltage sensing
- **MIC5209-3.3YS-TR**: 3.3V LDO voltage regulator
- **J5 (10-pin header)**: MCU interface for SPI communication

## Design Rules

Default net class:
- Track width: 0.2mm
- Via: 0.6mm diameter, 0.3mm drill
- Clearance: 0.2mm

**HighVoltage** net class (for AC mains traces):
- Track width: 1.0mm
- Via: 1.6mm diameter, 1.0mm drill
- Clearance: 1.0mm

Teardrop pads enabled for PTH, SMD pads, and vias.
