# ATM90E26A Evaluation Board

KiCad 10.0 design for a single-phase energy metering evaluation board based on the Microchip ATM90E26A IC.

## Features

- **ATM90E26A** high-precision energy metering IC (SSOP-28)
- **ZMPT101K** voltage transformer (1000:1000) for isolated AC voltage sensing
- **MIC5209-3.3YS-TR** LDO for 3.3V power supply
- 10-pin header for MCU interface (SPI communication)
- Single-phase two-wire or three-wire configuration support

## Project Files

| File | Description |
|------|-------------|
| `ATM90E26_EVAL/ATM90E26_EVAL/*.kicad_*` | KiCad schematic, PCB, and project files |
| `symbols/ul_MIC5209-3-3YS-TR/` | Custom symbol and footprint for LDO regulator |
| `ZMPT101B.pdf` | Voltage transformer reference datasheet |

## MCU Interface (J5)

| Pin | Signal | Description |
|-----|--------|-------------|
| 1 | +3.3V | 3.3V power |
| 2 | GND | Ground |
| 3 | ATM_SDI | SPI data in (MOSI to ATM90E26) |
| 4 | ATM_SDO | SPI data out (MISO from ATM90E26) |
| 5 | ATM_CLK | SPI clock |
| 6 | ATM_CS | Chip select (active low) |
| 7 | ATM_IRQ | Interrupt output |
| 8 | ATM_CF1 | Energy pulse output |
| 9 | SCL | I2C clock (for EEPROM) |
| 10 | SDA | I2C data (for EEPROM) |

## Design Rules

- Default track: 0.2mm, via 0.6mm/0.3mm drill
- High voltage traces: 1.0mm track, 1.0mm clearance

## Requirements

- KiCad 10.0 or later

## License

Reference design for evaluation purposes.
