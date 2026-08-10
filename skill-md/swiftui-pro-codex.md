---
name: swiftui-pro
display_name: swiftui-pro
platform: Codex
category: Software engineering and app building
---

# swiftui-pro - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-pro` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Review SwiftUI and Swift code for correctness, modern API usage, accessibility compliance, performance, data flow, navigation, design patterns, Swift 6.2 concurrency, and code hygiene against iOS 26+ expectations. Use fo

## How To Use It In Codex

In Codex, click the chat box, press /, choose swiftui-pro, then write the task. Fallback prompt: Use the swiftui-pro skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-pro` |
| Canonical name | `swiftui-pro` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Review SwiftUI and Swift code for correctness, modern API usage, accessibility compliance, performance, data flow, navigation, design patterns, Swift 6.2 concurrency, and code hygiene against iOS 26+ expectations. Use fo


## Original SKILL.md

---
name: swiftui-pro
description: Review SwiftUI and Swift code for correctness, modern API usage, accessibility compliance, performance, data flow, navigation, design patterns, Swift 6.2 concurrency, and code hygiene against iOS 26+ expectations. Use for SwiftUI code reviews, PR reviews, audits, deprecated API checks, accessibility and Dynamic Type validation, VoiceOver issues, Reduce Motion problems, performance pitfalls, state/property-wrapper bugs, NavigationStack or NavigationSplitView problems, Swift concurrency issues, and before/after fix recommendations organized by file and priority. Report only genuine problems; do not nitpick or invent issues.
---

# SwiftUI Pro

## Review Posture

Review Swift and SwiftUI code for correctness, modern API usage, accessibility, performance, and project convention fit. Report only genuine issues with user impact, correctness risk, maintainability cost, or measurable performance concern.

Assume iOS 26 is the default deployment target for new apps unless project files say otherwise. Target Swift 6.2 or later and modern Swift concurrency. Prefer SwiftUI over UIKit/AppKit bridging unless the user or codebase requires bridging. Do not introduce third-party frameworks without asking.

For Apple platform build/run/test actions, prefer XcodeBuildMCP when available. In simulator workflows, call `session_show_defaults` before the first build/run/test unless already done in the current session.

## Review Process

Load only the reference files relevant to the review scope:

1. Deprecated and modern APIs: `references/api.md`.
2. Views, modifiers, composition, and animations: `references/views.md`.
3. Data flow, property wrappers, shared state, and bindings: `references/data.md`.
4. Navigation, sheets, alerts, confirmation dialogs, and presentation: `references/navigation.md`.
5. Human Interface Guidelines and design behavior: `references/design.md`.
6. Dynamic Type, VoiceOver, Reduce Motion, and accessibility: `references/accessibility.md`.
7. Runtime and SwiftUI rendering performance: `references/performance.md`.
8. Modern Swift, Swift 6.2, and concurrency: `references/swift.md`.
9. Compile cleanliness, file organization, and maintainability: `references/hygiene.md`.

If doing a partial review, load only the matching references. If a file has no issues, omit it from the findings.

## Hard Rules

- Do not invent issues to fill a quota.
- Do not report style preferences unless they hide a real bug or project convention violation.
- Do not recommend UIKit/AppKit bridging when native SwiftUI solves the problem.
- Do not suggest third-party frameworks without explicit user approval.
- Do not require one architecture pattern across the project.
- Prefer one primary type per Swift file unless the codebase has a local convention for small helper types.
- Keep folder layout feature-oriented when proposing new files.
- Treat accessibility failures as correctness issues, not polish.
- Use `#available` for APIs newer than the deployment target.

## Output Format

Organize findings by file. For each issue:

- State file and relevant line or tight line range.
- Name the violated rule.
- Explain why it matters in one sentence.
- Show a brief before/after code fix when the fix is clear.

Use this shape:

```markdown
ContentView.swift

Line 12: Use `foregroundStyle()` instead of `foregroundColor()`.

Why: `foregroundStyle()` is the modern SwiftUI styling API and composes better with hierarchical styles.

```swift
// Before
Text("Hello").foregroundColor(.red)

// After
Text("Hello").foregroundStyle(.red)
```
```

End with a prioritized summary:

```markdown
Summary
- Accessibility (high): The icon-only add button has no VoiceOver label.
- Data flow (medium): Manual binding in the view body performs side effects during editing.
- Deprecated API (low): `foregroundColor()` should move to `foregroundStyle()`.
```

If there are no findings, say that no genuine issues were found and mention any review scope limits.

## Verification

When edits are requested, run the project's relevant verification before claiming completion. Common commands include `swift test`, `xcodebuild build`, `xcodebuild test`, SwiftLint, or the repository's documented checks. Report commands actually run and their result.
