---
name: composio-cli
display_name: composio-cli
platform: Universal Agents
category: Agent platforms, tools, and automation
---

# composio-cli - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `composio-cli` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Search, authenticate, and execute tools across 1000+ apps from the terminal. Use when an agent needs to discover available integrations, connect to third-party services, or execute actions across SaaS apps.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the composio-cli skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `composio-cli` |
| Canonical name | `composio-cli` |
| Platform | `Universal Agents` |
| Category | Agent platforms, tools, and automation |

## Description

Search, authenticate, and execute tools across 1000+ apps from the terminal. Use when an agent needs to discover available integrations, connect to third-party services, or execute actions across SaaS apps.


## Original SKILL.md

---
name: composio-cli
description: "Search, authenticate, and execute tools across 1000+ apps from the terminal. Use when an agent needs to discover available integrations, connect to third-party services, or execute actions across SaaS apps."
---

# Composio CLI

Search, authenticate, and execute tools across 1000+ apps. Type-safe code generation, trigger listeners, and structured JSON output.

- **Docs**: https://docs.composio.dev/docs/cli
- **Website**: https://composio.dev

## Installation

```bash
curl -fsSL https://composio.dev/install | bash
composio login
```

## Key Commands

```bash
composio search "star a github repo"
composio execute GITHUB_STAR_A_REPOSITORY_FOR_THE_AUTHENTICATED_USER -d '{"owner":"composiohq","repo":"composio"}'
composio apps list
composio triggers list
```

## Agent-Friendly Features

- Structured JSON output on all commands
- API key auth via env vars
- Non-interactive execution mode
- 1000+ pre-built tool integrations
