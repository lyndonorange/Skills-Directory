---
name: resolving-merge-conflicts
display_name: resolving-merge-conflicts
platform: OpenCode
category: General and specialized workflows
---

# resolving-merge-conflicts - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `resolving-merge-conflicts` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use when you need to resolve an in-progress git merge/rebase conflict.

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the resolving-merge-conflicts skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `resolving-merge-conflicts` |
| Canonical name | `resolving-merge-conflicts` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Use when you need to resolve an in-progress git merge/rebase conflict.


## Original SKILL.md

---
name: resolving-merge-conflicts
description: "Use when you need to resolve an in-progress git merge/rebase conflict."
---

1. **See the current state** of the merge/rebase. Check git history, and the conflicting files.

2. **Find the primary sources** for each conflict. Understand deeply why each change was made, and what the original intent was. Read the commit messages, check the PRs, check original issues/tickets.

3. **Resolve each hunk.** Preserve both intents where possible. Where incompatible, pick the one matching the merge's stated goal and note the trade-off. Do **not** invent new behaviour. Always resolve; never `--abort`.

4. Discover the project's **automated checks** and run them — typically typecheck, then tests, then format. Fix anything the merge broke.

5. **Finish the merge/rebase.** Stage everything and commit. If rebasing, continue the rebase process until all commits are rebased.
