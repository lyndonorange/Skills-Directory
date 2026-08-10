---
name: reference-to-swiftui
display_name: reference-to-swiftui
platform: Universal Agents
category: General and specialized workflows
---

# reference-to-swiftui - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `reference-to-swiftui` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Recreate or adapt visual references as accessible production SwiftUI from Figma URLs or files, PDFs, PNG/JPEG/WebP/HEIC/SVG images, screenshots, local design files, HTML/CSS, and live website references. Use when transla

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the reference-to-swiftui skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `reference-to-swiftui` |
| Canonical name | `reference-to-swiftui` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Recreate or adapt visual references as accessible production SwiftUI from Figma URLs or files, PDFs, PNG/JPEG/WebP/HEIC/SVG images, screenshots, local design files, HTML/CSS, and live website references. Use when transla


## Original SKILL.md

---
name: reference-to-swiftui
description: Recreate or adapt visual references as accessible production SwiftUI from Figma URLs or files, PDFs, PNG/JPEG/WebP/HEIC/SVG images, screenshots, local design files, HTML/CSS, and live website references. Use when translating an existing design, mockup, screenshot, document page, or webpage into SwiftUI while preserving hierarchy, tokens, assets, responsive behavior, platform conventions, and explicit fidelity decisions.
---

# Reference to SwiftUI

Translate evidence, not guesses. Preserve the reference’s information architecture and visual intent while adapting interaction, accessibility, and layout to the target Apple platform.

## Input Router

| Input | Acquire evidence |
|---|---|
| Figma URL or file | Use the available Figma connector or tools to read the exact node, variables, components, assets, and rendered context. Ask for a node-specific URL only when the connector requires one. |
| PDF | Inspect page count and text, render only relevant pages at readable resolution, and cite the page used for each screen. |
| PNG, JPEG, WebP, HEIC, SVG, or screenshot | Inspect the original-resolution image, dimensions, crop, visible states, typography, assets, and platform chrome. |
| Website URL | Use a browser to inspect responsive states, DOM, computed styles, assets, motion, and interaction when accessible; use screenshots when implementation details are unavailable. |
| Local HTML/CSS or design-reference file | Read the file and its referenced assets; do not assume the visible entry file contains the whole system. |

Do not require a particular AI product. Use whatever equivalent filesystem, browser, Figma, PDF, and image-inspection tools the current client exposes.

## Workflow

1. Read the applicable `AGENTS.md` chain, deployment targets, existing SwiftUI architecture, and design tokens.
2. Identify the exact reference, target screen(s), device families, supported orientations, and desired fidelity.
3. Build an evidence sheet: hierarchy, spacing rhythm, color roles, typography roles, shapes, imagery, controls, states, and motion.
4. Separate observed facts from inferred behavior. Ask only when an unresolved choice materially changes the result.
5. Reuse existing project tokens and components where they match. Otherwise create semantic tokens before screen code.
6. Use `hallmark study` to extract reusable design DNA without pixel-cloning when the reference needs deeper analysis. Use `swiftui-design` for native visual direction and anti-generic review; use `swiftui-expert-skill` for data flow, APIs, performance, accessibility, and availability gates.
7. Implement with native SwiftUI controls and platform behavior. Match appearance without copying web-only interaction patterns blindly.
8. Render the result at relevant sizes and compare it against the source using `references/fidelity-checklist.md`.
9. Run the project build/tests before claiming the implementation works.

## Fidelity Rules

- Preserve content priority, alignment, rhythm, and visual relationships before chasing individual pixel values.
- Use supplied or legally reusable assets. Do not invent logos, proprietary icons, hidden screens, or unavailable fonts.
- Convert raw colors into semantic light/dark roles; verify contrast and increased-contrast behavior.
- Map typography to Dynamic Type-compatible styles and scaled custom fonts.
- Infer responsive behavior from multiple states when available; do not treat one screenshot as proof of every breakpoint.
- Keep source attribution and distinguish exact reproduction from platform adaptation.
- Respect copyright and trademarks. Recreate user-owned or authorized designs; otherwise use the reference as inspiration and avoid redistributing protected assets.

## Deliverable

Provide the implemented SwiftUI files, any token or asset additions, a short list of evidence-based deviations, and the fresh build/test result. When only analysis is requested, provide the evidence sheet and implementation plan without editing.
