---
name: swiftui-expert-skill
display_name: swiftui-expert-skill
platform: Codex
category: Software engineering and app building
---

# swiftui-expert-skill - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-expert-skill` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Write, review, refactor, and improve SwiftUI code using modern Apple patterns for state management, view composition, accessibility, animation, navigation, lists, layout, performance, previews, localization, Charts, macO

## How To Use It In Codex

In Codex, click the chat box, press /, choose swiftui-expert-skill, then write the task. Fallback prompt: Use the swiftui-expert-skill skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-expert-skill` |
| Canonical name | `swiftui-expert-skill` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Write, review, refactor, and improve SwiftUI code using modern Apple patterns for state management, view composition, accessibility, animation, navigation, lists, layout, performance, previews, localization, Charts, macO


## Original SKILL.md

---
name: swiftui-expert-skill
description: Write, review, refactor, and improve SwiftUI code using modern Apple patterns for state management, view composition, accessibility, animation, navigation, lists, layout, performance, previews, localization, Charts, macOS scenes, and version-gated APIs including iOS 26+ Liquid Glass when explicitly requested. Use for SwiftUI feature implementation, SwiftUI code review, deprecated API replacement, performance tuning, Instruments trace interpretation, view extraction, @Observable migration, ForEach identity bugs, accessibility fixes, and safe adoption of current SwiftUI APIs with #available fallbacks.
---

# SwiftUI Expert Skill

## Operating Rules

Read `references/latest-apis.md` at the start of every SwiftUI task to avoid deprecated or version-sensitive APIs.

Prefer native SwiftUI APIs over UIKit/AppKit bridging unless bridging is necessary. Focus on correctness, maintainability, accessibility, and performance. Do not force a named architecture such as MVVM or VIPER; do separate business logic from views when it improves testability.

Only adopt Liquid Glass or iOS 26+ visual effects when the user explicitly asks for them or the existing code already uses them. Gate version-specific APIs with `#available` and provide sensible fallbacks.

For Apple platform build/run/test actions, prefer XcodeBuildMCP when available. In simulator workflows, call `session_show_defaults` before the first build/run/test unless already done in the current session.

## Workflow

For review or refactor:

1. Read the target SwiftUI files and identify relevant topics.
2. Read `references/latest-apis.md`.
3. Load the smallest topic references from the router below.
4. Flag correctness bugs before style or architecture suggestions.
5. Validate availability gates, fallbacks, accessibility, and preview behavior.
6. Edit only when the user asked for edits; otherwise report findings and recommendations.

For new features:

1. Identify owned state, injected state, bindings, environment, and observable models.
2. Design the data flow before writing view code.
3. Extract complex subviews early enough to keep diffing and compile times healthy.
4. Use `Button` or platform controls for tappable UI.
5. Add accessibility labels, values, grouping, and Dynamic Type behavior as needed.
6. Gate modern APIs and keep fallbacks aligned with deployment targets.
7. Run the project verification command before claiming success.

For trace-driven work:

1. If the user asks to record a trace, clarify target app/device when missing.
2. If a `.trace` file is provided, inspect the trace using available local tooling or Xcode Instruments exports.
3. Connect hot views, update causes, hangs, and animation hitches back to source symbols.
4. Return prioritized recommendations; edit code only when asked.

## Topic Router

Read the matching reference file when the topic applies:

- State management and observation: `references/state-management.md`.
- View structure, extraction, and composition: `references/view-structure.md`.
- Performance and trace interpretation: `references/performance-patterns.md`.
- Lists, `ForEach`, row identity, and filtering: `references/list-patterns.md`.
- Layout, navigation, sheets, scrolling, focus, text, localization, previews, accessibility, animations, Charts, and macOS: `references/ui-patterns.md`.
- Liquid Glass and iOS 26+ visual effects: `references/liquid-glass.md`.
- Deprecated, soft-deprecated, and version-specific APIs: `references/latest-apis.md`.

## Correctness Checklist

Treat these as bugs unless the project has a documented reason:

- `@State` properties are private.
- Use `@Binding` only where a child modifies parent-owned state.
- Do not declare passed-in values as `@State` or `@StateObject`.
- Use `@StateObject` for view-owned observable objects and `@ObservedObject` for injected objects in legacy observable-object code.
- On iOS 17+, prefer `@Observable` models with `@State` for owned instances and `@Bindable` for injected models that need bindings.
- `ForEach` uses stable identity that outlives the view and is not derived from mutable display content.
- Avoid `.indices`, `\.offset`, and unstable IDs for editable or reorderable collections.
- Keep a constant number of views per `ForEach` element; `List` rows should be unary.
- Do not store closures in custom `@Environment` or `@FocusedValue` keys.
- Custom `@Entry` default values are stable; avoid inline `Date()`, `UUID()`, or model construction.
- `.animation(_:value:)` includes the `value` parameter.
- `@FocusState` properties are private.
- Avoid redundant `@FocusState` writes inside tap gesture handlers on `.focusable()` views.
- iOS 26+ APIs have `#available` gates and fallbacks.
- Files using Swift Charts import `Charts`.
- Previews use self-contained mock data and do not depend on live services or network.

## Output Style

For reviews, lead with prioritized findings and cite file/line evidence when available. For implementations, explain the data flow, availability strategy, verification run, and any residual risk. For performance work, label suggestions separately from required correctness fixes.
