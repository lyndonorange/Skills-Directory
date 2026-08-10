---
name: mobile-ui-accessibility
display_name: mobile-ui-accessibility
platform: OpenCode
category: Software engineering and app building
---

# mobile-ui-accessibility - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `mobile-ui-accessibility` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Implement and independently review accessible native iOS and iPadOS interfaces across SwiftUI and UIKit, including VoiceOver semantics, Dynamic Type, contrast, touch targets, focus, keyboard and pointer input, safe areas

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the mobile-ui-accessibility skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `mobile-ui-accessibility` |
| Canonical name | `mobile-ui-accessibility` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Implement and independently review accessible native iOS and iPadOS interfaces across SwiftUI and UIKit, including VoiceOver semantics, Dynamic Type, contrast, touch targets, focus, keyboard and pointer input, safe areas


## Original SKILL.md

---
name: mobile-ui-accessibility
description: Implement and independently review accessible native iOS and iPadOS interfaces across SwiftUI and UIKit, including VoiceOver semantics, Dynamic Type, contrast, touch targets, focus, keyboard and pointer input, safe areas, motion, transparency, localization, orientation, size classes, multitasking, and platform states. Use during mobile design, implementation, accessibility remediation, or the mandatory accessibility verification stage before an iPhone or iPad build can advance through apple-build-supervisor.
---

# Mobile UI Accessibility

Treat accessibility as correctness. Read project targets, existing accessibility conventions, and `references/verification-matrix.md` before editing or reviewing.

## Workflow

1. Identify supported devices, OS versions, input methods, orientations, size classes, languages, and assistive technologies.
2. Inspect semantics before visuals: roles, labels, values, hints, grouping, order, actions, focus, headings, and announcements.
3. Use native controls and semantic colors where possible. Preserve system text styles and avoid fixed frames that clip scaled content.
4. Verify interactive targets, visible states, contrast, differentiation without color, reduced motion, reduced transparency, and sufficient time or recovery.
5. Verify iPad adaptation: compact and regular widths, multitasking, keyboard, pointer, popovers, sidebars, focus, and rotation where supported.
6. Run the smallest applicable automated checks, then inspect the rendered app with VoiceOver and representative text sizes.
7. Report real evidence and remaining manual checks. Do not pass your own implementation; hand it to a different reviewer.

## Review Output

```text
VERDICT: PASS | REVISE | BLOCKED
TARGETS AND CONFIGURATIONS:
SEMANTICS AND FOCUS:
DYNAMIC TYPE AND LAYOUT:
CONTRAST AND NON-COLOR CUES:
INPUT AND TARGETS:
MOTION AND TRANSPARENCY:
IPAD ADAPTATION:
EVIDENCE:
NOT VERIFIED:
HUMAN DECISION REQUIRED:
```

Return this report to `apple-build-supervisor`. Agent `PASS` still requires explicit human approval.
