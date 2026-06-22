---
name: virtual-agent/ios
display_name: virtual-agent/ios
platform: Codex
category: General and specialized workflows
---

# virtual-agent/ios - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `virtual-agent/ios` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Official docs:

## How To Use It In Codex

In Codex, click the chat box, press /, choose virtual-agent/ios, then write the task. Fallback prompt: Use the virtual-agent/ios skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `virtual-agent/ios` |
| Canonical name | `virtual-agent/ios` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Official docs:

## Original SKILL.md

---
name: virtual-agent/ios
description: "Zoom Virtual Agent iOS integration via WKWebView. Use for Swift/Objective-C script injection, message handlers, support_handoff relay, and URL routing policies."
user-invocable: false
triggers:
  - "virtual agent ios"
  - "wkwebview zva"
  - "support_handoff ios"
  - "zoomCampaignSdk:ready ios"
  - "wkusercontentcontroller"
---

# Zoom Virtual Agent - iOS

Official docs:
- https://developers.zoom.us/docs/virtual-agent/ios/

## Quick Links

1. [concepts/webview-lifecycle.md](concepts/webview-lifecycle.md)
2. [examples/js-bridge-patterns.md](examples/js-bridge-patterns.md)
3. [references/ios-reference-map.md](references/ios-reference-map.md)
4. [troubleshooting/common-issues.md](troubleshooting/common-issues.md)

## Integration Model

- Load campaign URL in `WKWebView`.
- Inject `window.zoomCampaignSdkConfig` using `WKUserScript`.
- Register message handlers for exit/common/handoff flows.
- Handle URL behavior in navigation delegates (`in-app`, `SFSafariViewController`, or system browser).

## Hard Guardrails

- Register scripts and handlers before web interaction.
- Handle iOS 14.5+ download behavior where needed.
- Keep deprecated `openURL` command support as fallback only.

## Chaining

- Product-level patterns: [../SKILL.md](../SKILL.md)
- Contact Center mobile scope: [../../contact-center/ios/SKILL.md](../../contact-center/ios/SKILL.md)

