---
name: kw-zoom-plugin-plan-zoom-product
display_name: kw-zoom-plugin-plan-zoom-product
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-plan-zoom-product - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-plan-zoom-product` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-plan-zoom-product, then write the task. Fallback prompt: Use the kw-zoom-plugin-plan-zoom-product skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-plan-zoom-product` |
| Canonical name | `kw-zoom-plugin-plan-zoom-product` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: plan-zoom-product
name: kw-zoom-plugin-plan-zoom-product
description: Choose the right Zoom building surface for a use case and explain the tradeoffs clearly. Use when deciding between REST API, Webhooks, WebSockets, Meeting SDK, Video SDK, Zoom Apps SDK, Phone, Contact Center, or MCP for a specific product idea or integration goal.
argument-hint: "<product idea, app type, or integration goal>"
user-invocable: false
---

# /plan-zoom-product

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Choose between Zoom REST API, Webhooks, WebSockets, Meeting SDK, Video SDK, Zoom Apps SDK, Phone, Contact Center, or MCP for a specific use case.

## Usage

```text
/plan-zoom-product $ARGUMENTS
```

## Workflow

1. Identify the user's actual goal.
2. Classify whether the problem is automation, embedded meetings, custom video, in-client app behavior, event delivery, AI tooling, or support/phone/contact-center work.
3. If the request is ambiguous, ask one short clarifier before locking the recommendation.
4. Recommend the primary Zoom surface and list the minimum supporting pieces.
5. Explain why the rejected alternatives are worse for this case.
6. End with a concrete next-step plan.

## Output

- Recommended Zoom surface
- Supporting components required
- Key tradeoffs and constraints
- Suggested implementation sequence
- Relevant skill links for the next step

## Related Skills

- [start](../start/SKILL.md)
- [choose-zoom-approach](../choose-zoom-approach/SKILL.md)
- [design-mcp-workflow](../design-mcp-workflow/SKILL.md)

