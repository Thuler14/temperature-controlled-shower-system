# Servo Motor Wiring

Two MG996R servos actuate the hot and cold water valves from the Control ESP32.

The servos use a separate 6 V power supply while their control signals come from the ESP32.

## Connections

| Servo      | Signal | Connection |
| :--------- | :----- | :--------- |
| Cold valve | PWM    | GPIO 18    |
| Hot valve  | PWM    | GPIO 19    |
| Both       | Power  | 6 V supply |
| Both       | Ground | Supply GND |

The servo-supply ground is connected to ESP32 ground so the PWM signals share a common electrical reference.

## Wiring Notes

The prototype used a shared 6 V servo supply rated for at least 3 A.

Each servo was calibrated separately because the mechanical open and closed positions differ between the two valve assemblies.

## Related Files

- [`design/config/servo_motor.md`](../config/servo_motor.md) — servo calibration and valve-mixing behavior

## Evidence

![Servo motor wiring](../../mechanical/photos/m1_servo_motor_wiring.jpg)
