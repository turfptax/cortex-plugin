---
description: Check Cortex wearable device connectivity and status
allowed-tools: [mcp__cortex__ping, mcp__cortex__get_status, mcp__cortex__connection_info]
---

# Cortex Status Check

The user wants to check the status of their Cortex wearable AI memory device.

## Instructions

1. First call `connection_info` to check the serial port and ESP32 connection
2. Then call `ping` to test BLE round-trip to the Pi Zero
3. If ping succeeds, call `get_status` to get full device status (uptime, storage, recording state)
4. Present results in a concise summary:
   - Serial connection: connected/disconnected, which port
   - BLE link: connected/disconnected (ping result)
   - Pi status: uptime, free storage, active session count, total notes/activities
5. If anything is disconnected, suggest troubleshooting steps:
   - Serial: "Is the ESP32 USB dongle plugged in?"
   - BLE: "Try rebooting the ESP32 or Pi Zero"
