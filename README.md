# Cortex Plugin Marketplace

A Claude Code plugin marketplace for the [Cortex wearable AI memory system](https://github.com/turfptax/cortex).

## Installation

### 1. Install the MCP server

```bash
pip install git+https://github.com/turfptax/cortex.git
```

### 2. Verify connectivity (ESP32 must be plugged in)

```bash
python -m cortex_mcp ping
```

### 3. Add this marketplace to Claude Code

```
/plugin marketplace add turfptax/cortex-plugin
```

### 4. Install the plugin

```
/plugin install cortex@cortex-plugin
```

### 5. Restart Claude Code

The Cortex MCP tools, slash commands, and memory skill will be available in all sessions.

## Also want it on Claude Desktop?

After the pip install, run:

```bash
python -m cortex_mcp setup --target claude-desktop
```

Then restart Claude Desktop. Both Claude Code and Claude Desktop can connect simultaneously through the daemon.

## What's Included

### Plugin: `cortex`

- **MCP Server**: 13 tools for interacting with your Cortex wearable (notes, sessions, activities, queries)
- **Skill**: `cortex-memory` — Claude automatically loads context at conversation start and logs sessions
- **Commands**:
  - `/cortex-status` — Check device connectivity and status
  - `/cortex-log` — Log a session summary to your wearable memory

## Hardware Required

- **Cortex Link**: ESP32-S3 USB dongle (BLE bridge) — [firmware](https://github.com/turfptax/esp32-keymaster)
- **Cortex Core**: Pi Zero 2 W with SQLite database — [software](https://github.com/turfptax/cortex-core)

## License

MIT
