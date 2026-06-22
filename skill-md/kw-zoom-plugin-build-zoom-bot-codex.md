---
name: kw-zoom-plugin-build-zoom-bot
display_name: kw-zoom-plugin-build-zoom-bot
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-build-zoom-bot - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-build-zoom-bot` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill for automation that joins meetings, captures media, or reacts to live session data.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-build-zoom-bot, then write the task. Fallback prompt: Use the kw-zoom-plugin-build-zoom-bot skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-build-zoom-bot` |
| Canonical name | `kw-zoom-plugin-build-zoom-bot` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill for automation that joins meetings, captures media, or reacts to live session data.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: build-zoom-bot
name: kw-zoom-plugin-build-zoom-bot
description: Build a Zoom meeting bot, recorder, or real-time media workflow. Use when joining meetings programmatically, processing live media or transcripts, or combining Meeting SDK, RTMS, and backend services.
---

# /build-zoom-bot

Use this skill for automation that joins meetings, captures media, or reacts to live session data.

## Covers

- Bot architecture
- Meeting join strategy
- Real-time media and transcript handling
- Backend orchestration
- Storage, post-processing, and event flow design

## Workflow

1. Clarify whether the bot needs to join, observe, transcribe, summarize, or act.
2. Route to Meeting SDK and RTMS as the core implementation path.
3. Add REST API for meeting/resource management and Webhooks for asynchronous events when needed.
4. Call out environment and lifecycle constraints early.

## Primary References

- [meeting-sdk](../meeting-sdk/SKILL.md)
- [rtms](../rtms/SKILL.md)
- [scribe](../scribe/SKILL.md)
- [rest-api](../rest-api/SKILL.md)
- [webhooks](../webhooks/SKILL.md)

## Common Mistakes

- Treating batch transcription and live media as the same workflow
- Designing the bot before defining join authority and auth model
- Forgetting post-meeting storage and retry behavior

