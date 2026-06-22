---
name: kw-zoom-plugin-debug-zoom
display_name: kw-zoom-plugin-debug-zoom
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-debug-zoom - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-debug-zoom` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-debug-zoom, then write the task. Fallback prompt: Use the kw-zoom-plugin-debug-zoom skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-debug-zoom` |
| Canonical name | `kw-zoom-plugin-debug-zoom` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: debug-zoom
name: kw-zoom-plugin-debug-zoom
description: Debug a broken Zoom integration by isolating the failure point and routing into the right Zoom references. Use when auth, API, webhook, SDK, or MCP behavior is failing and you need a ranked hypothesis list plus verification steps.
argument-hint: "<symptoms, error, or failing flow>"
---

# /debug-zoom

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Debug Zoom auth, API, webhook, SDK, or MCP issues without wandering through the entire docs set.

## Usage

```text
/debug-zoom $ARGUMENTS
```

## Workflow

1. Identify the failing layer: auth, API request, webhook, SDK init, media/session behavior, or MCP transport.
2. Ask for the minimum missing evidence: exact error, platform, request/response, event payload, or code path.
3. Produce 2-4 plausible causes ranked by likelihood.
4. Route to the most relevant deep references in `skills/`.
5. Give a short verification plan so the user can confirm the fix.

## Output

- Most likely failure layer
- Ranked hypotheses
- Targeted fix steps
- Verification checklist
- Relevant skill links

## Related Skills

- [debug-zoom-integration](../debug-zoom-integration/SKILL.md)
- [setup-zoom-oauth](../setup-zoom-oauth/SKILL.md)
- [design-mcp-workflow](../design-mcp-workflow/SKILL.md)

