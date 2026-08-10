---
name: convex-master
display_name: convex-master
platform: OpenCode
category: Software engineering and app building
---

# convex-master - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `convex-master` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Route Convex backend, database, schema, function, auth, component, migration, quickstart, and performance requests to the right specialized Convex workflow. Use when the user asks generally for Convex help, says "Convex"

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the convex-master skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `convex-master` |
| Canonical name | `convex-master` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Route Convex backend, database, schema, function, auth, component, migration, quickstart, and performance requests to the right specialized Convex workflow. Use when the user asks generally for Convex help, says "Convex"


## Original SKILL.md

---
name: convex-master
description: Route Convex backend, database, schema, function, auth, component, migration, quickstart, and performance requests to the right specialized Convex workflow. Use when the user asks generally for Convex help, says "Convex", wants to add or fix Convex in a repo, is unsure which Convex skill to use, or asks to check whether Convex AI guidance is installed. Prefer a more specific Convex skill when the request clearly matches `convex-quickstart`, `convex-setup-auth`, `convex-create-component`, `convex-migration-helper`, or `convex-performance-audit`.
---

# Convex Master

## Purpose

Use this as the router for Convex work. Do not stay in this skill when a specialized Convex workflow clearly matches the request.

## Start Here

Before writing or changing Convex code, check whether the project has current Convex AI guidance:

```bash
npx convex ai-files status
```

If guidance is missing or stale, strongly recommend installing or refreshing it:

```bash
npx convex ai-files install
```

This command installs or refreshes managed Convex AI files, including `convex/_generated/ai/guidelines.md`, AGENTS/CLAUDE sections, and agent skills configured by the project. Prefer this over copying rules by hand.

If the CLI is unavailable or the project cannot run `npx convex`, use the fallback rules file:

```text
https://convex.link/convex_rules.txt
```

Use current official docs for version-sensitive Convex guidance:

- `https://docs.convex.dev/ai/overview`
- `https://docs.convex.dev/cli/reference/ai-files`
- `https://docs.convex.dev/production/project-configuration`

## Route Table

| User Goal | Route |
|-----------|-------|
| New app, add Convex to an existing app, scaffold, provision, first function | `convex-quickstart` |
| Auth setup, providers, users, identity mapping, access control | `convex-setup-auth` |
| Reusable Convex component, component boundary, app wrapper functions | `convex-create-component` |
| Breaking schema or data changes, backfills, online migrations | `convex-migration-helper` |
| Slow queries, high read bytes, OCC conflicts, subscription cost, function limits | `convex-performance-audit` |

If the target specialized skill is installed, switch to it. If it is not installed, say which skill is missing and continue using the routing summary plus official Convex docs as the fallback.

## Routing Heuristics

- Route to quickstart when `convex/` is absent, the user asks to set up Convex, or `package.json` lacks `convex`.
- Route to auth when the request mentions login, signup, Clerk, Convex Auth, WorkOS, Auth0, JWTs, `ctx.auth`, users, roles, or authorization.
- Route to components when the user wants reusable backend logic with isolated tables or package-like Convex functionality.
- Route to migrations when a schema change affects existing data, especially adding required fields, changing types, splitting tables, or removing fields.
- Route to performance when there is measured slowness, high document reads, high bytes read, OCC conflicts, high subscriptions, timeouts, or transaction limits.

## Fallback Behavior

If no route is clear:

1. Inspect the repo for `convex/`, `convex.json`, `package.json`, `_generated`, auth files, schema, functions, and deployment env vars.
2. Ask one concise clarifying question only if route choice changes the implementation path.
3. Recommend `npx convex ai-files install` when guidance is missing.
4. Use official Convex docs for current syntax and CLI behavior.
5. Run the relevant validation command before claiming success.

## Validation Defaults

Prefer project-specific commands. Common Convex checks:

- `npx convex ai-files status`
- `npx convex dev --once`
- `npx convex codegen`
- `npx convex insights --details`
- Project tests, typecheck, and lint commands from `package.json`

Do not run long-lived `npx convex dev` in the foreground. For local development, ask the user to run the watcher or start it in the background when appropriate.
