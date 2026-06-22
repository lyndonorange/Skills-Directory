---
name: kw-zoom-plugin-setup-zoom-mcp
display_name: kw-zoom-plugin-setup-zoom-mcp
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-setup-zoom-mcp - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-setup-zoom-mcp` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-setup-zoom-mcp, then write the task. Fallback prompt: Use the kw-zoom-plugin-setup-zoom-mcp skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-setup-zoom-mcp` |
| Canonical name | `kw-zoom-plugin-setup-zoom-mcp` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: setup-zoom-mcp
name: kw-zoom-plugin-setup-zoom-mcp
description: Decide when Zoom MCP is the right fit and produce a safe setup plan for Claude. Use when planning AI workflows over Zoom data, deciding between MCP and REST, or defining a hybrid MCP architecture.
argument-hint: "<AI workflow or MCP use case>"
---

# /setup-zoom-mcp

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Plan a Zoom MCP workflow and decide when to use MCP alone versus a hybrid REST API + MCP architecture.

## Usage

```text
/setup-zoom-mcp $ARGUMENTS
```

## Workflow

1. Determine whether the goal is deterministic automation, AI tool orchestration, or a hybrid.
2. If MCP is appropriate, identify the likely Zoom MCP surface and transport assumptions.
3. If MCP alone is not enough, define the REST API responsibilities separately.
4. Call out auth, scope, and client capability constraints.
5. End with a minimal proof-of-concept sequence.

## Output

- Recommended MCP strategy
- Connector expectations
- Hybrid boundaries if REST is also required
- Risks and setup notes
- Relevant skill links

## Related Skills

- [design-mcp-workflow](../design-mcp-workflow/SKILL.md)
- [choose-zoom-approach](../choose-zoom-approach/SKILL.md)

