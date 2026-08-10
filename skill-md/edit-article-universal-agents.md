---
name: edit-article
display_name: edit-article
platform: Universal Agents
category: General and specialized workflows
---

# edit-article - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `edit-article` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Edit and improve articles by restructuring sections, improving clarity, and tightening prose. Use when user wants to edit, revise, or improve an article draft.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the edit-article skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `edit-article` |
| Canonical name | `edit-article` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Edit and improve articles by restructuring sections, improving clarity, and tightening prose. Use when user wants to edit, revise, or improve an article draft.


## Original SKILL.md

---
name: edit-article
description: Edit and improve articles by restructuring sections, improving clarity, and tightening prose. Use when user wants to edit, revise, or improve an article draft.
license: MIT
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

1. First, divide the article into sections based on its headings. Think about the main points you want to make during those sections.

Consider that information is a directed acyclic graph, and that pieces of information can depend on other pieces of information. Make sure that the order of the sections and their contents respects these dependencies.

Confirm the sections with the user.

2. For each section:

2a. Rewrite the section to improve clarity, coherence, and flow. Use maximum 240 characters per paragraph.
