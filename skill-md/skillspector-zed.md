---
name: skillspector
display_name: skillspector
platform: Zed
category: General and specialized workflows
---

# skillspector - Zed Skill Package

## What This Is

This is a friend-safe Markdown copy of `skillspector` for Zed. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use the installed SkillSpector CLI for security review of AI agent skills.

## How To Use It In Zed

In Zed, open the Agent panel and type: Use the skillspector skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `skillspector` |
| Canonical name | `skillspector` |
| Platform | `Zed` |
| Category | General and specialized workflows |

## Description

Use the installed SkillSpector CLI for security review of AI agent skills.

## Original SKILL.md

---
name: skillspector
description: Use NVIDIA SkillSpector to scan AI agent skills for security risks, malicious patterns, vulnerable dependencies, MCP permission issues, or unsafe instructions before or after installing skills. Use when asked to audit, inspect, validate, or run a security scan against skill folders.
---

# SkillSpector

Use the installed SkillSpector CLI for security review of AI agent skills.

## Installed Runtime

- CLI: `[local home]/.local/bin/skillspector`
- Source/venv: `[local home]/.local/share/skillspector`
- Reports: `[local home]/.local/share/skillspector/reports`

## Workflow

1. Prefer static scanning first:

   ```bash
   [local home]/.local/bin/skillspector scan /path/to/skill --no-llm --format json --output /path/to/report.json
   ```

2. Use LLM scanning only when the needed provider credentials are available through environment variables. Do not ask the user to paste secrets into chat.
3. Treat results above `SAFE` as review prompts, not automatic proof of malicious behavior. Inspect exact files and lines before recommending removal.
4. For batches, write one JSON report per skill plus an aggregate Markdown summary.

## Output

Summarize scanned skill count, highest risk score, total issues, `CAUTION` or `DO_NOT_INSTALL` skills, and the report location.

