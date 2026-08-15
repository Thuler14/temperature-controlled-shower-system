# Temperature Setpoint

The UI allows the user to select the target outlet temperature sent to the Control ESP32. Setpoint configuration is shared between both boards.

## Configuration

| Parameter                   |  Value   |
| :-------------------------- | :------: |
| Default setpoint            | `100 °F` |
| Minimum selectable setpoint | `80 °F`  |
| Maximum selectable setpoint | `120 °F` |
| Default adjustment step     |  `1 °F`  |
| Preset A                    | `98 °F`  |
| Preset B                    | `105 °F` |

## Implementation Notes

User adjustments are constrained to the configured 80–120°F setpoint range before being transmitted to the Control unit.

Preset A and Preset B are selected with long presses on the corresponding UI buttons.

These values define the **allowed command range**. They should not be interpreted as independent measured-temperature safety cutoffs.

## Related Files

- [`firmware/common/config.h`](../../firmware/common/config.h) — shared setpoint values
- [`firmware/ui/ui.ino`](../../firmware/ui/ui.ino) — setpoint editing and presets
- [`firmware/control/control.ino`](../../firmware/control/control.ino) — received setpoint handling
