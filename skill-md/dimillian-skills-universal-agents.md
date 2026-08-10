---
name: dimillian-skills
display_name: dimillian-skills
platform: Universal Agents
category: General and specialized workflows
---

# dimillian-skills - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `dimillian-skills` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Route engineering work to focused workflows adapted from Dimillian's Skills collection: app-store changelogs, bug hunting, GitHub tasks, iOS debugging, macOS app scaffolding and packaging, batch refactors, project skill

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the dimillian-skills skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `dimillian-skills` |
| Canonical name | `dimillian-skills` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Route engineering work to focused workflows adapted from Dimillian's Skills collection: app-store changelogs, bug hunting, GitHub tasks, iOS debugging, macOS app scaffolding and packaging, batch refactors, project skill


## Original SKILL.md

---
name: dimillian-skills
description: "Route engineering work to focused workflows adapted from Dimillian's Skills collection: app-store changelogs, bug hunting, GitHub tasks, iOS debugging, macOS app scaffolding and packaging, batch refactors, project skill audits, React performance, simplification, review swarms, Swift concurrency, and SwiftUI liquid glass, performance, patterns, and refactoring. Use when the user names Dimillian Skills or asks which workflow fits one of these tasks."
---

# Dimillian Skills

Use this compact router to avoid loading overlapping specialist skills until the task needs one.

## Workflow

1. Read the applicable `AGENTS.md` chain and identify the exact task boundary.
2. Select one primary route from `references/route-map.md`.
3. Prefer an already installed local specialist with equivalent or stronger instructions.
4. Preserve read-only boundaries for audits and reviews; do not infer authorization to implement.
5. Run the route's relevant verification before claiming completion.

## Workflow Routing

| Domain | Route family |
|---|---|
| Apple platforms | iOS debugger, macOS setup/package, Swift concurrency, SwiftUI specialists |
| Review and debugging | bug hunt, review swarm, simplify changes |
| Project operations | GitHub, changelog, skill audit, batch refactor |
| Web performance | React component performance |

## Gotchas

- Several upstream skills explicitly use subagents; only delegate when the active instructions or user request authorize it.
- Many routes overlap installed curated skills. Use the most specific current local skill rather than combining duplicate instructions.
- Review routes are read-only unless the user also asks for fixes.
- Apple API guidance can drift; verify platform-sensitive details against current Apple documentation when needed.

## Examples

- “Use Dimillian Skills to debug this simulator issue” → route to the installed iOS debugger specialist.
- “Which Dimillian workflow should review this large diff?” → choose review swarm or simplification based on whether edits are authorized.

## References

- Read `references/route-map.md` for upstream-to-local mappings and provenance.
