# Push Buttons

Five active-low pushbuttons provide local control of the UI. Internal ESP32 pull-ups are used, so a pressed button reads `LOW`.

## Configuration

| Button | Function          | GPIO |
| :----- | :---------------- | :--: |
| ▲      | Increase setpoint | `25` |
| ▼      | Decrease setpoint | `26` |
| ●      | Run/stop control  | `27` |
| A      | Preset A          | `14` |
| B      | Preset B          | `13` |

### Gesture Timing

| Parameter           |  Value   |
| :------------------ | :------: |
| Debounce            | `25 ms`  |
| Double-click window | `350 ms` |
| Long press          | `800 ms` |
| Repeat delay        | `500 ms` |
| Repeat interval     | `150 ms` |

## Implementation Notes

Up and down adjust the setpoint and support repeat events while held.

The final UI uses long presses for the higher-impact actions:

- long-press **A** selects Preset A;
- long-press **B** selects Preset B;
- long-press **●** toggles run/stop.

This reduces the chance of accidentally changing operating state while using the interface.

## Related Files

- [`firmware/ui/config.h`](../../firmware/ui/config.h) — pin and timing configuration
- [`firmware/ui/buttons.cpp`](../../firmware/ui/buttons.cpp) — debounce and gesture detection
- [`firmware/ui/ui.ino`](../../firmware/ui/ui.ino) — button-to-action mapping
