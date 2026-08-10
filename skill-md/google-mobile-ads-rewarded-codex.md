---
name: google-mobile-ads-rewarded
display_name: google-mobile-ads-rewarded
platform: Codex
category: General and specialized workflows
---

# google-mobile-ads-rewarded - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-mobile-ads-rewarded` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK rewarded ads in Android or iOS mobile applications. Use this skill when the task involves setting up rewarded ads. Don't use

## How To Use It In Codex

In Codex, click the chat box, press /, choose google-mobile-ads-rewarded, then write the task. Fallback prompt: Use the google-mobile-ads-rewarded skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-mobile-ads-rewarded` |
| Canonical name | `google-mobile-ads-rewarded` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK rewarded ads in Android or iOS mobile applications. Use this skill when the task involves setting up rewarded ads. Don't use

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: google-mobile-ads-rewarded
description: "Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK rewarded ads in Android or iOS mobile applications. Use this skill when the task involves setting up rewarded ads. Don't use for \"rewarded interstitial\" ads."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Google Mobile Ads SDK - Rewarded Ads

Rewarded ads reward users with in-app items for interacting with full-screen
ads. Rewarded ads are served after a user explicitly opts in to view a rewarded
ad.

### Ad Placement Guidelines

**CRITICAL:** You MUST evaluate and apply the following Ad Placement Guidelines
before proceeding with any rewarded ad implementation.

*   **Determine Ad Placement**:
    *   [ ] **Identify the target file** where the ad should be placed. Ask if
        unsure.

## Workflow

1.  **Determine the user's platform**: Identify if the project is Android or
    iOS. If unclear, ask before proceeding.

2.  **Read the platform guide** for implementation details:
    -   Android: `references/android-rewarded.md`
    -   iOS: `references/ios-rewarded.md`

3.  **Follow these steps in order**:
    -   [ ] Load the ad
    -   [ ] Register for ad event callbacks
    -   [ ] Add an opt-in UI element
    -   [ ] Show the ad
    -   [ ] Verify the implementation
