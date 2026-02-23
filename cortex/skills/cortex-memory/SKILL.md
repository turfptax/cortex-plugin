---
name: cortex-memory
description: Use this skill when the user mentions "memory", "remember", "log this", "save a note", "session", "what was I working on", "cortex", or asks to persist information across conversations. Also use at the START of conversations to load context, and at the END to log a session summary.
version: 1.0.0
---

# Cortex Memory Skill

You are connected to the **Cortex wearable AI memory system** via MCP. This gives you persistent memory across conversations through a physical device the user wears.

## Architecture

```
You (Claude) --MCP--> cortex-mcp --daemon--> ESP32 USB dongle --BLE--> Pi Zero 2 W (SQLite DB)
```

## Available Tools

| Tool | When to Use |
|------|-------------|
| `ping` | Test connectivity before other operations |
| `get_context` | **Start of conversation** — load recent sessions, projects, notes, bugs, reminders |
| `get_status` | Check Pi uptime, storage, BLE connection |
| `send_note` | Store any information the user wants remembered (supports tags, project, type) |
| `log_activity` | Log what program/file the user is working on |
| `log_search` | Log web searches for research history |
| `session_start` | Begin tracking a session (returns session_id) |
| `session_end` | End session with a summary of what was accomplished |
| `query` | Search the database (tables: notes, activities, searches, sessions, projects, computers, people) |
| `register_computer` | Register this machine with Cortex |

## Note Types

When using `send_note`, choose the appropriate type:
- **note** — General information
- **decision** — Architectural or design decisions made
- **bug** — Known bugs or issues
- **reminder** — Things to follow up on later
- **idea** — Ideas for future exploration
- **todo** — Tasks to complete
- **context** — Background context for future sessions

## Session Management

- Call `session_start` early in conversations where real work is being done
- Call `session_end` with a concise summary before the conversation ends
- The `projects` field in `session_end` should list project tags that were touched (comma-separated)

## Best Practices

1. **Start of conversation**: Call `get_context` to understand what the user has been working on recently
2. **During work**: Log important decisions as `decision` notes, bugs as `bug` notes
3. **End of conversation**: If meaningful work was done, log a session summary with `session_end`
4. **Be selective**: Don't log every trivial interaction — focus on information that would be valuable in future sessions
5. **Use project tags**: Always tag notes and sessions with relevant project names for easy filtering later
