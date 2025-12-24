---
name: openspec
description: Guidelines for using the openspec CLI tool via MCP, specifically for running validation commands in non-interactive mode. Use this skill when you need to validate changes or specs using openspec and want to avoid interactive prompts that cause failures in the MCP environment.
---

# OpenSpec Guidelines

The `openspec` CLI defaults to interactive mode for some commands, which causes failures in the MCP environment. Use the following non-interactive flags instead.

## Validation Commands

Avoid `openspec validate` (interactive). Use these specific targets instead:

- **Validate everything**: `openspec validate --all`
- **Validate changes only**: `openspec validate --changes`
- **Validate specs only**: `openspec validate --specs`
- **Validate specific item**: `openspec validate <item-name>`