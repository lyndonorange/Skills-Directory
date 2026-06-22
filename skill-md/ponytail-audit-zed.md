---
name: ponytail-audit
display_name: ponytail-audit
platform: Zed
category: Software engineering and app building
---

# ponytail-audit - Zed Skill Package

## What This Is

This is a friend-safe Markdown copy of `ponytail-audit` for Zed. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

name: ponytail-audit

## How To Use It In Zed

In Zed, open the Agent panel and type: Use the ponytail-audit skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `ponytail-audit` |
| Canonical name | `ponytail-audit` |
| Platform | `Zed` |
| Category | Software engineering and app building |

## Description

name: ponytail-audit

## Original SKILL.md

---
name: ponytail-audit
description: >
  Whole-repo audit for over-engineering. Like ponytail-review, but scans the
  entire codebase instead of a diff: a ranked list of what to delete, simplify,
  or replace with stdlib/native equivalents. Use when the user says "audit this
  codebase", "audit for over-engineering", "what can I delete from this repo",
  "find bloat", "ponytail-audit", or "/ponytail-audit". One-shot report, does
  not apply fixes.
---

ponytail-review, repo-wide. Scan the whole tree instead of a diff. Rank
findings biggest cut first.

## Tags

Same as ponytail-review:

- `delete:` dead code, unused flexibility, speculative feature. Replacement: nothing.
- `stdlib:` hand-rolled thing the standard library ships. Name the function.
- `native:` dependency or code doing what the platform already does. Name the feature.
- `yagni:` abstraction with one implementation, config nobody sets, layer with one caller.
- `shrink:` same logic, fewer lines. Show the shorter form.

## Hunt

Deps the stdlib or platform already ships, single-implementation interfaces,
factories with one product, wrappers that only delegate, files exporting one
thing, dead flags and config, hand-rolled stdlib.

## Output

One line per finding, ranked: `<tag> <what to cut>. <replacement>. [path]`.
End with `net: -<N> lines, -<M> deps possible.` Nothing to cut: `Lean already. Ship.`

## Boundaries

Complexity only, correctness bugs, security holes, and performance go to a
normal review pass. Lists findings, applies nothing. One-shot.
"stop ponytail-audit" or "normal mode" to revert.

