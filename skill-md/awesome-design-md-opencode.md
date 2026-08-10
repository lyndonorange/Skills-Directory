---
name: awesome-design-md
display_name: awesome-design-md
platform: OpenCode
category: General and specialized workflows
---

# awesome-design-md - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `awesome-design-md` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Select, fetch, adapt, and apply curated DESIGN.md files from VoltAgent's awesome-design-md collection. Use when a user wants a website or app to follow a named visual language, needs an AI-readable design system, asks to

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the awesome-design-md skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `awesome-design-md` |
| Canonical name | `awesome-design-md` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Select, fetch, adapt, and apply curated DESIGN.md files from VoltAgent's awesome-design-md collection. Use when a user wants a website or app to follow a named visual language, needs an AI-readable design system, asks to


## Original SKILL.md

---
name: awesome-design-md
description: Select, fetch, adapt, and apply curated DESIGN.md files from VoltAgent's awesome-design-md collection. Use when a user wants a website or app to follow a named visual language, needs an AI-readable design system, asks to create or improve DESIGN.md, or wants design tokens and component rules extracted into implementation guidance.
---

# Awesome DESIGN.md

Use a design system as evidence, not as permission to clone a brand or reproduce protected assets.

## Workflow

1. Read the applicable `AGENTS.md` chain and any existing `DESIGN.md`.
2. Clarify the product, platform, audience, and desired qualities. If a named brand is requested, distinguish inspiration from exact replication.
3. List available systems with `scripts/fetch_design_md.sh --list` or fetch one with `scripts/fetch_design_md.sh <slug> <output>`.
4. Treat the fetched file as source material. Reconcile it with local design tokens, accessibility rules, platform conventions, and existing components.
5. Write or update the project `DESIGN.md`, then implement only if the user requested implementation.
6. Use `hallmark` to audit the rendered system for generic structure, fabricated proof, token drift, and platform-inappropriate styling. Apply its native adapter outside web surfaces.
7. Verify visual consistency, responsive or adaptive behavior, contrast, typography fallbacks, and interaction states.

## Workflow Routing

| Intent | Action |
|---|---|
| Browse available styles | Run the script with `--list` |
| Apply a named style | Fetch its slug, then adapt it |
| Create a new system | Use the section contract in `references/design-md-contract.md` |
| Audit an existing system | Check completeness, conflicts, accessibility, and implementability |

## Gotchas

- The upstream collection changes; fetch at task time rather than assuming a slug exists.
- Brand-specific files may reference proprietary fonts or assets. Provide licensed fallbacks and do not copy logos or trade dress without authorization.
- Do not overwrite an existing `DESIGN.md` until its local decisions are reconciled.
- A design file is not visual verification; inspect the rendered result.

## Examples

- “Give this dashboard a Linear-inspired system” → fetch `linear.app`, adapt tokens, preserve product identity.
- “Create DESIGN.md for this app” → derive the contract from the current UI and requirements.

## References

- Read `references/design-md-contract.md` before creating or auditing a file.
