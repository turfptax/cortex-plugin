---
description: Log a session summary to Cortex memory
argument-hint: [summary]
allowed-tools: [mcp__cortex__session_start, mcp__cortex__session_end, mcp__cortex__send_note]
---

# Log Session to Cortex

The user wants to log a session summary to their Cortex wearable memory device.

## Arguments

The user provided: $ARGUMENTS

## Instructions

1. If arguments were provided, use them as the session summary
2. If no arguments, review the conversation history and write a concise 1-3 sentence summary of what was accomplished
3. Call `session_start` to begin a session record
4. Call `send_note` with the summary as a `context` type note, tagged with any relevant project names
5. Call `session_end` with the session_id from step 3, the summary, and comma-separated project tags
6. Confirm to the user that the session was logged, showing:
   - Session ID
   - Summary that was recorded
   - Projects tagged
