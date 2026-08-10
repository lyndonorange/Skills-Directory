---
name: ima-sdk-basics
display_name: ima-sdk-basics
platform: Codex
category: General and specialized workflows
---

# ima-sdk-basics - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `ima-sdk-basics` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill for Interactive Media Ads (IMA) SDK client-side ad insertion when you are requesting video ads client-side into websites, apps, TVs or other platforms with VAST or VMAP. Do not use for Dynamic Ad Insertion

## How To Use It In Codex

In Codex, click the chat box, press /, choose ima-sdk-basics, then write the task. Fallback prompt: Use the ima-sdk-basics skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `ima-sdk-basics` |
| Canonical name | `ima-sdk-basics` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill for Interactive Media Ads (IMA) SDK client-side ad insertion when you are requesting video ads client-side into websites, apps, TVs or other platforms with VAST or VMAP. Do not use for Dynamic Ad Insertion

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: ima-sdk-basics
description: "Use this skill for Interactive Media Ads (IMA) SDK client-side ad insertion when you are requesting video ads client-side into websites, apps, TVs or other platforms with VAST or VMAP. Do not use for Dynamic Ad Insertion (DAI), SSAI, or SGAI (use the `ima-sdk-dai-basics` skill instead)."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# IMA SDK basics

The Google IMA SDK (Interactive Media Ads) lets you load in-stream video and
audio ads into websites, apps, TVs and other digital platforms. Use an IMA SDK
to request ads from any VAST-compliant ad server and manage ad playback.

## Prerequisites

Before integrating the IMA SDK, you **must** read the platform-specific guide
below to support all platforms that your app can support:

*   **Web/HTML5/ReactJs/NodeJs/Angular:** Read all these guides
    [ima-sdk-web-guide.md](references/ima-sdk-web-guide.md),
    [ima-sdk-web-iframe-mode.md](references/ima-sdk-web-iframe-mode.md),
    [ima-sdk-web-mobile-safari.md](references/ima-sdk-web-mobile-safari.md)
*   **Android/AndroidTV/ReactNative:** Read [ima-sdk-android-guide.md](references/ima-sdk-android-guide.md)
*   **iOS/tvOS/ReactNative:** Read all these guides
    [ima-sdk-ios-guide.md](references/ima-sdk-ios-guide.md),
    [ima-sdk-tvos-guide.md](references/ima-sdk-tvos-guide.md)

--------------------------------------------------------------------------------

## Quick start (general workflow)

1.  Import the SDK: Prerequisites, dependencies.
2.  Initialization: Early setup, Warmup, Settings Configuration, and Ad UI
    Setup.
3.  Ad Request: Creating and triggering the request, User gesture compliance.
4.  Ad Load Success/Failure: Handling the load event to get the AdsManager, or
    handling early fatal errors.
5.  Ad Playback Events: Listening to playback events via AdsManager to
    coordinate content play/pause, and handling non-fatal LOG events and fatal
    active playback errors.
6.  Cleanup: Properly destroying the AdsManager to release resources and prevent
    memory leaks.

For detailed, platform-specific implementation details, always refer to the
guides in the Prerequisites section.
