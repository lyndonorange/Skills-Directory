---
name: swift-testing-pro
display_name: swift-testing-pro
platform: Codex
category: Software engineering and app building
---

# swift-testing-pro - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `swift-testing-pro` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Write, migrate, improve, and review Swift Testing code for Swift 6.2+ projects using modern `import Testing`, `@Test`, `@Suite`, `#expect`, `#require`, confirmations, time limits, attachments, exit tests, tags, traits, p

## How To Use It In Codex

In Codex, click the chat box, press /, choose swift-testing-pro, then write the task. Fallback prompt: Use the swift-testing-pro skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swift-testing-pro` |
| Canonical name | `swift-testing-pro` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Write, migrate, improve, and review Swift Testing code for Swift 6.2+ projects using modern `import Testing`, `@Test`, `@Suite`, `#expect`, `#require`, confirmations, time limits, attachments, exit tests, tags, traits, p


## Original SKILL.md

---
name: swift-testing-pro
description: Write, migrate, improve, and review Swift Testing code for Swift 6.2+ projects using modern `import Testing`, `@Test`, `@Suite`, `#expect`, `#require`, confirmations, time limits, attachments, exit tests, tags, traits, parameterized tests, async tests, actor isolation, and XCTest migration patterns. Use when the user asks for Swift unit or integration tests, Swift Testing best practices, XCTest-to-Swift-Testing conversion, test review findings, async test fixes, or verification that Swift test features are wired correctly. Do not use for UI tests, which still require XCTest.
---

# Swift Testing Pro

## Core Rule

Write or review only against confirmed Swift Testing surfaces. Before critiquing a file as Swift Testing code, confirm it imports `Testing` or uses Swift Testing syntax such as `@Test`, `@Suite`, `#expect`, or `#require`.

Treat the installed toolchain as authoritative. Swift Testing changes often, so check current Apple documentation or the local compiler when exact API spelling, availability, or behavior matters.

## Workflow

1. Identify the task: write new tests, improve tests, migrate XCTest, review existing tests, or debug failing/flaky tests.
2. Identify the toolchain: Swift version, Xcode version, package or Xcode project, and target type.
3. Load only the relevant reference:
   - Core conventions: `references/core-rules.md`.
   - Test quality and assertions: `references/writing-better-tests.md`.
   - Async tests and concurrency: `references/async-tests.md`.
   - Swift 6.2+ features: `references/new-features.md`.
   - XCTest migration: `references/migrating-from-xctest.md`.
4. For reviews, report only genuine issues with file, line, rule, before/after, and priority summary.
5. For implementation, edit tests directly and verify with the project test command before claiming success.

For Apple platform build or test actions, prefer XcodeBuildMCP when available. In simulator workflows, call `session_show_defaults` before the first build/run/test in the session. For Swift packages, use `swift test` unless the repo defines a more specific command.

## Defaults

- Prefer Swift Testing for new unit and integration tests.
- Keep XCTest for UI tests and any legacy framework feature Swift Testing cannot cover.
- Prefer `struct` suites over XCTest-style classes.
- Use `init` and `deinit` for per-test setup and cleanup.
- Use `#expect` for normal assertions.
- Use `#require` only for preconditions where the test cannot continue.
- Put the expression directly inside `#expect` where possible so diagnostics preserve context.
- Use dependency injection and mocks instead of live network, clock, filesystem, or database dependencies.
- Assume tests may run in parallel unless explicitly serialized.

## Review Output

When reviewing, organize findings by file. For each issue:

- State file and relevant line.
- Name the violated rule.
- Show a brief before/after fix.
- Skip files with no issues.
- End with a prioritized summary of the most impactful fixes.

## Write Or Improve Tests

When writing tests:

- Prefer small tests with descriptive names.
- Cover success, failure, boundary, and regression paths relevant to the change.
- Use parameterized tests when they reduce repetition without hiding intent.
- Avoid mirroring production logic to compute expected values.
- Add async confirmations or continuations based on the API shape.
- Record attachments only when they materially improve diagnosis.
- Run the relevant test command before saying the tests pass.
