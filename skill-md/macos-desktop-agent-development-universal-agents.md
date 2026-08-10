---
name: macos-desktop-agent-development
display_name: macos-desktop-agent-development
platform: Universal Agents
category: General and specialized workflows
---

# macos-desktop-agent-development - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `macos-desktop-agent-development` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Design, implement, review, and secure Swift-based macOS desktop agents that observe or control applications through Accessibility APIs, AppKit, process discovery, event monitoring, and authenticated local IPC. Use for wo

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the macos-desktop-agent-development skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `macos-desktop-agent-development` |
| Canonical name | `macos-desktop-agent-development` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Design, implement, review, and secure Swift-based macOS desktop agents that observe or control applications through Accessibility APIs, AppKit, process discovery, event monitoring, and authenticated local IPC. Use for wo


## Original SKILL.md

---
name: macos-desktop-agent-development
description: Design, implement, review, and secure Swift-based macOS desktop agents that observe or control applications through Accessibility APIs, AppKit, process discovery, event monitoring, and authenticated local IPC. Use for workflow automation, assistive tools, desktop monitors, UI element discovery, AX permission handling, or agent-to-orchestrator communication in Codex, OpenCode, and other Agent Skills clients.
---

# macOS Desktop Agent Development

Treat Accessibility access as a powerful user-granted capability. Build transparent, narrowly scoped tools with explicit ownership and visible failure modes.

## Architecture

Separate these responsibilities:

- `PermissionController`: check trust and explain how the user grants or revokes access.
- `ApplicationLocator`: resolve a configured bundle identifier to a running process.
- `AXClient`: typed reads, writes, actions, timeouts, and `AXError` mapping.
- `ElementQuery`: bounded traversal with role, identifier, title, subrole, and ancestry predicates.
- `Observer`: `AXObserver` notifications with polling only as a measured fallback.
- `Policy`: allowlisted applications, operations, fields, and data classes.
- `IPC`: authenticated, versioned request/response messages with size limits and cancellation.
- `AuditLog`: privacy-filtered operational events without captured user content.

Keep observed state separate from runtime handles so behavior can be tested without controlling a live app.

## Workflow

1. Read the project contract, entitlements, sandbox model, deployment target, and threat boundaries.
2. Define the exact application, elements, reads, writes, and actions in scope.
3. Start read-only. Add mutation only when the user explicitly needs it.
4. Request Accessibility permission through the system prompt; never bypass or conceal permission requirements.
5. Inspect real AX trees and record stable selectors. Prefer identifiers and semantic roles over child indexes or screen coordinates.
6. Use notifications for changes; if polling is required, bound frequency, traversal depth, memory, and retry behavior.
7. Validate every IPC message at the trust boundary and return structured errors.
8. Test the query and policy layers with synthetic trees, then perform an approval-gated live check against the intended app.

## Accessibility Boundaries

- Check trust with `AXIsProcessTrustedWithOptions`; keep permission prompting separate from background monitoring.
- Never read or write secure text fields, password managers, authentication dialogs, payment screens, or private data unless the user explicitly defines a legitimate accessible workflow.
- Do not capture whole UI trees when a narrow query is sufficient.
- Do not automate destructive actions without a visible confirmation or user-approved policy.
- Stop cleanly when the target app exits, permission is revoked, or AX calls repeatedly time out.
- Avoid app-specific assumptions in generic modules; isolate selectors and adapters per target application.

## IPC Boundaries

- Prefer a local Unix-domain socket or XPC when practical; restrict filesystem permissions.
- Authenticate clients, version the protocol, cap message sizes, validate enums and paths, and reject unknown commands.
- Separate read, write, and destructive capabilities.
- Never expose an unauthenticated network listener for Accessibility control.
- Redact UI content, tokens, paths, and personal data from logs.

## Verification

- Build with the project’s existing SwiftPM or Xcode command.
- Test permission-denied, target-not-running, unsupported attribute, stale element, timeout, malformed IPC, cancellation, and clean shutdown paths.
- Run static analysis and concurrency checks appropriate to the toolchain.
- For live automation, report the target bundle identifier, granted capability, exact action, and observed result.

## Source

Adapted and security-hardened for universal Agent Skills from `macos-agent-development` in [cacr92/wereply](https://github.com/cacr92/wereply/tree/6a2debd152a2a8850bdb14c09a678e0c9ae5c792/.codex/skills/macos-agent-development). Preserve the included MIT license.
