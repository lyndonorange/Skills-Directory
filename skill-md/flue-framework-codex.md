---
name: flue-framework
display_name: flue-framework
platform: Codex
category: Software engineering and app building
---

# flue-framework - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `flue-framework` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Flue is a TypeScript agent harness framework for building autonomous agents and AI workflows. Use it when the project needs app-native agents with sessions, tools, skills, instructions, filesystem/sandbox access, routes,

## How To Use It In Codex

In Codex, click the chat box, press /, choose flue-framework, then write the task. Fallback prompt: Use the flue-framework skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `flue-framework` |
| Canonical name | `flue-framework` |
| Platform | `Codex` |
| Category | Software engineering and app building |

## Description

Flue is a TypeScript agent harness framework for building autonomous agents and AI workflows. Use it when the project needs app-native agents with sessions, tools, skills, instructions, filesystem/sandbox access, routes,

## Original SKILL.md

---
name: flue-framework
description: Use when building or modifying Flue Framework agents, workflows, tools, skills, sandboxes, or Electron app agent backends. Covers Flue CLI/runtime setup, project layout, and local commands.
---

# Flue Framework

Flue is a TypeScript agent harness framework for building autonomous agents and AI workflows. Use it when the project needs app-native agents with sessions, tools, skills, instructions, filesystem/sandbox access, routes, and deployable Node or Cloudflare targets.

## Installed Tooling

- Global CLI: `/opt/homebrew/bin/flue`
- Global packages: `@flue/cli`, `@flue/runtime`, `@flue/sdk`
- Installed version: `0.10.1`
- Required Node: `>=22.18.0`
- Local machine Node LTS: `/opt/homebrew/opt/node@24/bin/node`

## Project Setup

Prefer project-local dependencies even though the CLI is globally available:

```bash
npm install @flue/runtime
npm install --save-dev @flue/cli
npx flue init --target node
```

For Electron apps, use Flue as the local agent backend or workflow layer, not as the renderer UI itself.

Recommended layout:

```text
src/
  agents/
    app-assistant.ts
  workflows/
    summarize-note.ts
  tools/
    project-files.ts
  skills/
    product-planning/
      SKILL.md
flue.config.ts
```

## Common Commands

```bash
npx flue init --target node
npx flue dev --target node
npx flue connect app-assistant local --target node
npx flue run summarize-note --target node --payload '{"text":"hello"}'
npx flue build --target node
```

Use `flue --help` for current command syntax.

## Core Patterns

- `src/agents/*.ts` defines addressable agents. The filename becomes the agent name.
- `src/workflows/*.ts` defines finite operations that can be invoked by name.
- Import app-owned skills with `import skill from '../skills/name/SKILL.md' with { type: 'skill' }`.
- Workspace skills can also be discovered under `<cwd>/.agents/skills/<name>/SKILL.md`.
- Use tools for executable actions; skills only guide agent behavior.
- Do not commit provider secrets. Keep `.env` ignored.

## Electron Fit

Use Electron renderer for UI and Electron main process or a local Node sidecar for Flue. The app can call a local Flue agent/workflow via HTTP/WebSocket or invoke Flue runtime code from the Node side when appropriate.

