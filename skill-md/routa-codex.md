---
name: routa
display_name: routa
platform: Codex
category: General and specialized workflows
---

# routa - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `routa` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use when Codex should use or coordinate with Routa, the workspace-first multi-agent coordination platform across ACP, MCP, A2A, and AG-UI: installing or verifying `routa-cli` or Routa Desktop, running terminal-first repo

## How To Use It In Codex

In Codex, click the chat box, press /, choose routa, then write the task. Fallback prompt: Use the routa skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `routa` |
| Canonical name | `routa` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use when Codex should use or coordinate with Routa, the workspace-first multi-agent coordination platform across ACP, MCP, A2A, and AG-UI: installing or verifying `routa-cli` or Routa Desktop, running terminal-first repo


## Original SKILL.md

---
name: routa
description: "Use when Codex should use or coordinate with Routa, the workspace-first multi-agent coordination platform across ACP, MCP, A2A, and AG-UI: installing or verifying `routa-cli` or Routa Desktop, running terminal-first repository prompts, inspecting ACP/runtime status, planning Sessions/Kanban/Team workflows, attaching repositories to Routa workspaces, or documenting how Routa fits into a local app-building workflow."
---

# Routa

## Overview

Routa is a workspace-first multi-agent coordination layer for real software work. It keeps agent work attached to product objects such as sessions, boards, specialists, teams, and codebases instead of treating everything as one long chat.

Read `references/upstream.md` when you need the installed versions, source links, install commands, or first-run checklist.

## Choose The Surface

- Use Routa CLI for terminal-first repository prompts, quick architecture reads, refactor planning, automation scripts, runtime inspection, and one-shot coordination from a repo root.
- Use Routa Desktop when the user wants the full local UI: workspaces, provider management, repository attachment, Session, Kanban, and Team flows.
- Use Routa Web/self-hosting only when the user explicitly wants a browser-hosted or internal deployment path.

## CLI Workflow

1. Verify the binary with `routa --version` and `routa --help`.
2. Run Routa from the target repository root when a prompt depends on codebase context.
3. Start with read-only prompts such as `routa -p "Explain the architecture of this repository"` or `routa -p "Plan the next refactor for this codebase"`.
4. Inspect local runtime support with `routa acp runtime-status` before deeper provider work.
5. Use Routa output as planning or coordination context, then apply local DOX instructions and normal verification before editing files.

## Desktop Workflow

1. Verify `/Applications/Routa Desktop.app` exists and reports the expected version in `Contents/Info.plist`.
2. Launch Routa Desktop when the user wants workspace creation, provider setup, repository attachment, or visual Session/Kanban/Team coordination.
3. Follow the upstream first-run order: create a workspace, configure at least one provider, attach a repository, start with a Session, then move to Kanban when decomposition and lane automation are useful.
4. Treat the desktop app as a coordination surface. Keep durable project rules in `AGENTS.md` and verify any code changes with the repo's own checks.

## Guardrails

- Prefer read-only and status commands before agentic, mutating, or delegated workflows.
- Do not put secrets, API keys, tokens, or private credentials into Routa prompts.
- Ask before changing provider configuration, self-hosting Routa, or running workflows that may edit files, create branches, open pull requests, or start long-running agents.
- If Routa suggests changes, implement them through the normal local workflow unless the user explicitly asks Routa to execute.
- Record durable workflow changes in the relevant `AGENTS.md` and regenerate any generated skill directory when Routa skill metadata changes.
