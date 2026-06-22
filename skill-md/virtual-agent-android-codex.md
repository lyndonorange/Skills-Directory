---
name: virtual-agent/android
display_name: virtual-agent/android
platform: Codex
category: General and specialized workflows
---

# virtual-agent/android - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `virtual-agent/android` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Official docs:

## How To Use It In Codex

In Codex, click the chat box, press /, choose virtual-agent/android, then write the task. Fallback prompt: Use the virtual-agent/android skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `virtual-agent/android` |
| Canonical name | `virtual-agent/android` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Official docs:

## Original SKILL.md

---
name: virtual-agent/android
description: "Zoom Virtual Agent Android integration via WebView. Use for Java/Kotlin bridge callbacks, native URL handling, support_handoff relay, and lifecycle-safe embedding."
user-invocable: false
triggers:
  - "virtual agent android"
  - "android webview zva"
  - "zoomCampaignSdk:ready android"
  - "support_handoff android"
  - "javascriptinterface"
---

# Zoom Virtual Agent - Android

Official docs:
- https://developers.zoom.us/docs/virtual-agent/android/

## Quick Links

1. [concepts/webview-lifecycle.md](concepts/webview-lifecycle.md)
2. [examples/js-bridge-patterns.md](examples/js-bridge-patterns.md)
3. [references/android-reference-map.md](references/android-reference-map.md)
4. [troubleshooting/common-issues.md](troubleshooting/common-issues.md)

## Integration Model

- Host campaign URL in Android WebView.
- Inject runtime context (`window.zoomCampaignSdkConfig`).
- Register JavaScript bridge for `exitHandler`, `commonHandler`, `support_handoff`.
- Apply URL policy via `shouldOverrideUrlLoading` and optional multi-window callbacks.

## Hard Guardrails

- Initialize handlers before expecting JS callbacks.
- Treat legacy `openURL` command handling as compatibility path only.
- Prefer DOM links or `window.open` handling plus explicit native routing.

## Chaining

- Product-level patterns: [../SKILL.md](../SKILL.md)
- Contact Center mobile scope: [../../contact-center/android/SKILL.md](../../contact-center/android/SKILL.md)

