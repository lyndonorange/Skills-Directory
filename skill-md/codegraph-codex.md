---
name: codegraph
display_name: codegraph
platform: Codex
category: Software engineering and app building
---

# codegraph - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `codegraph` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use CodeGraph to build and query a local semantic index for a codebase. CodeGraph is installed globally as `codegraph` and configured as an MCP server for Codex and OpenCode.

## How To Use It In Codex

In Codex, click the chat box, press /, choose codegraph, then write the task. Fallback prompt: Use the codegraph skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `codegraph` |
| Canonical name | `codegraph` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Use CodeGraph to build and query a local semantic index for a codebase. CodeGraph is installed globally as `codegraph` and configured as an MCP server for Codex and OpenCode.

## Original SKILL.md

---
name: codegraph
description: Use CodeGraph for local semantic code intelligence, MCP-backed repo exploration, symbol search, call graphs, impact analysis, affected tests, and codebase indexing. Use when the user mentions codegraph, semantic code search, callers, callees, impact radius, affected files, or wants faster understanding of a repo before editing.
---

# CodeGraph

Use CodeGraph to build and query a local semantic index for a codebase. CodeGraph is installed globally as `codegraph` and configured as an MCP server for Codex and OpenCode.

## When To Use

- Before editing an unfamiliar or medium-to-large repo.
- When the user asks what calls a function, what a function calls, what might break, or which tests are affected.
- When normal grep/read exploration would be noisy or expensive.
- When working in Zed through Codex ACP or OpenCode after those agents have restarted.

## Setup Per Project

Run from the project root:

```bash
codegraph init -i
```

If the project is already initialized, refresh it with:

```bash
codegraph sync
codegraph status
```

The project index lives in `.codegraph/`. Do not commit it unless the project explicitly decides to.

## CLI Commands

- `codegraph status`: show index status and statistics.
- `codegraph query "<search>"`: search symbols and code text.
- `codegraph files`: show indexed project file structure.
- `codegraph callers <symbol>`: find callers of a symbol.
- `codegraph callees <symbol>`: find functions a symbol calls.
- `codegraph impact <symbol>`: analyze impact radius before changing a symbol.
- `codegraph affected <files...>`: identify likely affected test files.
- `codegraph serve --mcp`: MCP server command used by agents.

## Agent Workflow

1. Check `codegraph status` in the project root.
2. If not initialized, run `codegraph init -i`.
3. Use CodeGraph queries before broad file reads when the task is about structure, relationships, or impact.
4. After making code edits, rely on the MCP watcher when available; otherwise run `codegraph sync`.
5. For final verification, combine CodeGraph impact results with the repo's normal tests.

## Installed Locations

- CLI: `/opt/homebrew/bin/codegraph`
- Codex MCP config: `[local home]/.codex/config.toml`
- OpenCode MCP config: `[local home]/.config/opencode/opencode.json`
- Codex skill: `[local home]/.codex/skills/codegraph/SKILL.md`
- OpenCode skill: `[local home]/.config/opencode/skills/codegraph/SKILL.md`

