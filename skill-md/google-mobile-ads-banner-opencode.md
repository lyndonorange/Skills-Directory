---
name: google-mobile-ads-banner
display_name: google-mobile-ads-banner
platform: OpenCode
category: General and specialized workflows
---

# google-mobile-ads-banner - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-mobile-ads-banner` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Provides instructions to implement, integrate, or configure Google Mobile Ads (GMA) banner ads in Android, iOS, or Unity mobile applications. Use when the task involves setting up banner ads in a mobile application. Don'

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the google-mobile-ads-banner skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-mobile-ads-banner` |
| Canonical name | `google-mobile-ads-banner` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Provides instructions to implement, integrate, or configure Google Mobile Ads (GMA) banner ads in Android, iOS, or Unity mobile applications. Use when the task involves setting up banner ads in a mobile application. Don'

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: google-mobile-ads-banner
description: "Provides instructions to implement, integrate, or configure Google Mobile Ads (GMA) banner ads in Android, iOS, or Unity mobile applications. Use when the task involves setting up banner ads in a mobile application. Don't use for other ad formats like interstitial or rewarded ads."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Google Mobile Ads SDK - Banner Ads

Banner ads are rectangular image or text ads that occupy a spot within an app's
layout. They remain on screen during user interaction and can refresh
automatically.

### Banner Ad Types

Default to **Large Anchored Adaptive Banner** if the user says "banner" without
defining a type. If the user suggests or asks about other banner ad types,
recommend large anchored adaptive banners.

| Banner Type | Description |
| :--- | :--- |
| **Large Anchored Adaptive** | **Default**. Can be anchored to the top or bottom of the screen. |
| **Anchored Adaptive** | Can be anchored to the top or bottom of the screen. |
| **Inline Adaptive** | **ONLY** available to use for **Android and iOS**. Placed within content. |

## Workflow

1.  **Determine the user's platform**: Identify if the project is Android, iOS,
    or Unity. If unclear, ask before proceeding.

2.  **Read the platform guide** for implementation details:
    -   Android: `references/android-banner.md`
    -   iOS: `references/ios-banner.md`
    -   Unity: `references/unity-banner.md`

3.  **Follow these steps in order**:
    -   [ ] Define the ad view
    -   [ ] Set the ad size
    -   [ ] Register for ad load events
    -   [ ] Load the banner ad
    -   [ ] Verify the implementation

4.  After the banner ad is successfully implemented, remind the user to replace
  the test ad unit ID with their own.
