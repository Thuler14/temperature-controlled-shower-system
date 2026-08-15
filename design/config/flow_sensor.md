# Flow Sensor

A YF-S201 Hall-effect flow sensor measures outlet-flow pulses on the Control ESP32. The firmware counts pulses using a hardware interrupt and converts the measured pulse frequency into an estimated flow rate.

## Configuration

| Parameter                 |        Value        |
| :------------------------ | :-----------------: |
| Signal GPIO               |        `21`         |
| Measurement window        |      `500 ms`       |
| Flow filter time constant |      `1000 ms`      |
| Conversion factor         | `7.5` (placeholder) |

## Implementation Notes

Pulse counts are captured on rising edges and evaluated over a 500 ms measurement window. Raw pulse frequency and estimated flow are then smoothed using an exponential filter.

The conversion factor in the current firmware was **not experimentally calibrated against a known flow reference**. The resulting flow values are useful for demonstrating the sensing and logging pipeline but should not be treated as validated flow-accuracy measurements.

## Related Files

- [`firmware/control/config.h`](../../firmware/control/config.h) — flow configuration
- [`firmware/control/flow_sensor.cpp`](../../firmware/control/flow_sensor.cpp) — interrupt counting, conversion, and filtering
- [`tests/data/m2_flow_sensor_test_data.csv`](../../tests/data/m2_flow_sensor_test_data.csv) — recorded flow-sensor test data
