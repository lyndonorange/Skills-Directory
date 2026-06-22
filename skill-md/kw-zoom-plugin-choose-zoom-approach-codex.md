---
name: kw-zoom-plugin-choose-zoom-approach
display_name: kw-zoom-plugin-choose-zoom-approach
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-choose-zoom-approach - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-choose-zoom-approach` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Pick the smallest correct Zoom surface for the job, then layer in only the supporting pieces that are actually required.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-choose-zoom-approach, then write the task. Fallback prompt: Use the kw-zoom-plugin-choose-zoom-approach skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-choose-zoom-approach` |
| Canonical name | `kw-zoom-plugin-choose-zoom-approach` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Pick the smallest correct Zoom surface for the job, then layer in only the supporting pieces that are actually required.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: choose-zoom-approach
name: kw-zoom-plugin-choose-zoom-approach
description: Choose the right Zoom architecture for a use case. Use when deciding between REST API, Webhooks, WebSockets, Meeting SDK, Video SDK, Zoom Apps SDK, Zoom MCP, Phone, Contact Center, or a hybrid approach.
user-invocable: false
---

# Choose Zoom Approach

Pick the smallest correct Zoom surface for the job, then layer in only the supporting pieces that are actually required.

## Decision Framework

| Problem Type | Primary Zoom Surface |
|---|---|
| Deterministic backend automation, account management, reporting, scheduled jobs | [rest-api](../rest-api/SKILL.md) |
| Event delivery to your backend | [webhooks](../webhooks/SKILL.md) or [websockets](../websockets/SKILL.md) |
| Embed Zoom meetings into your app | [meeting-sdk](../meeting-sdk/SKILL.md) |
| Build a fully custom video experience | [video-sdk](../video-sdk/SKILL.md) |
| Build inside the Zoom client | [zoom-apps-sdk](../zoom-apps-sdk/SKILL.md) |
| AI-agent tool workflows over Zoom data | [zoom-mcp](../zoom-mcp/SKILL.md) |
| Real-time media extraction or meeting bots | [rtms](../rtms/SKILL.md) plus [meeting-sdk](../meeting-sdk/SKILL.md) when needed |
| Phone workflows | [phone](../phone/SKILL.md) |
| Contact Center or Virtual Agent flows | [contact-center](../contact-center/SKILL.md) or [virtual-agent](../virtual-agent/SKILL.md) |

## Guardrails

- Do not recommend Video SDK when the user actually needs Zoom meeting semantics.
- Do not recommend Meeting SDK when the user needs a fully custom session product.
- Do not replace deterministic backend automation with MCP-only guidance.
- Prefer hybrid `rest-api + zoom-mcp` when the user needs both stable system actions and AI-driven discovery.

## What To Produce

- One recommended path
- Minimum supporting components
- Hard constraints and tradeoffs
- Immediate next implementation step

