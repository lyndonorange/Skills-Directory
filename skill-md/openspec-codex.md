---
name: openspec
display_name: openspec
platform: Codex
category: Software engineering and app building
---

# openspec - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `openspec` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

OpenSpec is a spec-driven development system and CLI for turning feature ideas into durable specs, change proposals, tasks, validation, and archived product history.

## How To Use It In Codex

In Codex, click the chat box, press /, choose openspec, then write the task. Fallback prompt: Use the openspec skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `openspec` |
| Canonical name | `openspec` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

OpenSpec is a spec-driven development system and CLI for turning feature ideas into durable specs, change proposals, tasks, validation, and archived product history.

## Original SKILL.md

---
name: openspec
description: "Use when doing spec-driven development with OpenSpec: initializing specs, creating change proposals, writing tasks, validating specs, viewing status, or archiving completed changes."
---

# OpenSpec

OpenSpec is a spec-driven development system and CLI for turning feature ideas into durable specs, change proposals, tasks, validation, and archived product history.

## Installed Tooling

- CLI: `/opt/homebrew/bin/openspec`
- Global package: `@fission-ai/openspec@1.2.0`

## When To Use

Use OpenSpec when a change needs a formal proposal, implementation tasks, validation, and a stable spec trail. It is best for durable product or architecture changes, not for tiny one-off edits.

## Common Commands

```bash
openspec init
openspec list
openspec new
openspec change
openspec show <item-name>
openspec validate <item-name>
openspec status <change-name>
openspec archive <change-name>
openspec instructions
```

## App Program Fit

- Mode: Planning and Building.
- Stages: Product Definition, Architecture, Product Build, QA and Review, Release.
- Use before coding for spec proposals and tasks.
- Use during implementation to validate completion against the spec.
- Use after release to archive completed changes and update main specs.

## Working Rule

Before creating or changing OpenSpec artifacts, inspect existing specs and changes with `openspec list` and `openspec show`. Run `openspec validate` before treating a change as ready.

