---
name: kw-zoom-plugin-design-mcp-workflow
display_name: kw-zoom-plugin-design-mcp-workflow
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-design-mcp-workflow - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-design-mcp-workflow` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill when the user wants Claude or another MCP-capable client to interact with Zoom via tool calls instead of only deterministic API code.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-design-mcp-workflow, then write the task. Fallback prompt: Use the kw-zoom-plugin-design-mcp-workflow skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-design-mcp-workflow` |
| Canonical name | `kw-zoom-plugin-design-mcp-workflow` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill when the user wants Claude or another MCP-capable client to interact with Zoom via tool calls instead of only deterministic API code.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: design-mcp-workflow
name: kw-zoom-plugin-design-mcp-workflow
description: Design a Zoom MCP workflow for Claude. Use when deciding whether Zoom MCP fits a task, when planning tool-based AI workflows, or when separating MCP responsibilities from REST API responsibilities.
user-invocable: false
---

# Design MCP Workflow

Use this skill when the user wants Claude or another MCP-capable client to interact with Zoom via tool calls instead of only deterministic API code.

## Covers

- MCP fit assessment
- REST API vs MCP boundaries
- Hybrid architectures
- Connector expectations
- Whiteboard-specific MCP routing

## Workflow

1. Decide whether the problem is agentic tooling, deterministic automation, or both.
2. Route MCP-only tasks to [zoom-mcp](../zoom-mcp/SKILL.md).
3. Route hybrid tasks to both [zoom-mcp](../zoom-mcp/SKILL.md) and [rest-api](../rest-api/SKILL.md).
4. If Whiteboard is central, route to [zoom-mcp/whiteboard](../zoom-mcp/whiteboard/SKILL.md).
5. Call out transport, auth, and client capability assumptions explicitly.

## Common Mistakes

- Using MCP for deterministic backend jobs that should stay in REST
- Treating MCP as a replacement for all API design
- Ignoring client transport support and auth requirements

