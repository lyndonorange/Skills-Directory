---
name: google-mobile-ads-interstitial
display_name: google-mobile-ads-interstitial
platform: OpenCode
category: General and specialized workflows
---

# google-mobile-ads-interstitial - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-mobile-ads-interstitial` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK interstitial ads in Android and iOS mobile applications. Use this skill when the task involves setting up interstitial ads.

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the google-mobile-ads-interstitial skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-mobile-ads-interstitial` |
| Canonical name | `google-mobile-ads-interstitial` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK interstitial ads in Android and iOS mobile applications. Use this skill when the task involves setting up interstitial ads.

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: google-mobile-ads-interstitial
description: "Provides instructions for implementing, integrating, or configuring Google Mobile Ads (GMA) SDK interstitial ads in Android and iOS mobile applications. Use this skill when the task involves setting up interstitial ads. Don't use for \"rewarded interstitial\" ads."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Google Mobile Ads SDK - Interstitial Ads

Interstitial ads show full-page ads for users on mobile apps. Interstitial ads
are designed to be placed between content and are best placed at natural app
transition points.

### Ad Placement Guidelines

**CRITICAL:** You MUST evaluate and apply the following Ad Placement Guidelines
before proceeding with any interstitial ad implementation.

*   **Determine Ad Placement**:
    *   [ ] **Identify the target file** where the ad should be placed. Ask if
        unsure.

## Workflow

1.  **Determine the user's platform**: Identify if the project is Android or
    iOS. If unclear, ask before proceeding.

2.  **Read the platform guide** for implementation details:
    -   Android: `references/android-interstitial.md`
    -   iOS: `references/ios-interstitial.md`

3.  **Follow these steps in order**:
    -   [ ] Load the ad
    -   [ ] Register for ad event callbacks
    -   [ ] Show the ad
    -   [ ] Verify the implementation
