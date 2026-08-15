# Emergency Stop Wiring

The E-stop switch is connected to the Control ESP32 as an active-low input.

## Connections

| Signal                | Connection |
| :-------------------- | :--------- |
| E-stop input          | GPIO 33    |
| Other switch terminal | GND        |

GPIO 33 uses the ESP32's internal pull-up, so activating the switch pulls the input low.

## Wiring Notes

The switch provides the physical input used by the firmware's E-stop handling.

## Related Files

- [`design/config/emergency_stop.md`](../config/emergency_stop.md) — E-stop behavior and configuration
