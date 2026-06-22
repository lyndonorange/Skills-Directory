---
name: virtual-agent/web
display_name: virtual-agent/web
platform: Codex
category: General and specialized workflows
---

# virtual-agent/web - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `virtual-agent/web` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Official docs:

## How To Use It In Codex

In Codex, click the chat box, press /, choose virtual-agent/web, then write the task. Fallback prompt: Use the virtual-agent/web skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `virtual-agent/web` |
| Canonical name | `virtual-agent/web` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Official docs:

## Original SKILL.md

---
name: virtual-agent/web
description: "Zoom Virtual Agent SDK for web embeds. Use for campaign or entry ID chat launch, event-driven controls, user context updates, and CSP-safe deployment."
user-invocable: false
triggers:
  - "virtual agent web"
  - "zoomCampaignSdk"
  - "zcc-sdk"
  - "campaign embed"
  - "entry id"
  - "waitForReady"
  - "engagement_started"
---

# Zoom Virtual Agent SDK - Web

Official docs:
- https://developers.zoom.us/docs/virtual-agent/web/
- https://developers.zoom.us/docs/virtual-agent/web/reference/

## Quick Links

1. [concepts/lifecycle-and-events.md](concepts/lifecycle-and-events.md)
2. [examples/campaign-and-entry-patterns.md](examples/campaign-and-entry-patterns.md)
3. [references/web-reference-map.md](references/web-reference-map.md)
4. [troubleshooting/common-issues.md](troubleshooting/common-issues.md)

## Hard Guardrails

- Gate calls behind readiness (`zoomCampaignSdk:ready` or `waitForReady()`).
- Do not call `show/hide/open/close` before SDK initialization.
- Keep CSP and script host policy validated before debugging business logic.
- Prefer campaign embed over entry ID when minimizing user friction is a priority.

## Chaining

- Product-level architecture and drift checks: [../SKILL.md](../SKILL.md)
- Contact Center web context: [../../contact-center/web/SKILL.md](../../contact-center/web/SKILL.md)
- OAuth or REST for backend workflows: [../../oauth/SKILL.md](../../oauth/SKILL.md), [../../rest-api/SKILL.md](../../rest-api/SKILL.md)

