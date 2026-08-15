# Temperature Sensors

Three DS18B20 sensors measure the hot inlet, cold inlet, and mixed outlet temperatures on a shared OneWire bus.

Each sensor is bound to its physical location using its unique ROM address.

## Configuration

| Parameter                 |  Value   |
| :------------------------ | :------: |
| OneWire GPIO              |   `4`    |
| Sensor resolution         | `9 bit`  |
| Maximum conversion time   | `94 ms`  |
| Temperature update period | `100 ms` |
| EMA smoothing factor      |  `0.20`  |

### Sensor Addresses

| Location     | ROM Address               |
| :----------- | :------------------------ |
| Hot inlet    | `28 9D E1 BA 00 00 00 78` |
| Cold inlet   | `28 84 B3 B4 00 00 00 B6` |
| Mixed outlet | `28 4D F1 BA 00 00 00 C0` |

The addresses were identified with [`m1_temp_scan.ino`](../../firmware/tools/m1_temp_scan/m1_temp_scan.ino).

## Implementation Notes

The sensors run at 9-bit resolution so a complete conversion fits within the nominal 100 ms acquisition interval.

An exponential moving average with `α = 0.20` smooths temperature measurements before they are used by the control loop.

The Control firmware also performs validity, plausible-range, and rapid-change checks before allowing temperature data to drive the valves.

## Related Files

- [`firmware/control/config.h`](../../firmware/control/config.h) — addresses, timing, filtering, and plausibility limits
- [`firmware/control/temperature.cpp`](../../firmware/control/temperature.cpp) — temperature acquisition and filtering
- [`firmware/control/control.ino`](../../firmware/control/control.ino) — control and sensor-fault handling
- [`validation/measurement/data/m2_outlet_temp_test_data.csv`](../../validation/measurement/data/m2_outlet_temp_test_data.csv) — recorded outlet-temperature test data
