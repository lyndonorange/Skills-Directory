---
name: apple-platform-build
display_name: apple-platform-build
platform: OpenCode
category: General and specialized workflows
---

# apple-platform-build - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `apple-platform-build` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Discover, build, test, launch, debug, and collect evidence for Xcode and SwiftPM projects targeting iOS, iPadOS, and macOS using available Codex/Xcode specialists or portable xcodebuild, simctl, devicectl, SwiftPM, and n

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the apple-platform-build skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `apple-platform-build` |
| Canonical name | `apple-platform-build` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Discover, build, test, launch, debug, and collect evidence for Xcode and SwiftPM projects targeting iOS, iPadOS, and macOS using available Codex/Xcode specialists or portable xcodebuild, simctl, devicectl, SwiftPM, and n


## Original SKILL.md

---
name: apple-platform-build
description: Discover, build, test, launch, debug, and collect evidence for Xcode and SwiftPM projects targeting iOS, iPadOS, and macOS using available Codex/Xcode specialists or portable xcodebuild, simctl, devicectl, SwiftPM, and native inspection fallbacks. Use when an Apple app must prove compilation, tests, launch behavior, logs, screenshots, destination coverage, or release artifact readiness across skill-capable agents without assuming one MCP server or harness.
---

# Apple Platform Build

Use the installed toolchain and repository contract as authority. Do not guess a scheme, container, destination, deployment target, signing identity, or simulator.

## Workflow

1. Read the applicable `AGENTS.md` chain and repository verification instructions.
2. Run `scripts/apple_project_info.py --root <repo>` to inventory workspaces, projects, packages, active Xcode, and available specialist skills.
3. List schemes with `xcodebuild -list -json -workspace <path>` or `-project <path>`.
4. List destinations with `xcodebuild -showdestinations -scheme <scheme> ...` and select an explicit available destination.
5. Read the matching platform reference: `references/ios-ipados.md` or `references/macos.md`.
6. Prefer a narrower installed specialist when it owns the task. Otherwise use the portable commands in the reference.
7. Run the smallest relevant build or test first, then the platform matrix required by the approved stage.
8. Capture the exact command, container, scheme, configuration, destination, exit status, timestamp, and relevant output. Do not summarize a command that was not run.

## Safety

- Ask before changing signing, entitlements, provisioning, certificates, device trust, package dependencies, or release configuration.
- Do not erase simulators, reset devices, delete broad DerivedData paths, or stop unrelated processes.
- Keep build products and logs outside source control unless the project explicitly owns them.
- Distinguish simulator, physical-device, and Mac evidence.
- Treat warnings, skipped tests, unavailable destinations, and partial matrices as visible residual risk.

## Evidence Contract

```text
VERDICT: PASS | REVISE | BLOCKED
PLATFORM:
XCODE AND SDK:
CONTAINER / SCHEME / CONFIGURATION:
DESTINATION:
COMMAND:
EXIT STATUS:
OUTPUT OR RESULT BUNDLE:
LAUNCH / SCREENSHOT / LOG EVIDENCE:
NOT VERIFIED:
RISKS:
```

Compilation alone does not prove launch behavior, interaction, accessibility, tests, performance, signing, packaging, or release readiness. Return this evidence to an independent reviewer and `apple-build-supervisor`.
