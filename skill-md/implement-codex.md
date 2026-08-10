---
name: implement
display_name: implement
platform: Codex
category: General and specialized workflows
---

# implement - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `implement` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Implement a piece of work based on a spec or set of tickets.

## How To Use It In Codex

In Codex, click the chat box, press /, choose implement, then write the task. Fallback prompt: Use the implement skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `implement` |
| Canonical name | `implement` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Implement a piece of work based on a spec or set of tickets.


## Original SKILL.md

---
name: implement
description: "Implement a piece of work based on a spec or set of tickets."
---

Implement the work described by the user in the spec or tickets.

Use /tdd where possible, at pre-agreed seams.

Run typechecking regularly, single test files regularly, and the full test suite once at the end.

Once done, use /code-review to review the work.

Commit your work to the current branch.
