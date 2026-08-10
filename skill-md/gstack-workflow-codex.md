---
name: gstack-workflow
display_name: gstack-workflow
platform: Codex
category: General and specialized workflows
---

# gstack-workflow - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `gstack-workflow` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Route product and engineering work through the gstack lifecycle: idea shaping, specifications, executive and engineering plan review, investigation, code review, QA, design review, shipping, documentation, security, and

## How To Use It In Codex

In Codex, click the chat box, press /, choose gstack-workflow, then write the task. Fallback prompt: Use the gstack-workflow skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gstack-workflow` |
| Canonical name | `gstack-workflow` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Route product and engineering work through the gstack lifecycle: idea shaping, specifications, executive and engineering plan review, investigation, code review, QA, design review, shipping, documentation, security, and


## Original SKILL.md

---
name: gstack-workflow
description: "Route product and engineering work through the gstack lifecycle: idea shaping, specifications, executive and engineering plan review, investigation, code review, QA, design review, shipping, documentation, security, and retrospectives. Use when the user mentions gstack or wants a disciplined plan-review-build-test-ship loop. Do not use as a substitute for an explicitly requested specialized local skill."
---

# GStack Workflow

Use gstack's product-and-engineering lifecycle without loading its roughly fifty large upstream skills into the default context.

## Workflow

1. Read the applicable `AGENTS.md` chain and inspect the repository state.
2. Choose the smallest workflow from `references/workflow-map.md` that covers the request.
3. Preserve the workflow boundary: review-only stages do not edit; implementation stages verify before shipping.
4. If the full upstream runtime is installed, invoke its namespaced skill. Otherwise execute the mapped local equivalent and state that the result is gstack-inspired rather than gstack-runtime output.
5. Finish with the next recommended lifecycle step.

## Workflow Routing

| Intent | Route |
|---|---|
| Shape an idea | `office-hours` or `spec` |
| Review scope or architecture | `plan-ceo-review`, `plan-eng-review`, or `autoplan` |
| Diagnose a bug | `investigate` |
| Review or verify | `review`, `qa`, `design-review`, or `cso` |
| Ship and document | `ship`, `land-and-deploy`, or `document-release` |
| Save learning | `context-save`, `learn`, or `retro` |

## Gotchas

- Do not claim the upstream gstack runtime ran unless its generated Codex skill and required binaries are present.
- Upstream gstack skills are very large; prefer this router in the curated default and load only the selected workflow.
- Planning and review routes are read-only until the user authorizes implementation.
- Browser and deploy routes may require setup that is not implied by invoking this router.

## Examples

- “Use gstack to shape this feature” → route to idea shaping, then recommend plan review.
- “Run the gstack loop before shipping” → review the plan and diff, verify behavior, then prepare the ship handoff.

## References

- Read `references/workflow-map.md` for the complete route map and upstream provenance.
