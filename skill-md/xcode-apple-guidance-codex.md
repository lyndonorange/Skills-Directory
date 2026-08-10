---
name: xcode-apple-guidance
display_name: xcode-apple-guidance
platform: Codex
category: Software engineering and app building
---

# xcode-apple-guidance - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `xcode-apple-guidance` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Find and cite version-matched Apple guidance from the active local Xcode installation without copying or redistributing Apple documentation. Use before relying on version-sensitive Swift, SwiftUI, UIKit, AppKit, accessib

## How To Use It In Codex

In Codex, click the chat box, press /, choose xcode-apple-guidance, then write the task. Fallback prompt: Use the xcode-apple-guidance skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `xcode-apple-guidance` |
| Canonical name | `xcode-apple-guidance` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Find and cite version-matched Apple guidance from the active local Xcode installation without copying or redistributing Apple documentation. Use before relying on version-sensitive Swift, SwiftUI, UIKit, AppKit, accessib


## Original SKILL.md

---
name: xcode-apple-guidance
description: Find and cite version-matched Apple guidance from the active local Xcode installation without copying or redistributing Apple documentation. Use before relying on version-sensitive Swift, SwiftUI, UIKit, AppKit, accessibility, testing, build, coding-intelligence, or platform APIs; when an article or skill claims behavior from a newer Xcode; or when a coding agent needs evidence tied to the installed toolchain.
---

# Xcode Apple Guidance

Treat the active Xcode and project deployment targets as authoritative. This skill discovers and searches local Apple-authored guidance; it does not install third-party packages or mirror Apple content into portable bundles.

## Workflow

1. Run `xcodebuild -version` and `xcode-select -p`.
2. Run `scripts/find_xcode_guidance.py --topic '<topic>'`.
3. Read only the returned local documents relevant to the task.
4. Record Xcode version, document filename, local source path, and the API or behavior supported.
5. Confirm deployment-target availability in the SDK or compiler before implementation.
6. If local guidance is absent, use official Apple Developer documentation and label the result as external rather than local evidence.

## Version Gate

The current machine may not expose newer Xcode agent commands. Never assume `xcrun agent skills export` exists because an article mentions Xcode 27. Check the active version and command help first. If a future Xcode provides export, write only to a scoped quarantine directory, inspect provenance and contents, and never replace existing skills without review and human approval.

## Output

```text
XCODE VERSION:
DEVELOPER DIRECTORY:
TOPIC:
LOCAL DOCUMENTS READ:
SUPPORTED CLAIMS:
DEPLOYMENT-TARGET CHECK:
EXTERNAL APPLE SOURCES:
NOT VERIFIED:
```

Read `references/source-policy.md` before copying, sharing, or packaging any derived material.
