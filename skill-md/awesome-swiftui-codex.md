---
name: awesome-swiftui
display_name: awesome-swiftui
platform: Codex
category: General and specialized workflows
---

# awesome-swiftui - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `awesome-swiftui` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Search, shortlist, and vet SwiftUI learning resources, libraries, UI components, and open-source applications using onmyway133/awesome-swiftui as a discovery catalog. Use when a user asks for a SwiftUI library, component

## How To Use It In Codex

In Codex, click the chat box, press /, choose awesome-swiftui, then write the task. Fallback prompt: Use the awesome-swiftui skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `awesome-swiftui` |
| Canonical name | `awesome-swiftui` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Search, shortlist, and vet SwiftUI learning resources, libraries, UI components, and open-source applications using onmyway133/awesome-swiftui as a discovery catalog. Use when a user asks for a SwiftUI library, component


## Original SKILL.md

---
name: awesome-swiftui
description: Search, shortlist, and vet SwiftUI learning resources, libraries, UI components, and open-source applications using onmyway133/awesome-swiftui as a discovery catalog. Use when a user asks for a SwiftUI library, component, example app, tutorial, animation, layout, image loader, inspection tool, or implementation reference. Prefer current native SwiftUI APIs when they meet the need; do not recommend a dependency without maintenance, license, platform, and deployment-target checks.
---

# Awesome SwiftUI

Use the upstream list to discover candidates, then verify them against the current project and current ecosystem before recommending or integrating anything.

## Step 0 — Sufficiency Check

Confirm the requested capability, target platforms, minimum OS versions, package-manager constraints, and whether third-party dependencies are acceptable. If some details are missing but a useful shortlist is possible, state the assumption briefly and proceed. Ask at most three questions only when the missing details would make the shortlist structurally wrong.

## Workflow

1. Read the applicable `AGENTS.md` chain, package manifest, deployment targets, and nearby code.
2. Search the catalog with `scripts/search_catalog.sh` using the mapping below.
3. Prefer Apple documentation and native SwiftUI when current platform APIs cover the requirement.
4. For each remaining candidate, verify its repository live: license, latest meaningful activity, supported platforms, minimum Swift/OS versions, installation method, open maintenance issues, and API fit.
5. Compare no more than five candidates using `references/evaluation-rubric.md`.
6. Recommend one option, explain the tradeoff, and provide a native or no-dependency fallback when practical.
7. Integrate only when the user asked for code changes; run the project's build and tests afterward.

## Workflow Routing

| Intent | Script invocation |
|---|---|
| Browse catalog sections | `scripts/search_catalog.sh --list-sections` |
| Find a capability | `scripts/search_catalog.sh --query "<terms>"` |
| Inspect one category | `scripts/search_catalog.sh --section "<heading>"` |
| Search a local snapshot | Add `--source <README.md>` |

## Gotchas

- The catalog includes early SwiftUI material and libraries that predate current native APIs; catalog inclusion is not a quality or freshness guarantee.
- A repository can be active yet incompatible with the project's deployment target, Swift language mode, accessibility needs, or package policy.
- Linked projects have their own licenses. The catalog's MIT license does not relicense third-party code.
- Avoid adding packages for small effects that modern SwiftUI implements directly.
- Verify exact product and repository URLs before presenting them; similarly named libraries are common.

## Examples

- “Find a maintained SwiftUI image-loading library” → search Image, compare native `AsyncImage` plus maintained packages, verify licenses and platform support.
- “Show me open-source SwiftUI macOS apps” → inspect the macOS section, verify current repositories, return a focused learning shortlist.
- “I need a custom grid” → check modern `Grid`, `LazyVGrid`, and `Layout` first, then vet third-party grids only for unmet requirements.

## References

- Read `references/evaluation-rubric.md` before recommending a dependency.
- Upstream source: [onmyway133/awesome-swiftui](https://github.com/onmyway133/awesome-swiftui), MIT licensed.
