# Firmware

The embedded software is split between two ESP32 boards: a Control unit that performs sensing and closed-loop temperature control, and a UI unit that handles user input and system status.

## Structure

- [`control/`](control/) — temperature acquisition, PI control, valve actuation, flow sensing, communication, and safety handling
- [`ui/`](ui/) — push-button input, OLED display, presets, and ESP-NOW communication
- [`common/`](common/) — configuration and protocol definitions shared by both ESP32s
- [`libraries/`](libraries/) — local reusable firmware components
- [`tools/`](tools/) — hardware discovery and calibration utilities
- [`test_sketches/`](test_sketches/) — bring-up and subsystem test firmware used during development

The deployed application entry points are:

- [`control/control.ino`](control/control.ino)
- [`ui/ui.ino`](ui/ui.ino)
