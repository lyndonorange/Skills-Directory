---
name: swiftui-master
display_name: swiftui-master
platform: Codex
category: Software engineering and app building
---

# swiftui-master - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-master` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Teach, design, implement, review, and verify modern SwiftUI app architecture using current Apple documentation, Observation with @Observable, @State, @Binding, @Bindable, @Environment, type-safe NavigationStack and Navig

## How To Use It In Codex

In Codex, click the chat box, press /, choose swiftui-master, then write the task. Fallback prompt: Use the swiftui-master skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-master` |
| Canonical name | `swiftui-master` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Teach, design, implement, review, and verify modern SwiftUI app architecture using current Apple documentation, Observation with @Observable, @State, @Binding, @Bindable, @Environment, type-safe NavigationStack and Navig


## Original SKILL.md

---
name: swiftui-master
description: Teach, design, implement, review, and verify modern SwiftUI app architecture using current Apple documentation, Observation with @Observable, @State, @Binding, @Bindable, @Environment, type-safe NavigationStack and NavigationPath routing, dependency injection, previews, lazy containers, performance tuning, Sendable-aware async work, and setup checks. Use when the user wants SwiftUI explanations, setup guidance, code examples, feature implementation, state-management decisions, navigation architecture, router patterns, dependency injection, migration from ObservableObject or @Published, or verification that SwiftUI features are wired correctly.
---

# SwiftUI Master

## Core Rule

Ground version-sensitive API details in current Apple documentation before giving final guidance. Start with `references/apple-docs-router.md` whenever the task asks about an API, framework feature, setup, availability, or "what should I use now?"

This skill is both a builder and a tutor: explain when to use a pattern, how to set it up, how the code works, and how to verify that it is connected correctly.

## Workflow

1. Identify the platform, deployment target, Xcode/SDK version, and whether this is new code, migration, review, or debugging.
2. Read the smallest relevant reference:
   - Apple docs routing and current API lookup: `references/apple-docs-router.md`.
   - Observation and state wrappers: `references/state-observation.md`.
   - NavigationStack, NavigationPath, and router pattern: `references/navigation-router.md`.
   - Dependency injection and app structure: `references/architecture-di.md`.
   - Rendering and list performance: `references/performance.md`.
   - Setup, previews, tests, and verification: `references/setup-verification.md`.
3. Explain the decision in plain terms before or alongside code.
4. Implement with modern SwiftUI defaults, unless the project's deployment target requires legacy APIs.
5. Check that the feature is wired correctly: ownership, bindings, environment injection, navigation destinations, async work, previews, and verification commands.

For Apple platform build/run/test actions, prefer XcodeBuildMCP when available. In simulator workflows, call `session_show_defaults` before the first build/run/test unless already done in the current session.

## Modern Defaults

- Prefer `@Observable` over new `ObservableObject` / `@Published` models when deployment targets support Observation.
- Use `@State` for view-owned values and owned observable models.
- Use `@Binding` when a child edits parent-owned state.
- Use `@Bindable` when a view needs bindings into an injected observable model.
- Use `@Environment` for shared dependencies injected with `.environment(...)`.
- Use `NavigationStack` with typed destinations for drill-down flows.
- Use `NavigationPath` or an observable router when navigation must be programmatic or restored.
- Use lazy containers for large collections.
- Keep expensive work out of `body`.
- Use `.task {}` or explicit async methods for async work, not `body` or initializers.

## State Decision Table

| Need | Prefer | Check |
|------|--------|-------|
| Local value state | `@State` | Private and owned by the view |
| Child edits parent value | `@Binding` | Parent remains source of truth |
| Owned observable model | `@State private var model` | Initialized once, usually in `init` for dependency injection |
| Injected observable model, read-only | Plain property or `@Environment` | No unnecessary wrapper |
| Injected observable model, editable bindings | `@Bindable` | Used where `$model.property` is needed |
| Shared app dependency | `@Environment(Type.self)` | Injected at a parent with `.environment(instance)` |

## Tutor Output

When teaching a pattern, include:

- When to use it.
- When not to use it.
- Setup steps.
- A minimal code example.
- How the code works.
- How to verify it is wired correctly.
- Migration notes if the old pattern differs.

## Implementation Checks

Before finishing SwiftUI work, check:

- State owner is correct and not duplicated.
- Bindings only flow to children that edit parent state.
- `@Observable` models are injected or owned intentionally.
- Environment dependencies are provided above every consumer.
- Navigation destinations cover every typed route.
- `ForEach` uses stable identity.
- Async work runs from `.task`, explicit actions, or model methods.
- Previews use self-contained mock data.
- Build/test commands were run before success claims.
