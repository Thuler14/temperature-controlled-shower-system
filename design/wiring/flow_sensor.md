# Flow Sensor Wiring

The YF-S201 flow sensor is installed on the mixed-water outlet and connected to the Control ESP32.

## Connections

| Wire   | Signal       | Connection |
| :----- | :----------- | :--------- |
| Yellow | Pulse output | GPIO 21    |
| Red    | Sensor power | 5 V        |
| Black  | Ground       | GND        |

A `10 kΩ` pull-up resistor connects the pulse signal on GPIO 21 to `3.3 V`.

## Wiring Notes

The pulse output provides the signal used by the Control ESP32 to measure outlet flow.

## Related Files

- [`design/config/flow_sensor.md`](../config/flow_sensor.md) — flow measurement and filtering configuration

## Evidence

![Flow sensor wiring](../../mechanical/photos/m2_flow_sensor_wiring.jpg)
