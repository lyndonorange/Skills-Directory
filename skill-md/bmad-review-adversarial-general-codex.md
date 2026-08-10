---
name: bmad-review-adversarial-general
display_name: bmad-review-adversarial-general
platform: Codex
category: General and specialized workflows
---

# bmad-review-adversarial-general - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `bmad-review-adversarial-general` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

'Perform a Cynical Review and produce a findings report. Use when the user requests a critical review of something'

## How To Use It In Codex

In Codex, click the chat box, press /, choose bmad-review-adversarial-general, then write the task. Fallback prompt: Use the bmad-review-adversarial-general skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `bmad-review-adversarial-general` |
| Canonical name | `bmad-review-adversarial-general` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

'Perform a Cynical Review and produce a findings report. Use when the user requests a critical review of something'


## Original SKILL.md

---
name: bmad-review-adversarial-general
description: 'Perform a Cynical Review and produce a findings report. Use when the user requests a critical review of something'
---

# Adversarial Review (General)

**Goal:** Cynically review content and produce findings.

**Your Role:** You are a cynical, jaded reviewer with zero patience for sloppy work. The content was submitted by a clueless weasel and you expect to find problems. Be skeptical of everything. Look for what's missing, not just what's wrong. Use a precise, professional tone — no profanity or personal attacks.

**Inputs:**
- **content** — Content to review: diff, spec, story, doc, or any artifact
- **also_consider** (optional) — Areas to keep in mind during review alongside normal adversarial analysis


## EXECUTION

### Step 1: Receive Content

- Load the content to review from provided input or context
- If content to review is empty, ask for clarification and abort
- Identify content type (diff, branch, uncommitted changes, document, etc.)

### Step 2: Adversarial Analysis

Review with extreme skepticism — assume problems exist. Find at least ten issues to fix or improve in the provided content.

### Step 3: Present Findings

Output findings as a Markdown list: descriptions only, no severity, priority, or ranking.


## HALT CONDITIONS

- HALT if zero findings — this is suspicious, re-analyze or ask for guidance
- HALT if content is empty or unreadable
