---
name: ios-development-expert
display_name: ios-development-expert
platform: Codex
category: General and specialized workflows
---

# ios-development-expert - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `ios-development-expert` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Build, run, test, debug, automate, and validate iPhone and iPad applications using the available Xcode toolchain, XcodeBuildMCP when present, and safe command-line fallbacks. Use for simulator or physical-device workflow

## How To Use It In Codex

In Codex, click the chat box, press /, choose ios-development-expert, then write the task. Fallback prompt: Use the ios-development-expert skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `ios-development-expert` |
| Canonical name | `ios-development-expert` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Build, run, test, debug, automate, and validate iPhone and iPad applications using the available Xcode toolchain, XcodeBuildMCP when present, and safe command-line fallbacks. Use for simulator or physical-device workflow


## Original SKILL.md

---
name: ios-development-expert
description: Build, run, test, debug, automate, and validate iPhone and iPad applications using the available Xcode toolchain, XcodeBuildMCP when present, and safe command-line fallbacks. Use for simulator or physical-device workflows, Xcode project discovery, UI automation, LLDB debugging, screenshots, logs, UIKit-to-SwiftUI bridges, and end-to-end iOS implementation in Codex, OpenCode, or another Agent Skills client.
---

# iOS Development Expert

Use the project contract and installed toolchain as the authority. Do not assume a specific agent harness, model, subagent framework, iOS version, Xcode version, simulator, scheme, or MCP tool prefix.

## Workflow

1. Read the applicable `AGENTS.md` chain and inspect the repository before editing.
2. Discover `.xcworkspace`, `.xcodeproj`, `Package.swift`, schemes, configurations, deployment targets, and existing verification commands.
3. Choose the smallest relevant path: simulator, device, UI automation, debugging, or UIKit interop.
4. Prefer XcodeBuildMCP when it is available. Discover its current tool names and parameters instead of assuming names from these references.
5. Fall back to `xcodebuild`, `xcrun simctl`, `xcrun devicectl`, `lldb`, and project scripts when MCP tooling is unavailable.
6. Make the smallest safe change, then run a fresh build or test command and inspect the real output before claiming success.

Do not require delegation. Use additional agents only when the user or applicable project instructions request them and the task can be split safely.

## Topic Router

- Simulator build, boot, launch, logs, tests, screenshots, and recording: `references/simulator-tools.md`.
- Physical-device discovery, build, install, launch, tests, and logs: `references/device-tools.md`.
- Accessibility-first UI interaction and screenshots: `references/ui-automation.md`.
- LLDB attachment, breakpoints, stacks, variables, and crash investigation: `references/debugging.md`.
- UIKit or view-controller integration inside SwiftUI: `references/uikit-integration.md`.

Treat capability names in the references as conceptual XcodeBuildMCP operations. Map them to the tools actually exposed in the current client.

## Safety

- Ask before installing optional utilities, changing signing identities, provisioning profiles, entitlements, or device trust settings.
- Never erase simulators, reset devices, delete derived data broadly, or change signing configuration without explicit need and scoped approval.
- Do not type secrets or personal data through UI automation.
- Prefer accessibility identifiers and element inspection over hard-coded coordinates.
- Keep simulator and device identifiers opaque; read them from current tool output.
- Preserve the user’s active simulator/device state unless the task requires changing it.

## Verification

- Match verification to the change: build, unit tests, UI tests, launch check, log inspection, screenshot, or device validation.
- Test the oldest supported OS when compatibility is material.
- Distinguish simulator evidence from physical-device evidence.
- Report the exact destination, scheme, and command/tool used.

## Source

Adapted for Codex, OpenCode, and universal Agent Skills from the `ios` skill in [fusengine/agents](https://github.com/fusengine/agents/tree/7cadb2ca7b133f61c9c694c8a96556eb87c1e003/plugins/swift-apple-expert/skills/ios). Preserve the included MIT license.
