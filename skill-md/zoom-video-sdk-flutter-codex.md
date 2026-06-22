---
name: zoom-video-sdk-flutter
display_name: zoom-video-sdk-flutter
platform: Codex
category: General and specialized workflows
---

# zoom-video-sdk-flutter - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `zoom-video-sdk-flutter` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill for Flutter apps that build custom real-time video session experiences with Zoom Video SDK.

## How To Use It In Codex

In Codex, click the chat box, press /, choose zoom-video-sdk-flutter, then write the task. Fallback prompt: Use the zoom-video-sdk-flutter skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `zoom-video-sdk-flutter` |
| Canonical name | `zoom-video-sdk-flutter` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill for Flutter apps that build custom real-time video session experiences with Zoom Video SDK.

## Original SKILL.md

---
name: zoom-video-sdk-flutter
description: |
  Zoom Video SDK for Flutter. Use when building custom video session apps in Flutter with
  flutter_zoom_videosdk, event-driven architecture, session lifecycle handling, and mobile
  platform integration patterns.
user-invocable: false
triggers:
  - video sdk flutter
  - zoom flutter video sdk
  - flutter video session
  - flutter_zoom_videosdk
  - zoom custom video flutter
  - flutter live transcription zoom
---

# Zoom Video SDK (Flutter)

Use this skill for Flutter apps that build custom real-time video session experiences with Zoom Video SDK.

## Quick Links

1. **[Lifecycle Workflow](concepts/lifecycle-workflow.md)** - init -> joinSession -> media/control -> leave -> cleanup
2. **[SDK Architecture Pattern](concepts/sdk-architecture-pattern.md)** - helper-based API surface and event model
3. **[High-Level Scenarios](concepts/high-level-scenarios.md)** - common product patterns
4. **[Setup Guide](examples/setup-guide.md)** - package setup + platform prerequisites
5. **[Session Join Pattern](examples/session-join-pattern.md)** - tokenized session join flow
6. **[Event Handling Pattern](examples/event-handling-pattern.md)** - listener mapping and action routing
7. **[SKILL.md](SKILL.md)** - complete navigation

## Core Notes

- Video SDK sessions are custom sessions, not Zoom Meetings.
- Keep SDK credentials server-side; generate JWT token on backend.
- Integration is strongly event-driven; bind listener flows early.
- Feature support and enum names can drift by wrapper/native version.

## References

- [Flutter Reference Index](references/flutter-reference.md)
- [Module Map](references/module-map.md)
- [Official Sources](references/official-sources.md)
- [Deprecated and Contradictions](troubleshooting/deprecated-and-contradictions.md)

## Related Skills

- [zoom-video-sdk](../SKILL.md)
- [zoom-oauth](../../oauth/SKILL.md)
- [zoom-general](../../general/SKILL.md)


## Merged from video-sdk/flutter/SKILL.md

# Zoom Video SDK Flutter - Documentation Index

## Start Here

1. [SKILL.md](SKILL.md)
2. [Lifecycle Workflow](concepts/lifecycle-workflow.md)
3. [SDK Architecture Pattern](concepts/sdk-architecture-pattern.md)
4. [Setup Guide](examples/setup-guide.md)

## Concepts

- [Lifecycle Workflow](concepts/lifecycle-workflow.md)
- [SDK Architecture Pattern](concepts/sdk-architecture-pattern.md)
- [High-Level Scenarios](concepts/high-level-scenarios.md)

## Examples

- [Setup Guide](examples/setup-guide.md)
- [Session Join Pattern](examples/session-join-pattern.md)
- [Event Handling Pattern](examples/event-handling-pattern.md)

## References

- [Flutter Reference Index](references/flutter-reference.md)
- [Module Map](references/module-map.md)
- [Official Sources](references/official-sources.md)

## Troubleshooting

- [Common Issues](troubleshooting/common-issues.md)
- [Version Drift](troubleshooting/version-drift.md)
- [Deprecated and Contradictions](troubleshooting/deprecated-and-contradictions.md)

## Operations

- [RUNBOOK.md](RUNBOOK.md) - 5-minute preflight and debugging checklist.

