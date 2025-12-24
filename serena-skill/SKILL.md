---
name: serena-skill
description: Guidelines for activating and using Serena MCP projects reliably. Use when Codex needs to work with Serena tools (semantic search, refactors, code navigation), especially when starting work in a new directory. Includes WSL-specific activation guidance using UNC paths (\\wsl$\\Ubuntu...) with a Linux-path fallback.
---

# Serena Skill

## Overview

Activate Serena projects consistently and apply a predictable Serena-first workflow for code understanding and editing.

## Project Activation

- Upon project initialization, activate the current directory as a Serena project before performing any operations.
- After activation, call `check_onboarding_performed`; if onboarding is not performed, run `onboarding` before continuing.

## WSL Environment

- When working in WSL (paths starting with `/home/...`), ALWAYS attempt to activate the project using the UNC path format first: `\\wsl$\Ubuntu<absolute_path>` (e.g., `\\wsl$\Ubuntu\home\user\repo`).
- Only use the standard Linux path if the UNC path activation fails.

## Serena-First Workflow

- Prefer Serena MCP tools for semantic code search, project analysis, and automated refactoring.
- Use shell commands mainly for non-code files and lightweight reads where semantics are not needed.
