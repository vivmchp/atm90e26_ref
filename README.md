# ATM90E26A Evaluation Board

KiCad 10.0 design for a single-phase energy metering evaluation board based on the Microchip ATM90E26A IC.

## Features

- **ATM90E26A** high-precision energy metering IC (SSOP-28)
- **HLK-10M12** AC/DC power module (100-240VAC input, 12VDC/10W output)
- **ZMPT101K** voltage transformer (1000:1000) for isolated AC voltage sensing
- **MIC5209-3.3YS-TR** LDO for 3.3V power supply
- **24C02C** I2C EEPROM for calibration data storage
- **10D561** varistor for surge protection
- 10-pin header for MCU interface (SPI + I2C)
- Single-phase two-wire or three-wire configuration support

## Block Diagram

```
AC Input (100-240V)
       │
       ├──► HLK-10M12 ──► 12V ──► MIC5209 ──► 3.3V
       │
       ├──► R1 (200K) ──► ZMPT101K ──► VP/VN ──► ATM90E26 (Voltage)
       │
       └──► RV1 (Varistor) ──► Surge Protection

Current Input (J2)
       │
       └──► R2/R3 ──► I1P/I1N ──► ATM90E26 (Current)

ATM90E26 ──► SPI/IRQ/CF1 ──► J5 (MCU Interface)
    │
    └──► I2C ──► 24C02C (EEPROM)
```

## Connectors

### AC Input (J1)
| Pin | Signal | Description |
|-----|--------|-------------|
| 1 | LINE | AC Live (100-240VAC) |
| 2 | NEUT | AC Neutral |

### Current Input (J2)
| Pin | Signal | Description |
|-----|--------|-------------|
| 1 | I1P | Current channel positive |
| 2 | I1N | Current channel negative |

### MCU Interface (J5)
| Pin | Signal | Description |
|-----|--------|-------------|
| 1 | +3.3V | 3.3V power output |
| 2 | GND | Ground |
| 3 | ATM_SDI | SPI data in (MOSI to ATM90E26) |
| 4 | ATM_SDO | SPI data out (MISO from ATM90E26) |
| 5 | ATM_CLK | SPI clock |
| 6 | ATM_CS | Chip select (active low) |
| 7 | ATM_IRQ | Interrupt output |
| 8 | ATM_CF1 | Energy pulse output |
| 9 | SCL | I2C clock (1K pull-up) |
| 10 | SDA | I2C data (1K pull-up) |

## PCB Specifications

| Parameter | Value |
|-----------|-------|
| Board size | 80mm × 70mm |
| Layers | 2 (Top + Bottom copper) |
| Thickness | 1.6mm |
| Default track | 0.2mm |
| Default via | 0.6mm / 0.3mm drill |
| HV track | 1.0mm |
| HV clearance | 1.0mm |

## Bill of Materials

| Ref | Part | Value | Package |
|-----|------|-------|---------|
| U1 | HLK-10M12 | 12V/10W | Module |
| U2 | ATM90E26-YU | - | SSOP-28 |
| U3 | MIC5209-3.3YS-TR | 3.3V | SOT-223 |
| U4 | 24C02C | 2Kbit | SOIC-8 |
| TR1 | ZMPT101K | 1000:1000 | Through-hole |
| Y1 | Crystal | 8.192MHz | HC49-U |
| RV1 | Varistor | 10D561 | Disc |
| R1 | Resistor | 200K/3W | Axial |
| C13, C14 | Capacitor | 12pF | 0603 |

## Requirements

- KiCad 10.0 or later

## License

Reference design for evaluation purposes.
