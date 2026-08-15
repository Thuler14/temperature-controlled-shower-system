# Automatic Temperature-Controlled Shower

ESP32-based closed-loop system that automatically mixes hot and cold water to maintain a user-selected outlet temperature.

Developed as a three-person NJIT ECE 416 capstone project, the prototype combines embedded control, wireless communication, temperature and flow sensing, servo-actuated valves, and a standalone user interface.

## System Overview

The prototype is split across two ESP32s:

- **Control unit** — reads three DS18B20 temperature sensors and a YF-S201 flow sensor, runs the PI temperature controller, drives the hot/cold valve servos, and handles safety conditions.
- **UI unit** — provides a 128×64 OLED and five-button interface for setpoint adjustment, presets, run/stop control, and system status.
- **ESP-NOW link** — transfers setpoint and run-state commands between the UI and Control units and returns outlet-temperature and flow status.

The final controller uses PI feedback with EMA-filtered temperature measurements, anti-windup, a small setpoint deadband, and output slew limiting.

## Key Features

- Dual-ESP32 embedded architecture with ESP-NOW communication
- Three-point temperature sensing: hot inlet, cold inlet, and mixed outlet
- PI closed-loop outlet-temperature control
- Individually calibrated servo-driven hot and cold valves
- EMA temperature filtering and 10 Hz control updates
- Flow sensing and CSV data logging
- OLED interface with adjustable setpoint, presets, and run/stop control
- Link-loss and temperature-sensor fault handling
- Physical E-stop switch monitored by the Control ESP32

## Safety Behavior

The prototype includes several firmware-level protections:

- loss of the UI communication link while running stops normal operation;
- invalid or implausible temperature readings stop normal operation;
- rapid temperature changes on the hot or cold lines are detected as faults;
- activating the E-stop switch stops normal operation;
- fault handling commands both valves closed and resets the PI controller.

The selectable setpoint is limited to **80–120°F**. This is a user-command range, not an independent measured-temperature cutoff.

## Project Structure

```text
temperature-controlled-shower-system/
├── firmware/
│   ├── common/       # Shared ESP-NOW protocol and setpoint configuration
│   ├── control/      # Sensors, PI control, valves, flow sensing, safety logic
│   ├── ui/           # Buttons, OLED interface, and ESP-NOW communication
│   ├── examples/     # Milestone and subsystem test sketches
│   └── tools/        # Sensor discovery and servo calibration tools
├── design/
│   ├── config/       # Subsystem configuration and implementation notes
│   └── wiring/       # Physical wiring documentation
├── mechanical/
│   ├── cad/          # Servo mount and valve coupler CAD
│   └── photos/       # Assembly and wiring photos
└── tests/
    ├── data/         # Recorded CSV test data
    ├── scripts/      # Logging and analysis tools
    └── reports/      # Test plots and supporting evidence
```

See [`design/README.md`](design/README.md) for subsystem documentation and [`mechanical/README.md`](mechanical/README.md) for the mechanical design.

## Data Logging and Analysis

The Control unit can stream CSV telemetry over USB, including:

- outlet temperature;
- selected setpoint;
- commanded valve ratio;
- PI output;
- controller gains;
- estimated flow;
- communication-link status.

Python scripts under [`tests/scripts/`](tests/scripts/) support live logging and offline plotting. Recorded datasets and plots are preserved under [`tests/data/`](tests/data/) and [`tests/reports/`](tests/reports/).

## Firmware

The main firmware entry points are:

- [`firmware/control/control.ino`](firmware/control/control.ino) — Control ESP32
- [`firmware/ui/ui.ino`](firmware/ui/ui.ino) — UI ESP32

Configuration is divided between:

- [`firmware/common/config.h`](firmware/common/config.h)
- [`firmware/control/config.h`](firmware/control/config.h)
- [`firmware/ui/config.h`](firmware/ui/config.h)

The project uses the Arduino ESP32 framework with OneWire, DallasTemperature, ESP32Servo, U8g2, and ESP-NOW.
