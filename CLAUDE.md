# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a KiCad 10.0 project for an ATM90E26A single-phase energy metering evaluation board. The ATM90E26 is a Microchip high-precision energy metering IC that measures voltage, current, power, and energy for single-phase two-wire or three-wire configurations.

## Project Structure

```
ATM90E26_Test/
├── ATM90E26_EVAL/ATM90E26_EVAL/   # Main KiCad project
│   ├── ATM90E26_EVAL.kicad_sch    # Schematic (A3 paper)
│   ├── ATM90E26_EVAL.kicad_pcb    # PCB layout (80mm × 70mm, 2-layer)
│   ├── ATM90E26_EVAL.kicad_pro    # Project configuration
│   └── .history/                   # KiCad automatic local backup (File > Local History)
├── symbols/                        # Custom component libraries
│   └── ul_MIC5209-3-3YS-TR/       # LDO regulator symbol/footprint
└── ZMPT101B.pdf, ZMPT101B_1.xlsx  # Voltage transformer reference data
```

## Bill of Materials

| Ref | Part | Value | Description |
|-----|------|-------|-------------|
| U1 | HLK-10M12 | - | AC/DC converter (100-240VAC to 12VDC, 10W) |
| U2 | ATM90E26-YU | - | Energy metering IC (SSOP-28) |
| U3 | MIC5209-3.3YS-TR | - | 3.3V LDO regulator |
| U4 | 24C02C | - | I2C EEPROM for calibration storage |
| TR1 | ZMPT101K | - | Voltage transformer (1000:1000, 2mA:2mA) |
| Y1 | Crystal | 8.192MHz | ATM90E26 clock source |
| RV1 | Varistor | 10D561 | Surge protection |
| R1 | Resistor | 200K/3W | Voltage divider (high voltage) |

## Circuit Blocks

### Power Supply
- **AC Input (J1)**: 100-240VAC via LINE/NEUT terminals
- **HLK-10M12 (U1)**: Isolated AC/DC module converts to 12VDC
- **MIC5209 (U3)**: LDO regulates 12V to 3.3V for digital circuits

### Voltage Sensing
- **R1** (200K/3W): Drops AC voltage for transformer input
- **TR1** (ZMPT101K): Provides galvanic isolation, outputs VP/VN to ATM90E26

### Current Sensing
- **J2**: External current input connector
- **R2, R3** (2.7Ω): Current sense resistors
- **C3** (0.033µF): Anti-aliasing filter
- Signals I1P/I1N feed ATM90E26 current channel

### MCU Interface (J5)
- SPI: ATM_SDI, ATM_SDO, ATM_CLK, ATM_CS
- Interrupt: ATM_IRQ
- Energy pulse: ATM_CF1
- I2C for EEPROM: SCL, SDA (1K pull-ups via R4, R5)

## Design Rules

**Default net class:**
- Track width: 0.2mm
- Via: 0.6mm diameter, 0.3mm drill
- Clearance: 0.2mm

**HighVoltage net class** (LINE, NEUT traces):
- Track width: 1.0mm
- Via: 1.6mm diameter, 1.0mm drill
- Clearance: 1.0mm

**PCB:**
- Board size: 80mm × 70mm
- Layers: 2 (F.Cu, B.Cu)
- Thickness: 1.6mm
- GND zones: Hatched fill on both layers
- Teardrop pads enabled for PTH, SMD, and vias
