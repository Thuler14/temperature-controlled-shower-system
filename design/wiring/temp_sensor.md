# Temperature Sensor Wiring

Three DS18B20 sensors measure the hot inlet, cold inlet, and mixed outlet temperatures. All three sensors share one OneWire bus on the Control ESP32.

## Connections

| Wire   | Signal    | Connection |
| :----- | :-------- | :--------- |
| Yellow | Data (DQ) | GPIO 4     |
| Red    | Power     | 3.3 V      |
| Blue   | Ground    | GND        |

A `4.7 kΩ` pull-up resistor connects the shared data line to `3.3 V`.

## Wiring Notes

All three sensors share the same data line and are distinguished in firmware by their unique ROM addresses.

## Related Files

- [`design/config/temp_sensor.md`](../config/temp_sensor.md) — sensor addressing, sampling, and filtering

## Evidence

![Temperature sensor wiring](../../mechanical/photos/m1_temp_sensor_wiring.jpg)
