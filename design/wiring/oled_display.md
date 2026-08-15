# OLED Display Wiring

The UI ESP32 drives a 128×64 SSD1309 OLED using hardware SPI.

## Connections

| OLED Pin | Signal       | Connection |
| :------- | :----------- | :--------- |
| 1        | GND          | GND        |
| 2        | VCC          | 3.3 V      |
| 3        | SCK          | GPIO 18    |
| 4        | MOSI         | GPIO 23    |
| 5        | Reset        | GPIO 4     |
| 6        | Data/Command | GPIO 22    |
| 7        | Chip Select  | GPIO 5     |

## Wiring Notes

The OLED uses the ESP32 hardware SPI bus, with separate chip-select, data/command, and reset signals.

## Related Files

- [`design/config/oled_display.md`](../config/oled_display.md) — display configuration and behavior

## Evidence

![OLED display wiring](../../mechanical/photos/m1_oled_display_wiring.jpg)
