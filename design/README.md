# System Design

This directory documents the system architecture, electrical connections, and key subsystem configuration used in the final prototype.

The documentation is split into three areas:

- [`diagrams/`](diagrams/) — system-level architecture diagrams and editable sources
- [`config/`](config/) — subsystem behavior, firmware configuration, calibration values, and implementation notes
- [`wiring/`](wiring/) — physical connections between the ESP32 boards, sensors, actuators, display, and controls

## System Architecture

The system-level architecture diagram documents the dual-ESP32 structure, ESP-NOW communication, Control ESP32 inputs and outputs, safe-state behavior, and the hot/cold water path through the sensing, valve, mixing, and outlet stages.

- [`system_architecture.svg`](diagrams/system_architecture.svg) — rendered architecture diagram
- [`system_architecture.drawio`](diagrams/system_architecture.drawio) — editable draw.io source

## Configuration

| Subsystem              | Documentation                                          |
| :--------------------- | :----------------------------------------------------- |
| PI temperature control | [`config/pid.md`](config/pid.md)                       |
| Temperature sensors    | [`config/temp_sensor.md`](config/temp_sensor.md)       |
| Servo-driven valves    | [`config/servo_motor.md`](config/servo_motor.md)       |
| Flow sensing           | [`config/flow_sensor.md`](config/flow_sensor.md)       |
| ESP-NOW communication  | [`config/esp_now.md`](config/esp_now.md)               |
| Temperature setpoint   | [`config/setpoint.md`](config/setpoint.md)             |
| OLED display           | [`config/oled_display.md`](config/oled_display.md)     |
| Push buttons           | [`config/push_button.md`](config/push_button.md)       |
| Emergency stop         | [`config/emergency_stop.md`](config/emergency_stop.md) |

## Wiring

| Subsystem           | Documentation                                          |
| :------------------ | :----------------------------------------------------- |
| Temperature sensors | [`wiring/temp_sensor.md`](wiring/temp_sensor.md)       |
| Servo motors        | [`wiring/servo_motor.md`](wiring/servo_motor.md)       |
| Flow sensor         | [`wiring/flow_sensor.md`](wiring/flow_sensor.md)       |
| OLED display        | [`wiring/oled_display.md`](wiring/oled_display.md)     |
| Push buttons        | [`wiring/push_button.md`](wiring/push_button.md)       |
| Emergency stop      | [`wiring/emergency_stop.md`](wiring/emergency_stop.md) |

Firmware configuration remains the source of truth for deployed constants and pin assignments:

- [`firmware/common/config.h`](../firmware/common/config.h)
- [`firmware/control/config.h`](../firmware/control/config.h)
- [`firmware/ui/config.h`](../firmware/ui/config.h)
