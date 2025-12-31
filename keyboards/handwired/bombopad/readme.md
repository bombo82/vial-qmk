# BomboPad Vial Firmware

BomboPad is an open-source, versatile 12-key macropad featuring dual rotary encoders and display support. Designed with
a focus on flexibility, it supports both wired and wireless configurations.

This directory contains the **Vial firmware** implementation for the BomboPad, designed for wired use with controllers
like the Pro Micro. This version allows you to configure your keymap, encoders, and settings in real-time using the
**Vial UI**.

## Key Features (v0.3)

- **12 keys**: Matrix layout 3x4.
- **Dual Rotary Encoders**: Supports EC11 or EVQWGD001 encoders.
- **Real-time Configuration**: No need to re-flash the firmware to change your keymap.
- **8 Dynamic Layers**: Fully programmable via Vial UI.
- **Display Support**: SSD1306 128x32 OLED showing current layer and status.
- **Microcontroller**: Pro Micro (ATmega32U4) or compatible.

## Hardware Availability

For hardware design files, electrical schematics, and PCB layouts, please refer to the
**[main BomboPad repository](https://github.com/bombo82/bombopad)**.

## Build Instructions

To build the Vial firmware, ensure you have the `vial-qmk` environment set up.

### Compiling

To compile the Vial keymap for version 0.3:

```bash
qmk compile -kb handwired/bombopad/v0_3 -km vial
```

### Flashing

To flash the firmware put the keyboard in bootloader mode (usually by resetting the Pro Micro) and run:

```bash
qmk flash -kb handwired/bombopad/v0_3 -km vial
```

### Pro Micro RP2040 Support

If you are using a **Pro Micro RP2040** module (such as the Waveshare RP2040-Plus or SparkFun Pro Micro RP2040), you can
leverage QMK's **Converters**. This allows you to use the existing keyboard configuration without any modifications.

To compile for the RP2040:

```bash
qmk compile -kb handwired/bombopad/v0_3 -km vial -e CONVERT_TO=rp2040_ce
```

*(Note: `promicro_rp2040` is now deprecated in favour of `rp2040_ce` or `sparkfun_pm2040`).*

#### Important Notes for RP2040:

- **Pin Compatibility**: The `keyboard.json` file includes `"pin_compatible": "promicro"`, which enables the use of
  converters.
- **Pin Mapping**: QMK automatically maps the original AVR pins (e.g. `B1`, `F4`) to the corresponding GPIO pins on the
  RP2040.
- **Bootloader**: To enter bootloader mode on the RP2040, you usually need to hold the **BOOT** button while connecting
  the USB cable or pressing the **RESET** button on the module.
- **Architecture**: The build system will automatically switch to the ARM/ChibiOS stack required for the RP2040.


## Using Vial

Once flashed, you can configure your BomboPad using the Vial application:

1. **Download Vial**: Get the desktop app from [get.vial.today](https://get.vial.today/) or use
   the [Web Version](https://vial.rocks/).
2. **Sideload JSON**: Until the BomboPad is officially included in the Vial database, you might need to load the
   `vial.json` file manually:
    - Open Vial.
    - Go to `File` -> `Load sideload JSON`.
    - Select the `vial.json` file located in `keyboards/handwired/bombopad/keymaps/vial/`.
3. **Configure**: Now you can change key assignments and encoder behaviors in real-time.

## Help & Contributions

Bug reports, suggestions, and contributions are welcome! Please
use [GitHub Issues](https://github.com/bombo82/bombopad/issues)
and [Discussions](https://github.com/bombo82/bombopad/discussions) for any feedback.

## Authors

- **Gianni Bombelli (bombo82)** - [GitHub Profile](https://github.com/bombo82)

## Licenses

Documentation are licensed under GNU Free Documentation License as published by the Free Software Foundation, either
version 1.3 of the License, or (at your option) any later version.

Source code are licensed under GNU General Public License as published by the Free Software Foundation, either version 3
of the License, or (at your option) any later version.

Hardware design and all related things are licensed under CERN Open Hardware Licence as published by the CERN, either
version 2 of the Licence, or (at your option) any later version.

## License Disclaimer

Copyright (C) 2024-2025 Gianni Bombelli <bombo82@giannibombelli.it>

Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.3
or any later version published by the Free Software Foundation;
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.

You should have received a copy of the GNU Free Documentation License
along with this program. If not, see <https://www.gnu.org/licenses/fdl-1.3.html>.

## Acknowledgements

Special thanks to [Arialdo](https://github.com/arialdomartini) for introducing me to the world of custom mechanical
keyboards.
