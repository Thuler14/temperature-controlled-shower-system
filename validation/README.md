# Validation

This directory contains test data and supporting evidence collected while bringing up the prototype, verifying subsystem behavior, and evaluating the temperature-control system.

## Areas

- [`bringup/`](bringup/) — early hardware and peripheral bring-up, including the ESP32, OLED, buttons, temperature sensing, and servo actuation
- [`communication/`](communication/) — ESP-NOW communication and setpoint transfer between the UI and Control ESP32s
- [`measurement/`](measurement/) — temperature and flow measurement tests, with recorded data, plots, and supporting scripts
- [`control/`](control/) — valve-mixing and closed-loop temperature-control tests, with recorded data, plots, scripts, and video evidence

The `measurement/` and `control/` directories keep related CSV data, generated plots, and analysis scripts together so that each test can be traced from the recorded measurements to its visualization.

Historical filenames such as `m1_*` and `m2_*` are retained where they identify the original development activity.
