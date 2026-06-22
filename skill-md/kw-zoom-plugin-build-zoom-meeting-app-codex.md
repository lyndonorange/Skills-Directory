---
name: kw-zoom-plugin-build-zoom-meeting-app
display_name: kw-zoom-plugin-build-zoom-meeting-app
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-build-zoom-meeting-app - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-build-zoom-meeting-app` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill for embedded meeting experiences and meeting lifecycle implementation.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-build-zoom-meeting-app, then write the task. Fallback prompt: Use the kw-zoom-plugin-build-zoom-meeting-app skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-build-zoom-meeting-app` |
| Canonical name | `kw-zoom-plugin-build-zoom-meeting-app` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill for embedded meeting experiences and meeting lifecycle implementation.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: build-zoom-meeting-app
name: kw-zoom-plugin-build-zoom-meeting-app
description: Build or embed a Zoom meeting flow. Use when implementing Meeting SDK joins, web or mobile meeting embeds, meeting lifecycle flows, or when deciding between Meeting SDK and Video SDK.
---

# /build-zoom-meeting-app

Use this skill for embedded meeting experiences and meeting lifecycle implementation.

## Covers

- Meeting SDK selection and platform routing
- Join/auth implementation planning
- Meeting creation plus join flow design
- Web vs native platform considerations
- Meeting SDK vs Video SDK boundary decisions

## Workflow

1. Confirm whether the user wants a Zoom meeting or a custom video session.
2. Route to Meeting SDK if the user needs actual Zoom meetings.
3. Pull in the relevant platform references.
4. Add REST API only for meeting creation, resource management, or reporting.
5. Add webhooks or RTMS only when the use case explicitly needs them.

## Primary References

- [meeting-sdk](../meeting-sdk/SKILL.md)
- [rest-api](../rest-api/SKILL.md)
- [webhooks](../webhooks/SKILL.md)
- [rtms](../rtms/SKILL.md)
- [video-sdk](../video-sdk/SKILL.md)

## Common Mistakes

- Using Video SDK for normal Zoom meeting embeds
- Mixing resource-management APIs into the core join flow without reason
- Skipping platform-specific SDK constraints until too late

