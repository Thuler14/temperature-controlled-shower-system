# ESP-NOW Communication

The UI and Control ESP32s communicate directly over ESP-NOW. The final system uses fixed peer MAC addresses and a fixed Wi-Fi channel for the one-to-one wireless link.

## Configuration

| Parameter        |        Value        |
| :--------------- | :-----------------: |
| Wi-Fi channel    |         `6`         |
| Control MAC      | `3C:8A:1F:80:A9:D4` |
| UI MAC           | `8C:4F:00:35:9B:F4` |
| Protocol version |         `1`         |
| Encryption       |      Disabled       |

MAC addresses were identified using [`m2_mac_scan.ino`](../../firmware/tools/m2_mac_scan/m2_mac_scan.ino).

## Implementation Notes

The UI sends the selected setpoint and run/stop state to the Control unit. Each packet includes a sequence number so the corresponding acknowledgment can be matched to the transmitted command.

The Control unit returns an acknowledgment containing the latest outlet-temperature and flow values when those measurements are valid.

The communication layer also supports ESP-NOW encryption, but encryption is disabled in the final configuration.

## Related Files

- [`firmware/common/config.h`](../../firmware/common/config.h) — shared protocol and peer configuration
- [`firmware/ui/communication.cpp`](../../firmware/ui/communication.cpp) — UI sender and acknowledgment handling
- [`firmware/control/communication.cpp`](../../firmware/control/communication.cpp) — command receiver and response handling
