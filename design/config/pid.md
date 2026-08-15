# PI Controller

The final system uses a PI feedback controller to regulate outlet temperature by adjusting the hot/cold valve mix ratio.

The controller is implemented with a generic PID class, but the deployed derivative gain is zero, so the final configuration operates as PI control.

## Configuration

| Parameter                |   Value   |
| :----------------------- | :-------: |
| Proportional gain (`Kp`) |  `0.025`  |
| Integral gain (`Ki`)     |  `0.005`  |
| Derivative gain (`Kd`)   |   `0.0`   |
| Output range             | `0.0–1.0` |
| Error deadband           | `0.2 °F`  |
| Normal output slew       | `0.8 /s`  |
| Fast output slew         | `3.0 /s`  |
| Fast-slew threshold      | `3.0 °F`  |

## Implementation Notes

Temperature measurements update at approximately 10 Hz. The controller calculates its timestep from consecutive outlet-temperature samples rather than assuming a fixed interval.

The implementation also includes:

- conditional integration to reduce windup during output saturation;
- integrator reset when the error crosses zero;
- a small deadband near the setpoint to reduce hunting;
- output slew limiting to avoid abrupt valve movements.

The main firmware loop runs more frequently, but the PI calculation only updates when a new outlet-temperature sample is available.

## Related Files

- [`firmware/control/config.h`](../../firmware/control/config.h) — deployed gains and limits
- [`firmware/control/pid.cpp`](../../firmware/control/pid.cpp) — PI/PID computation
- [`firmware/control/control.ino`](../../firmware/control/control.ino) — controller integration and slew limiting
