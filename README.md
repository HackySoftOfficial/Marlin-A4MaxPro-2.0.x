# Marlin 2.0.x for Anycubic 4Max Pro

[![Forum](https://img.shields.io/badge/Social-Forum-blue.svg)](https://drucktipps3d.de/forum/topic/anycubic-4max-pro)
[![Latest Release](https://img.shields.io/github/release/Poket-Jony/Marlin-A4MaxPro-2.0.x.svg?style=flat&color=blue)](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/releases/latest/)
[![GitHub stars](https://img.shields.io/github/stars/Poket-Jony/Marlin-A4MaxPro-2.0.x?style=flat&color=brightgreen)](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/stargazers)
[![Downloads](https://img.shields.io/github/downloads/Poket-Jony/Marlin-A4MaxPro-2.0.x/total.svg?style=flat&color=brightgreen)](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/releases)
[![Open Issues](https://img.shields.io/github/issues-raw/Poket-Jony/Marlin-A4MaxPro-2.0.x.svg?style=flat&color=yellowgreen)](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/issues?q=is%3Aopen+is%3Aissue)
[![Closed Issues](https://img.shields.io/github/issues-closed-raw/Poket-Jony/Marlin-A4MaxPro-2.0.x.svg?style=flat&color=brightgreen)](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/issues?q=is%3Aissue+is%3Aclosed)

## Overview

This is an optimized version of [Marlin Firmware](https://github.com/MarlinFirmware/Marlin) specifically for the Anycubic 4Max Pro 3D printer. It builds upon improvements from [davidramiro](https://github.com/davidramiro/Marlin-Ai3M-2.0.x), [derhopp](https://github.com/derhopp/Marlin-with-Anycubic-i3-Mega-TFT) and [alfrank](https://drucktipps3d.de/forum/topic/anycubic-4max-pro-marlin-1-1-9-firmware-ai3m-basierend/).

## Why Use This Firmware?

- Fixes incorrect hotend thermistor configuration in stock firmware
- Adds mesh bed leveling support for uneven print beds
- Improves upon Anycubic's basic touchscreen implementation
- Updates from old Marlin RC8 to latest 2.0.x version

## Installation

> **⚠️ Warning:** Only update your firmware if you're experiencing issues. If your printer works well, there's no need to update.
>
> You can always revert to the [original Anycubic firmware (v1.1.7)](https://drive.google.com/file/d/1FwKHQcOxPabLgirkihu3LnBMuHuZLqZR/view) if needed.

### Quick Install
1. Download the latest `.hex` file from [releases](https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x/releases)
2. Flash the firmware using the instructions below

### Build From Source
1. Install [Arduino IDE](https://www.arduino.cc/en/main/software)
2. Clone this repo: `git clone https://github.com/HackySoftOfficial/Marlin-A4MaxPro-2.0.x.git`
3. Open `Marlin.ino` in Arduino IDE
4. Configure settings in `Configuration.h` and `Configuration_adv.h` if needed
5. Select `Genuino Mega 2560` and `ATmega2560` under Tools > Board
6. Choose Sketch > Export Compiled Binary
7. Use the generated `Marlin.ino.hex` file (not the bootloader version)

### BLTouch Setup
1. Copy config files from `/config/examples/Anycubic4MaxPro/A4MaxProBLTouch/` to `/Marlin/`
2. Update `NOZZLE_TO_PROBE_OFFSET` values to match your BLTouch mount position

### Post-Installation
1. Connect printer via USB ([CP210x drivers here](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers))
2. Open terminal program (OctoPrint/Pronterface/etc) at 115200 baud
3. Send commands:
   - `M502` (Reset to defaults)
   - `M500` (Save settings)
4. Restart printer

## Calibration Guide

**Critical calibration steps for optimal printing:**

### Required Steps
- Check hotend thermistor is secure and fully inserted
- [Calibrate extruder PIDs](https://github.com/davidramiro/Marlin-Ai3M/wiki/Calibration#pid-tuning)
- [Calibrate extruder steps](https://github.com/davidramiro/Marlin-Ai3M/wiki/Calibration#extruder-steps)

### Recommended Steps  
- [Set up manual mesh bed leveling](https://github.com/davidramiro/Marlin-Ai3M#manual-mesh-bed-leveling)
- Consider upgrading to a [better fan duct](https://www.thingiverse.com/thing:3772311)
- Review the [FAQ](https://github.com/davidramiro/Marlin-AI3M/wiki/Frequently-Asked-Questions)

## Key Features

### Linear Advance
- Improves print quality at corners and edges
- Calibrate using the [K-factor tool](https://marlinfw.org/tools/lin_advance/k-factor.html)
- Set per-material K values with `M900` command or through Cura plugin

### Filament Runout Detection
- Automatically pauses print when filament runs out
- Guides you through filament change process
- Resume printing after loading new filament

### Smart Pause
- Moves printhead to safe position when paused
- Maintains temperature during pause
- Precise position recovery when resuming

### Mesh Bed Leveling
1. Insert SD card
2. Go to Extra Menu > Start Mesh Leveling
3. Adjust height at each point using paper test
4. Save with "Save EEPROM" when complete
5. Add mesh leveling to start G-code

## Credits

### Core Team
- Jonas Plamann ([@Poket-Jony](https://github.com/Poket-Jony))
- Ruslan Kolosovskyi ([@rkolosovskyi](https://github.com/rkolosovskyi))
- Bernhard Berger ([@bernhardberger](https://github.com/bernhardberger))
- [@mpk](https://drucktipps3d.de/forum/profile/mpk)
- [@m-kozlowski](https://github.com/m-kozlowski)
- [@whitecube](https://drucktipps3d.de/forum/profile/whitecube)

### Marlin Contributors
- Scott Lahteine ([@thinkyhead](https://github.com/thinkyhead))
- Roxanne Neufeld ([@Roxy-3D](https://github.com/Roxy-3D))
- Chris Pepper ([@p3p](https://github.com/p3p))
- Bob Kuhn ([@Bob-the-Kuhn](https://github.com/Bob-the-Kuhn))
- And many more...

## License

This firmware is released under the [GPL v3 License](https://github.com/MarlinFirmware/Marlin/blob/1.0.x/COPYING.md). You must:
- Keep the source code open
- Provide your modified source code upon request
- Maintain all copyright notices

The simplest way to comply is to fork this repo on Github and link to your modified version.

## Disclaimer
