---
name: kw-zoom-plugin-start
display_name: kw-zoom-plugin-start
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-start - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-start` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this as the default entry skill for the plugin.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-start, then write the task. Fallback prompt: Use the kw-zoom-plugin-start skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-start` |
| Canonical name | `kw-zoom-plugin-start` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this as the default entry skill for the plugin.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: start
name: kw-zoom-plugin-start
description: Start here for any Zoom integration or app idea. Use when you need to choose the right Zoom surface, shape the architecture, or route into the correct implementation skill without reading the whole Zoom doc set first.
---

# Start

Use this as the default entry skill for the plugin.

## What This Skill Does

- Classifies the request by job-to-be-done, not by product name alone
- Routes into the right implementation skill
- Pulls in product-specific Zoom references only after the route is clear
- Prevents common early mistakes, especially Meeting SDK vs Video SDK and REST API vs MCP confusion

## Routing Table

| If the user wants to... | Route to |
|---|---|
| Choose the right Zoom surface for a new project | [plan-zoom-product](../plan-zoom-product/SKILL.md) |
| Set up OAuth, tokens, scopes, or app credentials | [setup-zoom-oauth](../setup-zoom-oauth/SKILL.md) |
| Embed or customize a Zoom meeting flow | [build-zoom-meeting-app](../build-zoom-meeting-app/SKILL.md) |
| Build a bot, recorder, or real-time meeting processor | [build-zoom-bot](../build-zoom-bot/SKILL.md) |
| Use Zoom-hosted MCP for AI workflows | [setup-zoom-mcp](../setup-zoom-mcp/SKILL.md) |
| Debug a broken integration | [debug-zoom](../debug-zoom/SKILL.md) |

## Supporting Zoom References

Use these only after selecting the workflow:

- [general](../general/SKILL.md)
- [rest-api](../rest-api/SKILL.md)
- [meeting-sdk](../meeting-sdk/SKILL.md)
- [video-sdk](../video-sdk/SKILL.md)
- [webhooks](../webhooks/SKILL.md)
- [websockets](../websockets/SKILL.md)
- [oauth](../oauth/SKILL.md)
- [zoom-mcp](../zoom-mcp/SKILL.md)

## Operating Rules

1. Prefer one clear recommendation over a product catalog dump.
2. Ask a short clarifier only when the route is genuinely ambiguous.
3. Keep the first response architectural and actionable, then go deep.
4. Pull in deeper references only when they directly help the current decision or implementation.

