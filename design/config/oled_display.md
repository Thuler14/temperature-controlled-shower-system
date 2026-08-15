# OLED Display

The UI uses a 128×64 SSD1309 OLED over hardware SPI. The display provides the user-facing state of the controller without requiring a serial connection.

## Configuration

| Signal            | ESP32 GPIO |
| :---------------- | :--------: |
| Chip Select (CS)  |    `5`     |
| Data/Command (DC) |    `22`    |
| Reset (RST)       |    `4`     |

The display is driven with U8g2 using the full-framebuffer SSD1309 hardware-SPI configuration.

## Implementation Notes

Depending on the current UI state, the main display value shows:

- measured outlet temperature;
- the setpoint while it is being adjusted;
- outlet flow when the flow overlay is active.

The screen also shows run/stop state, adjustment step size, transmission count/status, and a pending indicator while a command is waiting to be sent or acknowledged.

## Related Files

- [`firmware/ui/config.h`](../../firmware/ui/config.h) — display pin configuration
- [`firmware/ui/display.cpp`](../../firmware/ui/display.cpp) — OLED rendering
- [`firmware/ui/ui.ino`](../../firmware/ui/ui.ino) — UI state and display updates
