# Cortex Plugin for Claude Code

Connects Claude Code to the **Cortex wearable AI memory system** — a physical device that gives AI persistent memory across conversations.

## What You Get

- **13 MCP tools** for storing notes, logging activities, tracking sessions, and querying your memory database
- **`/cortex-status`** — Quick connectivity and device status check
- **`/cortex-log`** — Log a session summary to your wearable memory
- **Cortex Memory skill** — Claude automatically uses your memory for context at the start of conversations and logs important work at the end

## Prerequisites

1. **Hardware**: Cortex Link (ESP32-S3 USB dongle) plugged into your computer, paired with a Cortex Core (Pi Zero 2 W) via BLE

2. **Python package**: Install the MCP server:
   ```bash
   pip install git+https://github.com/turfptax/cortex.git
   ```

3. **Verify**: Test connectivity before installing the plugin:
   ```bash
   cortex-cli ping
   ```

## MCP Tools

| Tool | Description |
|------|-------------|
| `ping` | Test BLE round-trip connectivity |
| `get_status` | Pi uptime, storage, recording state |
| `send_note` | Store a note (with tags, project, type) |
| `log_activity` | Log what program/file you're working on |
| `log_search` | Log a search query |
| `session_start` | Begin a session |
| `session_end` | End session with summary |
| `get_context` | Load full context (projects, sessions, notes, bugs) |
| `query` | Query any table in the Cortex database |
| `register_computer` | Register this machine |
| `send_message` | Send raw protocol message |
| `read_responses` | Read buffered messages |
| `connection_info` | Serial port status |

## Related Repos

- [cortex](https://github.com/turfptax/cortex) — MCP server, CLI, and daemon
- [cortex-core](https://github.com/turfptax/cortex-core) — Pi Zero wearable code
- [esp32-keymaster](https://github.com/turfptax/esp32-keymaster) — ESP32-S3 USB-BLE bridge firmware
