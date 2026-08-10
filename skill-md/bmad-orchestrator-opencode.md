---
name: bmad-orchestrator
display_name: bmad-orchestrator
platform: OpenCode
category: Product, growth, marketing, and PM
---

# bmad-orchestrator - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `bmad-orchestrator` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Route projects and major initiatives through the installed BMAD Method v6 workflow set. Use when starting or resuming BMAD, choosing the next BMAD phase or skill, coordinating analysis, planning, solutioning, implementat

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the bmad-orchestrator skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `bmad-orchestrator` |
| Canonical name | `bmad-orchestrator` |
| Platform | `OpenCode` |
| Category | Product, growth, marketing, and PM |

## Description

Route projects and major initiatives through the installed BMAD Method v6 workflow set. Use when starting or resuming BMAD, choosing the next BMAD phase or skill, coordinating analysis, planning, solutioning, implementat


## Original SKILL.md

---
name: bmad-orchestrator
description: Route projects and major initiatives through the installed BMAD Method v6 workflow set. Use when starting or resuming BMAD, choosing the next BMAD phase or skill, coordinating analysis, planning, solutioning, implementation, testing, retrospectives, Party Mode, Quick Dev, Dev Auto, or adapting BMAD work across Codex, OpenCode, and Devin.
---

# BMAD Orchestrator

Use this skill as a lean router. Delegate detailed execution to the installed `bmad-*` skill that matches the work instead of reproducing its instructions.

## Establish Context

1. Read the applicable repository instructions before changing files.
2. Check for `_bmad/`, `_bmad-output/`, and existing planning or implementation artifacts.
3. If `_bmad/` exists, treat its installed workflows, configuration, help catalog, and generated skills as authoritative for that project.
4. Invoke `bmad-help` when the current phase, next step, optionality, or workflow name is unclear.
5. Preserve existing artifact locations and project conventions. For a current v6 installation, expect planning artifacts under `_bmad-output/planning-artifacts/` and implementation artifacts under `_bmad-output/implementation-artifacts/` unless its configuration says otherwise.

## Choose the Route

| Need | Preferred skill |
| --- | --- |
| Decide what to do next | `bmad-help` |
| Pressure-test an early idea | `bmad-forge-idea` |
| Brainstorm | `bmad-brainstorming` |
| Market, domain, or technical research | `bmad-market-research`, `bmad-domain-research`, or `bmad-technical-research` |
| Product brief | `bmad-product-brief` |
| PRD creation, validation, or editing | `bmad-create-prd`, `bmad-validate-prd`, or `bmad-edit-prd` |
| UX design | `bmad-ux` |
| Architecture | `bmad-create-architecture` or `bmad-architecture` |
| Epics and stories | `bmad-create-epics-and-stories` |
| Implementation readiness | `bmad-check-implementation-readiness` |
| Project context or documentation | `bmad-generate-project-context` or `bmad-document-project` |
| Sprint planning or status | `bmad-sprint-planning` or `bmad-sprint-status` |
| Story implementation | `bmad-dev-story` |
| Small, well-understood change | `bmad-quick-dev` |
| Bounded autonomous development loop | `bmad-dev-auto` |
| Code review or course correction | `bmad-code-review` or `bmad-correct-course` |
| Testing strategy and automation | `bmad-tea` or the matching `bmad-testarch-*` skill |
| Retrospective | `bmad-retrospective` |
| Multi-perspective discussion | `bmad-party-mode` |
| Custom agent, workflow, or module | `bmad-agent-builder`, `bmad-workflow-builder`, or `bmad-module-builder` |

## Run the Lifecycle

Use the full lifecycle for new products and substantial initiatives:

1. Analysis: brainstorm or forge the idea, research where evidence is needed, then create the product brief.
2. Planning: create and validate the PRD; add UX work for user-facing products.
3. Solutioning: create architecture, epics and stories, then run implementation readiness.
4. Implementation: plan the sprint, create a story, implement, verify, review, and update sprint status.
5. Learning: run retrospectives and fold durable lessons into project context.

Use Quick Dev only when scope is small, risks are understood, and the change does not need the full planning chain. Use Dev Auto only for bounded work with explicit acceptance criteria, verification, stopping conditions, and approval boundaries.

## Coordinate Agents Safely

- Use one thread by default and synthesize BMAD perspectives directly.
- Use Party Mode for structured multi-perspective critique.
- Create separate agents or tasks only when the user explicitly requests delegation or the active environment contract permits it.
- Keep commits, pushes, pull requests, merges, migrations, releases, deployments, destructive changes, and external effects behind their existing authorization boundaries.
- Require fresh verification and the project-required review depth before declaring implementation complete.

## Maintain BMAD

Use the installed CLI for runtime maintenance:

```bash
bmad status
bmad install --directory <project> --action quick-update --yes
```

Do not update a project installation during ordinary workflow execution unless the user asks for an update or compatibility requires it. Back up project customizations before a significant version migration.
