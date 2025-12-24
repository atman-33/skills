---
name: terminal
description: Best practices for executing terminal commands, prioritizing the `execute_command` tool from the `terminal-runner` MCP server. Use when output is missing, truncated, or not returned (common in WSL), and fall back to capturing stdout/stderr by writing to `.tmp/copilot/` for inspection.
---

# Terminal Skill

When executing terminal commands, prioritize structured execution via MCP. If output still cannot be retrieved (common in WSL), use file-based capture under `.tmp/copilot/`.

## Workflow: Execute Command (Preferred)

1. Use the `execute_command` tool from the `terminal-runner` MCP server.
2. If `terminal-runner` is unavailable, run the command by typing it into the terminal (e.g., via `runInTerminal`).
3. If output cannot be retrieved, follow the workflow in "Capture Output to Files".

## Workflow: Capture Output to Files

1. Choose an output file path under `.tmp/copilot/` (create directories as needed).
2. Re-run the command with explicit redirection so both stdout and stderr are captured.
3. Inspect the saved output file to debug and continue.

### Patterns

- **Capture stdout + stderr**: `some-command > .tmp/copilot/output.txt 2>&1`
- **Capture + view live**: `some-command 2>&1 | tee .tmp/copilot/output.txt`
- **Capture exit code**: `some-command > .tmp/copilot/output.txt 2>&1; echo $? > .tmp/copilot/exit-code.txt`

### Notes

- Prefer text files with a short, descriptive name (e.g., `.tmp/copilot/rg-results.txt`).
- If the command produces multiple outputs, capture each to separate files to keep debugging fast.
