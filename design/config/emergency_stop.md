# Emergency Stop

The final prototype uses a physical E-stop switch connected to the Control ESP32. The switch provides an active-low input that stops normal control operation and commands both valves closed.

## Configuration

| Parameter    |     Value      |
| :----------- | :------------: |
| E-stop input |    GPIO 33     |
| Input mode   | `INPUT_PULLUP` |
| Active state |     `LOW`      |

## Implementation Notes

When the E-stop input becomes active, the Control ESP32:

- disables the current run command;
- enters the controller's safe state;
- commands both valves closed;
- resets the PI controller.

The E-stop in the final prototype is handled through the Control ESP32 firmware rather than through an independent servo-power disconnect.

## Related Files

- [`firmware/control/config.h`](../../firmware/control/config.h) — E-stop GPIO configuration
- [`firmware/control/control.ino`](../../firmware/control/control.ino) — E-stop detection and safe-state handling
