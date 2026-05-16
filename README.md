# Xiao nRF52840 4x5 ZMK Config

This is a minimal ZMK config for a custom macropad using a Seeed Studio XIAO nRF52840.

## Hardware Assumptions

The schematic image appears to use this matrix:

| Net | XIAO Pin | ZMK GPIO |
| --- | --- | --- |
| ROW0 | D0 | `&xiao_d 0` |
| ROW1 | D1 | `&xiao_d 1` |
| ROW2 | D2 | `&xiao_d 2` |
| ROW3 | D3 | `&xiao_d 3` |
| ROW4 | D4 | `&xiao_d 4` |
| COL0 | D5 | `&xiao_d 5` |
| COL1 | D10 | `&xiao_d 10` |
| COL2 | D9 | `&xiao_d 9` |
| COL3 | D8 | `&xiao_d 8` |
| Encoder A | D6 | `&xiao_d 6` |
| Encoder B | D7 | `&xiao_d 7` |

The matrix is written as 5 rows x 4 columns in ZMK. The bottom-right encoder push switch is part of the matrix at ROW4/COL3.

## Build Target

```yaml
include:
  - board: xiao_ble//zmk
    shield: xiao_macropad_4x5
```

Recent ZMK documentation lists Seeed Studio XIAO nRF52840 as `xiao_ble//zmk`, so this config uses that board name in `build.yaml`.

GitHub Actions builds are handled by `.github/workflows/build.yml`, using ZMK's reusable user config workflow.

## Files To Edit First

- Key layout: `boards/shields/xiao_macropad_4x5/xiao_macropad_4x5.keymap`
- Matrix pins: `boards/shields/xiao_macropad_4x5/xiao_macropad_4x5.overlay`
- Device name and defaults: `boards/shields/xiao_macropad_4x5/Kconfig.defconfig`

## First Test

1. Build the firmware.
2. Flash the generated UF2 to the XIAO nRF52840.
3. Pair over Bluetooth as `Xiao Pad 4x5`.
4. Test each key. The diagnostic layout sends `A` through `T`.
5. Test encoder rotation. It is mapped to volume up/down by default.
