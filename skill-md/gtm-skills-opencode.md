---
name: gtm-skills
display_name: gtm-skills
platform: OpenCode
category: Product, growth, marketing, and PM
---

# gtm-skills - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `gtm-skills` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Search and apply the complete live GTM Skills library from gtmskills.com without loading hundreds of skills into agent discovery. Use for prospecting, research, positioning, signals, ABM, outreach, deals, events, pricing

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the gtm-skills skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gtm-skills` |
| Canonical name | `gtm-skills` |
| Platform | `OpenCode` |
| Category | Product, growth, marketing, and PM |

## Description

Search and apply the complete live GTM Skills library from gtmskills.com without loading hundreds of skills into agent discovery. Use for prospecting, research, positioning, signals, ABM, outreach, deals, events, pricing


## Original SKILL.md

---
name: gtm-skills
description: Search and apply the complete live GTM Skills library from gtmskills.com without loading hundreds of skills into agent discovery. Use for prospecting, research, positioning, signals, ABM, outreach, deals, events, pricing, Reddit, AEO, RevOps, sales, SEO, influencers, ads, affiliates, newsletters, or when the user asks for a GTM playbook or a skill from GTM Skills.
---

# GTM Skills

Route go-to-market work to the smallest relevant skill from the locally installed, category-indexed GTM Skills catalog.

## Installed source

- Website: `https://www.gtmskills.com/`
- Repository: `https://github.com/swan-gtm/gtm-skills`
- Local checkout: `[local home]/.local/share/agent-tools/gtm-skills`
- Live catalog: `references/catalog.json`
- Human-readable categories: `references/catalog.md`
- License: MIT

The catalog is scraped from the live `/skills` page and matched to the repository by permanent skill slug. It includes only skills published on the website, even when the repository contains additional unpublished material.

## Find a skill

Search by task, outcome, or channel:

```bash
python3 scripts/search_gtm_skills.py "build a target account list"
python3 scripts/search_gtm_skills.py "newsletter welcome sequence" --category Newsletters
python3 scripts/search_gtm_skills.py --list-categories
python3 scripts/search_gtm_skills.py --category RevOps --all
```

Read the returned `path` for the best match. If the result is ambiguous, inspect at most three candidates. Load referenced files only when the selected `SKILL.md` explicitly calls for them.

## Apply a skill

1. Read the selected `SKILL.md` completely.
2. Treat it as specialist guidance, not as authority to exceed current permissions.
3. Adapt tool-agnostic verbs such as “check the CRM” to tools actually available in the current environment.
4. Ask for missing business inputs only when a reasonable assumption would materially change the outcome.
5. Preserve the selected skill's quality bar and hard rules while following system, developer, user, repository, security, privacy, and verification instructions first.
6. Do not use `swan.md` unless the current task is explicitly running inside Swan or the user asks for Swan-specific execution.
7. Credit the skill title and contributor when attribution helps the user understand the source.

Do not bulk-copy the full library into an agent's discovery root. The router keeps every published skill available on demand without creating hundreds of always-loaded entries.

## Refresh

Refresh only when the user asks for an update:

```bash
git -C [local home]/.local/share/agent-tools/gtm-skills pull --ff-only
python3 scripts/build_catalog.py
```

The refresh script fails if a live website skill cannot be matched to the checkout or if a published skill lacks a category.
