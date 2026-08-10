---
name: typescript-master
display_name: typescript-master
platform: OpenCode
category: Software engineering and app building
---

# typescript-master - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `typescript-master` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Advanced TypeScript engineering skill for building, debugging, reviewing, and migrating TypeScript codebases, especially Tauri desktop apps, Convex backends and data layers, React/Vite/Next frontends, monorepos, strict t

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the typescript-master skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `typescript-master` |
| Canonical name | `typescript-master` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Advanced TypeScript engineering skill for building, debugging, reviewing, and migrating TypeScript codebases, especially Tauri desktop apps, Convex backends and data layers, React/Vite/Next frontends, monorepos, strict t


## Original SKILL.md

---
name: typescript-master
description: Advanced TypeScript engineering skill for building, debugging, reviewing, and migrating TypeScript codebases, especially Tauri desktop apps, Convex backends and data layers, React/Vite/Next frontends, monorepos, strict tsconfig work, type-level APIs, module resolution, ESM/CJS issues, test setup, build tooling, and validation. Use when the user asks for "TypeScript master", TypeScript architecture, Tauri TypeScript frontend/backend boundary work, Convex TypeScript functions or validators, data-layer typing, type errors, tsconfig, build/test/lint setup, migration from JavaScript, or type-performance debugging.
---

# TypeScript Master

## Core Rule

Adapt to the project in front of you. Inspect package manager, framework, `tsconfig`, module system, scripts, Tauri files, Convex files, tests, and lint/format tools before changing broad TypeScript configuration.

For library, framework, SDK, or CLI details, fetch current docs first when Context7 or official docs are available. TypeScript, Tauri, Convex, Vite, Next.js, and testing tools change often.

## Workflow

1. Detect project shape:
   - Package manager and scripts from `package.json`.
   - TypeScript version with `npx tsc --version` when available.
   - `tsconfig*.json`, monorepo config, frontend framework, tests, linting, and build tools.
   - Tauri markers: `src-tauri/`, `tauri.conf.*`, `@tauri-apps/api`.
   - Convex markers: `convex/`, `_generated`, `convex/schema.ts`, `convex.config.ts`, `convex` dependency.
2. Route to the smallest relevant reference:
   - Core type design and strictness: `references/core-typescript.md`.
   - Tauri app integration: `references/tauri-typescript.md`.
   - Convex and data layer typing: `references/convex-data-layer.md`.
   - Tooling, monorepos, modules, and migrations: `references/tooling-monorepo.md`.
   - Library bundling with tsdown: `references/tsdown-library-bundling.md`.
   - Validation and troubleshooting: `references/validation-debugging.md`.
3. Prefer existing project scripts over raw commands.
4. Make the smallest change that preserves public API and runtime behavior unless the user requests a migration.
5. Run fresh validation before claiming success.

## Routing

- If the task is mostly Tauri project structure, Rust commands, permissions, capabilities, packaging, updater, or IPC security, also use `tauri-desktop-framework`.
- If the task is mostly Convex setup, auth, components, migrations, or performance, also use `convex-master`.
- If the task is TypeScript library publishing, npm package exports, declaration generation, tsup migration, dual ESM/CJS output, or package validation, read `references/tsdown-library-bundling.md`.
- If the task is ultra-specific bundler internals, ESM/CJS graph surgery, or TypeScript compiler trace work, say that deeper specialist review is warranted and continue only with bounded diagnostics unless the user asks you to proceed.

## Defaults

- Prefer `strict` TypeScript for new code.
- Prefer `unknown` plus narrowing over `any`.
- Prefer discriminated unions or result objects for recoverable states.
- Prefer `satisfies` for config objects that need validation without losing literals.
- Prefer interfaces for exported object shapes and type aliases for unions, mapped types, and conditional types.
- Keep type-level cleverness proportional to the API value.
- Co-locate feature types with implementation; move shared types only when reused across boundaries.
- Validate data at trust boundaries: Tauri invoke inputs, Convex function args, API responses, storage, file system, and user input.

## Common Checks

Use one-shot commands, not watch/serve processes:

```bash
npm run -s typecheck || npx tsc --noEmit
npm test -s || npx vitest run --reporter=basic --no-watch
npm run -s build
```

Adjust for `pnpm`, `yarn`, or `bun` and skip commands the project does not define. Use `npx convex dev --once` for Convex validation and Tauri project commands when app packaging or IPC changes need them.
