# Push Button Wiring

Five momentary pushbuttons provide local input to the UI ESP32. Each button is wired as an active-low input using the ESP32's internal pull-up.

## Connections

| Button | Connection |
| :----: | :--------: |
|   ▲    |  GPIO 25   |
|   ▼    |  GPIO 26   |
|   ●    |  GPIO 27   |
|   A    |  GPIO 14   |
|   B    |  GPIO 13   |

The second terminal of each button connects to GND.

## Wiring Notes

A released button reads `HIGH`. Pressing the button connects its GPIO to ground and produces a `LOW` input.

## Related Files

- [`design/config/push_button.md`](../config/push_button.md) — button timing, gestures, and UI actions

## Evidence

![Push button wiring](../../mechanical/photos/m1_push_button_wiring.jpg)
