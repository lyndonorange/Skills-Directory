---
name: kw-zoom-plugin-debug-zoom-integration
display_name: kw-zoom-plugin-debug-zoom-integration
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-debug-zoom-integration - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-debug-zoom-integration` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill when the user already built something and it is failing.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-debug-zoom-integration, then write the task. Fallback prompt: Use the kw-zoom-plugin-debug-zoom-integration skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-debug-zoom-integration` |
| Canonical name | `kw-zoom-plugin-debug-zoom-integration` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill when the user already built something and it is failing.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: debug-zoom-integration
name: kw-zoom-plugin-debug-zoom-integration
description: Debug broken Zoom implementations quickly. Use when auth, webhooks, SDK joins, MCP transport, or real-time media workflows are failing and you need to isolate the layer before proposing a fix.
user-invocable: false
---

# Debug Zoom Integration

Use this skill when the user already built something and it is failing.

## Triage Order

1. Auth and app configuration
2. Request construction or event verification
3. SDK initialization or platform mismatch
4. Media/session behavior
5. MCP transport and capability assumptions

## Evidence To Request

- Exact error text
- Platform and SDK/runtime
- Relevant request or payload sample
- What worked versus what failed
- Whether the issue is reproducible or intermittent

## Reference Routing

- [oauth](../oauth/SKILL.md)
- [rest-api](../rest-api/SKILL.md)
- [webhooks](../webhooks/SKILL.md)
- [meeting-sdk](../meeting-sdk/SKILL.md)
- [video-sdk](../video-sdk/SKILL.md)
- [rtms](../rtms/SKILL.md)
- [zoom-mcp](../zoom-mcp/SKILL.md)

## Output

- Most likely failing layer
- Ranked hypotheses
- Short fix plan
- Verification steps

