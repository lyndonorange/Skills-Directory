---
name: swiftui-pattern-gallery
display_name: swiftui-pattern-gallery
platform: Universal Agents
category: Software engineering and app building
---

# swiftui-pattern-gallery - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-pattern-gallery` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Mine Ivan Vorobei's SwiftUI example collection for interaction, animation, gesture, layout, navigation, drawing, UIKit interop, and Combine inspiration, then translate the selected idea into current SwiftUI. Use when a u

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the swiftui-pattern-gallery skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-pattern-gallery` |
| Canonical name | `swiftui-pattern-gallery` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Mine Ivan Vorobei's SwiftUI example collection for interaction, animation, gesture, layout, navigation, drawing, UIKit interop, and Combine inspiration, then translate the selected idea into current SwiftUI. Use when a u


## Original SKILL.md

---
name: swiftui-pattern-gallery
description: Mine Ivan Vorobei's SwiftUI example collection for interaction, animation, gesture, layout, navigation, drawing, UIKit interop, and Combine inspiration, then translate the selected idea into current SwiftUI. Use when a user wants an example-driven pattern, animation reference, prototype inspiration, or modernization of an older SwiftUI sample. Do not copy obsolete APIs unchanged.
---

# SwiftUI Pattern Gallery

Use the upstream repository as a visual and interaction index, not as a modern architecture authority.

## Workflow

1. Define the interaction or visual behavior to reproduce.
2. Read `references/pattern-index.md` and choose the closest example.
3. Inspect the current upstream source if implementation detail is needed.
4. Extract the underlying pattern: state machine, geometry, gesture, transition, data flow, or interop boundary.
5. Reimplement it with APIs appropriate to the project's deployment target and local architecture.
6. Verify behavior, accessibility, reduced motion, and performance.

## Workflow Routing

| Need | Pattern family |
|---|---|
| Motion and gesture | Cards, transitions, blur, side menu, flip/clock patterns |
| Structure | Lists, navigation, complex composition, iPad scenes |
| Data | Async image loading, GitHub API, search, Redux/Flux examples |
| Drawing and interop | Paths, shapes, UIControls, UIKit bridging |

## Gotchas

- The collection began in early SwiftUI eras; syntax and architecture may be obsolete.
- `.animation(_:)` without a value and older navigation APIs often require modernization.
- External linked projects have separate licenses; inspect them before copying code.
- A visually appealing animation still needs reduced-motion and input-accessibility behavior.

## Examples

- “Build an animatable card stack” → study the card example, extract geometry/state, implement with current animation APIs.
- “Find a SwiftUI/UIKit bridge example” → use the interop family, then adapt to the current deployment target.

## References

- Read `references/pattern-index.md` for the catalog and modernization checklist.
