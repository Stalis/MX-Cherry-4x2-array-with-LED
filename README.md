# MX Cherry 4x2

Compact 8-key Cherry MX keyboard module: 4 columns x 2 rows. It has no onboard microcontroller and is intended for connection to an external controller or breadboard.

## Features

- 8 Cherry MX 1U, PCB-mount switch footprints on a 19.05 mm pitch.
- 4x2 switch matrix with one diode per key.
- Independent 4x2 LED matrix with one LED per key.
- Two parallel SMD socket connectors, `J1` and `J2`: 2x10, 2.54 mm pitch, on the bottom side of the board.
- Two-layer, 1.6 mm thick PCB measuring 78.74 x 38.10 mm.

## Matrices

Key layout:

|       | `COL_0` | `COL_1` | `COL_2` | `COL_3` |
| --- | --- | --- | --- | --- |
| `ROW_0` | SW1 / D1 / RLED1 | SW2 / D2 / RLED2 | SW3 / D3 / RLED3 | SW4 / D4 / RLED4 |
| `ROW_1` | SW5 / D5 / RLED5 | SW6 / D6 / RLED6 | SW7 / D7 / RLED7 | SW8 / D8 / RLED8 |

Each key has a series diode, `D1` through `D8`, to prevent ghosting during matrix scanning. LEDs `RLED1` through `RLED8` form an independent matrix with the same four columns and two rows.

## Connections

`J1` and `J2` are electrically identical: use either connector, or both to mount the module. Pin numbering follows the standard 2x10 connector convention: odd pins are on one row and even pins on the other.

| Pin | Signal | Function |
| --- | --- | --- |
| 1 | `SW_0_ROW_0` | switch-matrix row 0 |
| 2 | `LED_0_ROW_0` | LED-matrix row 0 |
| 3 | `SW_0_ROW_1` | switch-matrix row 1 |
| 4 | `LED_0_ROW_1` | LED-matrix row 1 |
| 5-12 | NC | not connected |
| 13 | `SW_0_COL_0` | switch-matrix column 0 |
| 14 | `LED_0_COL_0` | LED-matrix column 0 |
| 15 | `SW_0_COL_1` | switch-matrix column 1 |
| 16 | `LED_0_COL_1` | LED-matrix column 1 |
| 17 | `SW_0_COL_2` | switch-matrix column 2 |
| 18 | `LED_0_COL_2` | LED-matrix column 2 |
| 19 | `SW_0_COL_3` | switch-matrix column 3 |
| 20 | `LED_0_COL_3` | LED-matrix column 3 |

The controller must scan both matrices externally. The PCB has no LED current-limiting resistors; use an external current-limiting circuit or LED driver.

## Components

| Quantity | References | Footprint |
| --- | --- | --- |
| 8 | `SW1-SW8` | Cherry MX 1U, PCB mount |
| 8 | `D1-D8` | SOD-323F |
| 8 | `RLED1-RLED8` | LED 1206, 3216 Metric |
| 2 | `J1`, `J2` | SMD socket 2x10, 2.54 mm |

The schematic does not specify diode ratings or LED color and electrical parameters. Select them for the voltage and current of the external driver.

## Repository Files

- `MX Cherry 4x2.kicad_pro` - KiCad project.
- `MX Cherry 4x2.kicad_sch` - main schematic.
- `MX Cherry 4x2.kicad_pcb` - PCB layout.
- `switch_module.kicad_sch` and `led_module.kicad_sch` - reusable sheets for one switch with a diode and one LED.
- `jlcpcb/` and `production/` - previously exported manufacturing files.

> The BOM and CPL files in `jlcpcb/` and `production/` are outdated relative to the current schematic and PCB. They omit `RLED1` through `RLED8` and describe the connectors as 1x10. Re-export Gerbers, BOM, and CPL from the current project before ordering.

## Opening and Checking

The project was created with KiCad 10. Open `MX Cherry 4x2.kicad_pro` in KiCad, or check it from the command line:

```sh
/Applications/KiCad/KiCad.app/Contents/MacOS/kicad-cli sch erc "MX Cherry 4x2.kicad_sch"
/Applications/KiCad/KiCad.app/Contents/MacOS/kicad-cli pcb drc --schematic-parity "MX Cherry 4x2.kicad_pcb"
```
