# Servo-Driven Valves

Two MG996R servos actuate the hot and cold valves. Each valve was individually calibrated to determine the pulse widths corresponding to its mechanical open and closed positions.

## Configuration

| Parameter    | Hot Valve | Cold Valve |
| :----------- | :-------: | :--------: |
| ESP32 GPIO   |   `19`    |    `18`    |
| Fully open   | `1180 µs` | `1120 µs`  |
| Fully closed | `2080 µs` | `2080 µs`  |

Normal mixing commands use a `15 µs` guard band inside the calibrated endpoints.

## Implementation Notes

A mix ratio from `0.0` to `1.0` is mapped to complementary hot/cold valve positions:

- `0.0` → cold open, hot closed;
- `1.0` → hot open, cold closed.

During normal mixing, the guard band keeps commanded positions slightly away from the mechanical endpoints.

When the controller enters its safe state, both valves are commanded directly to their calibrated closed positions.

Calibration was performed with [`m1_servo_calibration.ino`](../../firmware/tools/m1_servo_calibration/m1_servo_calibration.ino).

## Related Files

- [`firmware/control/config.h`](../../firmware/control/config.h) — calibrated pulse widths
- [`firmware/control/valve_mix.cpp`](../../firmware/control/valve_mix.cpp) — mix-ratio mapping and valve commands
