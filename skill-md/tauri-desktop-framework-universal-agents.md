---
name: tauri-desktop-framework
display_name: tauri-desktop-framework
platform: Universal Agents
category: Software engineering and app building
---

# tauri-desktop-framework - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `tauri-desktop-framework` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Build, review, debug, secure, package, and maintain Tauri desktop applications that combine a Rust backend with a web frontend. Use for Tauri 2 apps, src-tauri configuration, Rust commands, IPC validation, capabilities a

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the tauri-desktop-framework skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `tauri-desktop-framework` |
| Canonical name | `tauri-desktop-framework` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Build, review, debug, secure, package, and maintain Tauri desktop applications that combine a Rust backend with a web frontend. Use for Tauri 2 apps, src-tauri configuration, Rust commands, IPC validation, capabilities a


## Original SKILL.md

---
name: tauri-desktop-framework
description: Build, review, debug, secure, package, and maintain Tauri desktop applications that combine a Rust backend with a web frontend. Use for Tauri 2 apps, src-tauri configuration, Rust commands, IPC validation, capabilities and permissions, CSP, plugin permissions, filesystem and shell scopes, updater security, window/webview management, frontend invoke/listen patterns, packaging, cargo/npm verification, and cross-platform desktop performance/security work.
---

# Tauri Desktop Framework

## Core Principle

Treat Tauri as a security boundary between web content and native system access. Start with least privilege, validate every IPC input, and expose only the Rust commands, plugin permissions, paths, origins, and windows the app actually needs.

For Tauri app design, pair with `hallmark` and use its Tauri adapter: apply Hallmark's web visual rules to the renderer while preserving desktop window, keyboard, focus, menu, accessibility, system-theme, capability, IPC, and security conventions. This skill remains authoritative for the native boundary and build correctness.

Before writing version-sensitive Tauri code, check current docs. Prefer Tauri 2 for new apps unless the existing project is on Tauri 1.

Primary docs:

- `https://v2.tauri.app/concept/architecture/`
- `https://v2.tauri.app/security/capabilities/`
- `https://v2.tauri.app/security/permissions/`
- `https://v2.tauri.app/reference/config/`

## Inspect First

Before editing:

1. Read applicable `AGENTS.md` files.
2. Identify frontend framework and package manager.
3. Inspect `src-tauri/Cargo.toml`, `src-tauri/tauri.conf.*`, `src-tauri/capabilities/*`, `src-tauri/src/lib.rs`, and `src-tauri/src/main.rs`.
4. Inspect frontend invoke/listen code and Tauri plugin usage.
5. Preserve existing project conventions.

## Default Workflow

1. Define behavior and threat boundary.
2. Add or update tests first when practical.
3. Implement Rust command/plugin/state logic.
4. Wire frontend API calls with typed inputs/outputs.
5. Tighten capabilities, permissions, scopes, and CSP.
6. Run Rust, frontend, and Tauri verification.
7. Summarize security-sensitive choices and remaining risk.

## Load References

- Tauri v2 quick-start code and common gotchas: `references/quickstart-v2.md`.
- Security, capabilities, CSP, CVE-aware review: `references/security.md`.
- Rust commands, IPC validation, state, async, errors: `references/rust-ipc.md`.
- Frontend invoke/listen, windows, assets, environment variables: `references/frontend.md`.
- Packaging, updater, platform config, signing, release checks: `references/packaging.md`.
- Verification commands and review checklist: `references/verification.md`.

## High-Risk Defaults

- Never disable CSP without an explicit reason and safer replacement.
- Never grant broad filesystem or shell permissions.
- Never expose `TAURI_` secrets through frontend env prefixes.
- Never trust frontend-provided paths, URLs, commands, or serialized objects.
- Prefer scoped plugin permissions over blanket defaults.
- Require signed updates for production auto-updaters.
- Use safe error serialization; log internal details in Rust, return safe messages to the frontend.

## Common Project Files

```text
src-tauri/
  Cargo.toml
  tauri.conf.json
  capabilities/
    default.json
  src/
    lib.rs
    main.rs
```

Tauri also supports platform-specific config files such as `tauri.macos.conf.json`, `tauri.windows.conf.json`, and `tauri.linux.conf.json`; use them for platform-specific bundle, window, updater, or permission differences.

## Output Expectations

For implementation, provide focused edits plus verification evidence. For review, lead with security and correctness findings before style. For design, provide the command/capability/CSP shape before UI polish.
