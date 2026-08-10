---
name: swiftui-testing-expert
display_name: swiftui-testing-expert
platform: OpenCode
category: Software engineering and app building
---

# swiftui-testing-expert - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-testing-expert` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Design, implement, review, and run complete SwiftUI test strategies across Swift Testing, XCTest, XCUITest, snapshot or visual regression, previews, accessibility, async behavior, and multiple appearance or text-size con

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the swiftui-testing-expert skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-testing-expert` |
| Canonical name | `swiftui-testing-expert` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Design, implement, review, and run complete SwiftUI test strategies across Swift Testing, XCTest, XCUITest, snapshot or visual regression, previews, accessibility, async behavior, and multiple appearance or text-size con


## Original SKILL.md

---
name: swiftui-testing-expert
description: Design, implement, review, and run complete SwiftUI test strategies across Swift Testing, XCTest, XCUITest, snapshot or visual regression, previews, accessibility, async behavior, and multiple appearance or text-size configurations. Use for SwiftUI unit, integration, UI, snapshot, regression, or concurrency tests in Codex, OpenCode, and other Agent Skills clients. Pair with swift-testing-pro for detailed Swift Testing syntax.
---

# SwiftUI Testing Expert

Select the framework by test surface rather than forcing one framework everywhere.

## Test Surface Router

| Surface | Default |
|---|---|
| Pure models, reducers, formatters, and integration logic | Swift Testing when supported |
| Existing XCTest suites or XCTest-only APIs | XCTest |
| End-to-end UI flows and system interaction | XCUITest |
| Pixel-sensitive components and appearance matrices | Existing snapshot framework or project-approved visual harness |
| Layout exploration during development | SwiftUI previews, never as the only regression evidence |

Use `swift-testing-pro` for current `@Test`, `@Suite`, `#expect`, async, traits, parameterization, and XCTest-migration details.

## Workflow

1. Read the project contract and identify the toolchain, targets, schemes, current test frameworks, and existing helpers.
2. Define the behavior or regression being protected before writing the test.
3. Choose the lowest-cost test surface that can prove the behavior.
4. Make dependencies deterministic: inject clocks, networking, persistence, randomness, and environment values.
5. For UI tests, add stable accessibility identifiers and wait on observable state rather than sleeping.
6. For snapshots, use the project’s existing library; do not add one without approval. Cover relevant light/dark, Dynamic Type, locale, size class, and contrast variants without creating an unmaintainable matrix.
7. Run the narrow test first, then the relevant suite. Read fresh output before reporting success.

## Quality Rules

- Test behavior, not view-tree implementation details.
- Avoid `@unchecked Sendable` in test doubles unless the concurrency contract is understood and justified.
- Verify cancellation and error paths explicitly for async work.
- Keep launch arguments and test-only dependency overrides centralized.
- Use `waitForExistence`, predicates, or confirmations instead of fixed delays.
- Record screenshots or attachments when they improve failure diagnosis.
- Treat flaky tests as defects; identify the uncontrolled dependency instead of increasing timeouts blindly.

## Review Output

Report genuine issues by file and line, explain the failure mode, show the smallest correction, and name the verification command. Do not criticize Swift Testing syntax in files that do not import `Testing` or use its APIs.

## Source

Adapted for Codex, OpenCode, and universal Agent Skills from `swiftui-testing` in [fusengine/agents](https://github.com/fusengine/agents/tree/5841f809241ce4de317e7d7c3d93558fa3b08205/plugins/swift-apple-expert/skills/swiftui-testing). Preserve the included MIT license.
