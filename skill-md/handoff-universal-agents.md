---
name: handoff
display_name: handoff
platform: Universal Agents
category: General and specialized workflows
---

# handoff - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `handoff` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Compact the current conversation into a handoff document for another agent to pick up.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the handoff skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `handoff` |
| Canonical name | `handoff` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Compact the current conversation into a handoff document for another agent to pick up.


## Original SKILL.md

---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS - not the current workspace.

Include a "suggested skills" section in the document, which suggests skills that the agent should invoke.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
