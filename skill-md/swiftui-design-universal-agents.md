---
name: swiftui-design
display_name: swiftui-design
platform: Universal Agents
category: Software engineering and app building
---

# swiftui-design - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-design` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Design and review intentional, accessible SwiftUI interfaces for iOS, iPadOS, and macOS using product context, native platform conventions, visual systems, semantic color, Dynamic Type, layout, motion, interaction states

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the swiftui-design skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-design` |
| Canonical name | `swiftui-design` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Design and review intentional, accessible SwiftUI interfaces for iOS, iPadOS, and macOS using product context, native platform conventions, visual systems, semantic color, Dynamic Type, layout, motion, interaction states


## Original SKILL.md

---
name: swiftui-design
description: Design and review intentional, accessible SwiftUI interfaces for iOS, iPadOS, and macOS using product context, native platform conventions, visual systems, semantic color, Dynamic Type, layout, motion, interaction states, and rendered evidence. Use when defining or revising an Apple app's UX flows, visual direction, design tokens, components, adaptive layouts, reference fidelity, or design-quality acceptance criteria. Pair with apple-build-supervisor when the work must pass independent agent verification and explicit human approval.
---

# SwiftUI Design

Design from product intent and platform behavior, then prove the result in rendered software. Treat the existing app, brand system, deployment targets, and applicable `AGENTS.md` files as authoritative.

## Operating Contract

- Preserve native iOS, iPadOS, and macOS conventions; do not force one interaction model across platforms.
- Use semantic colors, Dynamic Type, VoiceOver, keyboard access, contrast, reduced motion, reduced transparency, and platform-appropriate target sizes from the first design pass.
- Treat visual patterns as context-dependent. Do not ban or require gradients, cards, font families, color counts, or spacing grids without a product reason.
- Offer multiple directions only when the visual direction is genuinely unresolved. When an approved design system exists, extend it consistently.
- Prefer real brand assets and SF Symbols. Mark placeholders honestly and never present fabricated assets as official.
- Pair with `reference-to-swiftui` for evidence extraction, `swiftui-master` for architecture, `swiftui-expert-skill` for implementation, and `swiftui-pro` for independent review.
- Do not declare a stage complete. Return evidence to `apple-build-supervisor` for agent and human approval.

## Design Workflow

1. **Ground the brief.** Identify users, primary jobs, constraints, supported platforms, content, data sensitivity, and success criteria.
2. **Inspect context.** Read existing screens, design tokens, assets, platform targets, localization, accessibility, and reference material.
3. **Map flows and states.** Cover entry, success, empty, loading, error, disabled, offline, permission, destructive, and recovery states that apply.
4. **Choose platform behavior.** Read `references/apple-platforms.md` and define navigation, presentation, input, windowing, density, and adaptation per platform.
5. **Define the visual system.** Specify semantic color roles, typography roles, spacing rhythm, shape, elevation/material, iconography, motion, and component states.
6. **Render representative screens.** Use previews, Simulator, or the running Mac app. Include relevant appearance, text-size, size-class, and window-size variants.
7. **Review against intent.** Check hierarchy, clarity, consistency, platform fit, accessibility, interaction completeness, and reference fidelity.
8. **Package the handoff.** Return the artifact set below with open questions and residual risks.

## Required Handoff

```text
DESIGN STAGE:
TARGETS: iOS | iPadOS | macOS
USER AND PRIMARY JOB:
APPROVED REQUIREMENTS:
FLOW AND STATE INVENTORY:
PLATFORM ADAPTATIONS:
VISUAL SYSTEM:
COMPONENT CONTRACTS:
ACCESSIBILITY REQUIREMENTS:
RENDERED EVIDENCE:
OPEN QUESTIONS:
NOT VERIFIED:
HUMAN DECISION REQUIRED:
```

For a governed build, submit this handoff to a fresh design reviewer. The reviewer must return `PASS`, `REVISE`, or `BLOCKED`; the human must explicitly approve before the supervisor advances the ledger.

## References

- Apple platform adaptation: `references/apple-platforms.md`.
- Detailed review dimensions: `references/design-review.md`.
- Layout patterns: `references/layout-patterns.md`.
- Typography and semantic color: `references/typography-color.md`.
- Deliberate anti-generic heuristics: `references/anti-ai-slop.md`; treat these as prompts for judgment, not blanket prohibitions.
- Friendly minimal direction: `references/friendly-minimal-style.md`; use only when selected by the user or existing product.
- Swift helpers: `references/swift-extensions.md`.

## Verification

Require screenshots or previews for every supported platform and materially different layout. Record the exact target, appearance, content size, and window or device class. A design stage is incomplete when interaction states, accessibility behavior, or platform adaptation remain assumed rather than inspected.
