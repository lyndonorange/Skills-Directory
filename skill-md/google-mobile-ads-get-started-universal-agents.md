---
name: google-mobile-ads-get-started
display_name: google-mobile-ads-get-started
platform: Universal Agents
category: General and specialized workflows
---

# google-mobile-ads-get-started - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-mobile-ads-get-started` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Provides instructions for integrating the Google Mobile Ads (GMA) SDK. Use this skill when the user wants to get started with, install, integrate, set up, or configure the SDK for AdMob or Ad Manager, GMA Next-Gen SDK or

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the google-mobile-ads-get-started skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-mobile-ads-get-started` |
| Canonical name | `google-mobile-ads-get-started` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Provides instructions for integrating the Google Mobile Ads (GMA) SDK. Use this skill when the user wants to get started with, install, integrate, set up, or configure the SDK for AdMob or Ad Manager, GMA Next-Gen SDK or

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: google-mobile-ads-get-started
description: "Provides instructions for integrating the Google Mobile Ads (GMA) SDK. Use this skill when the user wants to get started with, install, integrate, set up, or configure the SDK for AdMob or Ad Manager, GMA Next-Gen SDK or mobile ads framework in an Android, iOS, or Unity application."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Google Mobile Ads SDK - Install

## Workflow

1.  **Determine the user's platform**: Identify if the project is Android, iOS,
    or Unity. If unclear, ask before proceeding.

2. **Read the platform guide** for implementation details:
    - Android: `references/android-get-started.md`
    - iOS: `references/ios-get-started.md`
    - Unity: `references/unity-get-started.md`

3. **Follow these steps in order**:
   - [ ] Add the SDK dependency
   - [ ] Set the application identifier
   - [ ] Initialize the SDK
   - [ ] Verify the integration

4. After the SDK is successfully installed, ask the user to select an ad format
   to continue the integration.
