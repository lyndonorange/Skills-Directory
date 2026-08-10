---
name: base
display_name: base
platform: Universal Agents
category: General and specialized workflows
---

# base - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `base` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal integration guide for Christopher Kahler's BASE, the Builder's Automated State Engine and knowledge-graph layer in the PAUL/CARL ecosystem. Use when the user explicitly invokes BASE in this ecosystem; asks for

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the base skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `base` |
| Canonical name | `base` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Universal integration guide for Christopher Kahler's BASE, the Builder's Automated State Engine and knowledge-graph layer in the PAUL/CARL ecosystem. Use when the user explicitly invokes BASE in this ecosystem; asks for


## Original SKILL.md

---
name: base
description: Universal integration guide for Christopher Kahler's BASE, the Builder's Automated State Engine and knowledge-graph layer in the PAUL/CARL ecosystem. Use when the user explicitly invokes BASE in this ecosystem; asks for workspace health, project/task/decision graph state, AST or GraphRAG queries, drift detection, graph repair, PAUL graph synchronization, or BASE dashboard operations; or needs to distinguish the portable BASE skill from the optional Claude-hook runtime.
---

# BASE

Use BASE as the shared state and knowledge-graph layer when its local runtime is available. Keep the workflow usable without automatic Claude hooks.

## Runtime Boundary

1. Check `command -v base` and `base --version` before claiming the runtime is installed.
2. If the binary is absent, use this skill only as an integration guide. Do not call another tool “BASE.”
3. The inspected source checkout is present at `[local home]/.local/share/agent-tools/chris-ai-systems/base` for review.
4. Do not build, activate, update, install, or wire hooks without explicit authorization. Upstream install changes `~/.local/bin`, `~/.base-gbl`, Claude settings hooks, and Claude instructions.
5. Automatic hook injection is Claude-specific. Codex, OpenCode, Cursor, Kiro, Windsurf, Hermes, and other hosts can use the CLI manually if installed, but must not claim hook parity.

## Safe Preflight

When BASE is installed:

```bash
base --version
base doctor --json
```

Inspect health before any graph mutation. Never hand-edit the N-Quads graph. Repair, restore, compact, or purge only after showing the target and preserving the upstream snapshot behavior.

## Route the Request

| Need | BASE route |
|---|---|
| Workspace initialization | `base scaffold` after user authorizes project files |
| Code structure | AST sync and query |
| Project delivery state | projects, milestones, and tasks |
| Durable rationale | decisions and notes |
| Rule relevance | domains and rules; CARL remains the portable JIT rule layer |
| Context query | graph or GraphRAG query |
| Health or corruption | doctor, snapshots, repair, restore, compact |
| Visual inspection | dashboard, only when the user asks to launch it |
| PAUL continuity | ingest or reconcile PAUL state through the documented integration |

Read [operations.md](references/operations.md) before running mutating commands.

## Ecosystem Responsibilities

- SEED owns idea incubation and `PLANNING.md`.
- PAUL owns approved work state and PLAN/APPLY/UNIFY.
- CARL owns intent-matched reusable rules.
- BASE owns graph-backed state, relationships, health, and retrieval when installed.
- AEGIS owns diagnostic audit and risk synthesis.
- Skillsmith owns skill design and conformance.

BASE state never grants authority and cannot replace repository instructions, PAUL approval, or fresh verification.

## References

- Read [operations.md](references/operations.md) for safe CLI use and host limitations.
- Read [upstream.md](references/upstream.md) for pinned source, license/activation facts, and current install status.
