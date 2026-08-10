---
name: herdr-triage
display_name: herdr-triage
platform: Universal Agents
category: General and specialized workflows
---

# herdr-triage - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `herdr-triage` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Triage open herdr GitHub issues into a concise decision-first Markdown table. Use when the user says "triage", asks to triage open issues, asks which issues need attention, or wants issue priority/recommendation lights f

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the herdr-triage skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `herdr-triage` |
| Canonical name | `herdr-triage` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Triage open herdr GitHub issues into a concise decision-first Markdown table. Use when the user says "triage", asks to triage open issues, asks which issues need attention, or wants issue priority/recommendation lights f


## Original SKILL.md

---
name: herdr-triage
description: Triage open herdr GitHub issues into a concise decision-first Markdown table. Use when the user says "triage", asks to triage open issues, asks which issues need attention, or wants issue priority/recommendation lights for herdr.
---

# Herdr Issue Triage

Use this skill only inside the herdr repository.

When the user says `triage`, inspect open GitHub issues for `ogulcancelik/herdr` and return a concise Markdown table. Prefer GitHub MCP tools when available. If they are unavailable, use `gh issue list` / `gh issue view` only when authenticated access is already configured.

Use this table shape:

| Light | Recommendation | Issue | Age | Reactions | Why |
|---|---|---|---:|---:|---|
| 🔴 | fix now | [#123](https://github.com/ogulcancelik/herdr/issues/123) | 18d | 5 | user-visible regression |
| 🟡 | queue | [#124](https://github.com/ogulcancelik/herdr/issues/124) | 42d | 2 | useful but not blocking |
| 🔵 | defer | [#125](https://github.com/ogulcancelik/herdr/issues/125) | 7d | 0 | cosmetic polish |

Keep issue numbers as Markdown links. Use days since issue creation for `Age`. Use total reactions for `Reactions`; include a compact breakdown only when it changes interpretation, such as `7 (5 👍, 2 👀)`.

Classify with these lights:

- 🔴 `fix now`: reproducible bug, crash, data loss, blocked workflow, release risk, or high-confidence user-visible regression.
- 🟡 `queue`: useful feature, important quality issue, repeated user signal, stale issue that still looks valid, or behavior worth scheduling.
- 🔵 `defer`: cosmetic polish, low-signal idea, unclear report, docs-only nit, or issue that likely needs more evidence before implementation.

Recommendations should be short imperative phrases: `fix now`, `queue`, `defer`, `needs repro`, `close?`, or `needs owner decision`.

Write one sentence before the table only if needed to state scope, such as how many open issues were inspected. After the table, add at most one short note for uncertainty or follow-up. Do not produce a long narrative unless the user asks for depth.
