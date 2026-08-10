---
name: product-os
display_name: product-os
platform: Local Project Agents
category: Business creation, ideas, and validation
---

# product-os - Local Project Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `product-os` for Local Project Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

End-to-end product-building workflow from rough idea to launch-ready implementation plan. Use when the user wants to build a product, app, SaaS, agent tool, marketplace, internal tool, MVP, prototype, or feature and need

## How To Use It In Local Project Agents

From this workspace, type: Use the product-os skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `product-os` |
| Canonical name | `product-os` |
| Platform | `Local Project Agents` |
| Category | Business creation, ideas, and validation |

## Description

End-to-end product-building workflow from rough idea to launch-ready implementation plan. Use when the user wants to build a product, app, SaaS, agent tool, marketplace, internal tool, MVP, prototype, or feature and need


## Original SKILL.md

---
name: product-os
description: "End-to-end product-building workflow from rough idea to launch-ready implementation plan. Use when the user wants to build a product, app, SaaS, agent tool, marketplace, internal tool, MVP, prototype, or feature and needs guided movement through discovery, PRD, design, engineering spec, implementation, verification, and launch. Routes into existing skills such as interview-me, idea-refine, pm-skills-create-prd, design, openui, spec-driven-development, planning-and-task-breakdown, frontend-ui-engineering, test-driven-development, and shipping-and-launch."
---

# Product OS

Product OS is the umbrella workflow for turning a product idea into a buildable, verifiable product plan and then into shipped software.

Use this skill as the conductor. Do not duplicate every downstream skill. Pick the next useful phase, produce the artifact for that phase, and route into specialized skills when the work calls for them.

## Operating Mode

Start by identifying the product's current altitude:

| Altitude | Signal | Next move |
| --- | --- | --- |
| Raw idea | Vague problem, audience, or outcome | Interview and refine |
| Direction chosen | Problem and user are known, scope is fuzzy | PRD |
| PRD exists | Requirements exist but UX is unclear | Design path |
| Design exists | Screens or flows exist, build plan is missing | Engineering spec |
| Spec exists | Technical plan exists, tasks are missing | Task breakdown |
| Tasks exist | Work is ready to code | Implement and verify |
| Built | Needs release prep | Launch |

If the user asks to "just build it" but the idea is still ambiguous, surface assumptions and create a thin spec before coding. Keep the process lightweight, but do not let unclear product intent leak into implementation.

## Core Workflow

### 1. Frame

Clarify only what is necessary:

- Target user: who has the problem?
- Problem: what hurts or wastes time today?
- Outcome: what changes if this works?
- Constraint: platform, budget, deadline, existing repo, local tools.
- Success signal: how will we know the MVP is working?

If these are unknown, use `interview-me` or `idea-refine`. Keep questions to 3-5 at a time.

### 2. Refine

Turn the idea into a focused one-pager:

- Problem statement
- Recommended direction
- Key assumptions to validate
- MVP scope
- Not Doing list
- Open questions

Use `idea-refine` for vague or broad ideas. Push back on weak scope, unclear users, or product concepts that are mostly technology looking for a problem.

### 3. Specify Product

Create or update a PRD when the user is ready to commit to a direction.

Minimum PRD sections:

- Objective and target user
- Jobs-to-be-done or user stories
- Core flows
- Functional requirements
- Non-goals
- Success metrics
- Risks and assumptions
- Launch/readiness criteria

Use `pm-skills-create-prd`, `pm-skills-deliver-prd`, or `kw-product-management-write-spec` when available. Save durable PRDs under `docs/` or the project's existing product-docs location.

### 4. Design

Choose the design path by artifact need:

- **Need fast visual exploration:** use MagicPath or `visual-plan`.
- **Need production React/Tailwind design system output or live agent-accessible UI/UX work:** use Subframe `design` and Subframe MCP.
- **Need editable design handoff, diagramming, or wired prototypes:** use Penpot workflows by default; use Figma only when the project already lives there.
- **Need initial product imagery, hero assets, or visual style cues:** generate images directly when that is faster than using a design canvas.
- **Need runtime AI-generated UI:** use `openui` after the stable component vocabulary exists.
- **Need implementation without new design tools:** use `frontend-ui-engineering` with existing code/design patterns.
- **Need a second opinion on PRD-to-UI exploration:** Moonchild is optional, not a default step. Prefer MagicPath + Subframe + Penpot for this workspace.

Produce or request the smallest design artifact that can unblock engineering: a flow map, screen list, wireframe, design-system note, Subframe/MagicPath/Penpot link, generated image, or `Design.md`.

### 5. Specify Engineering

Translate product intent into an engineering spec before code.

Use `spec-driven-development` for new apps, major features, architectural choices, or anything likely to take more than 30 minutes.

The spec must include:

- Objective and acceptance criteria
- Tech stack and existing constraints
- Commands for build/test/dev
- Project structure
- Testing strategy
- Boundaries: Always / Ask First / Never
- Open questions

### 6. Plan Tasks

Use `planning-and-task-breakdown` when the implementation has multiple steps.

Tasks should be:

- Small enough for one focused session
- Ordered by dependency
- Paired with acceptance criteria
- Paired with verification
- Scoped to expected files where possible

### 7. Build

Implement in vertical slices:

- Use `incremental-implementation` for general build flow.
- Use `frontend-ui-engineering` for UI surfaces.
- Use `api-and-interface-design` for contracts and APIs.
- Use `source-driven-development` or Context7 for current library/framework/API docs.
- Use `openui` when implementing runtime generative UI.

Prefer the simplest product that tests the core assumption. Do not add nice-to-have features unless they directly serve the MVP success signal.

### 8. Verify

Run checks appropriate to the work:

- Unit/integration tests via `test-driven-development`
- Browser/runtime checks via `browser-testing-with-devtools`
- Accessibility review for user-facing UI
- Security review for auth, payments, user data, or external tool execution
- Build/lint/typecheck commands from the spec

If verification cannot run, state why and record the residual risk.

### 9. Launch

Use `shipping-and-launch` when the product is ready for users.

Launch artifacts may include:

- Release checklist
- Rollback plan
- Monitoring and instrumentation notes
- Beta user list or feedback loop
- Launch copy
- Post-launch learning plan

## Decision Rules

- Do not start with code when product intent is still raw.
- Do not start with a long PRD when a one-page idea brief is enough.
- Do not design every screen before the riskiest flow is understood.
- Do not use OpenUI for static screens that do not need runtime generation.
- Do not use MagicPath/Subframe/Figma as a blocker when the repo already has a clear design system and the change is small.
- Do not route to Moonchild by default; use it only for optional comparison or when the user explicitly asks for it.
- Prefer a validated MVP over a broad prototype that proves nothing.

## Artifacts

Default artifact path:

- Idea briefs: `docs/ideas/<name>.md`
- PRDs: `docs/prd/<name>.md`
- Design notes: `docs/design/<name>.md`
- Engineering specs: `docs/specs/<name>.md`
- Task plans: `docs/plans/<name>.md`
- Launch plans: `docs/launch/<name>.md`

Use existing project conventions when they differ. For this workspace, follow DOX before editing and update AGENTS.md files when durable workflow contracts change.

## References

Read `references/phase-skill-map.md` when choosing among similar downstream skills or explaining the workflow to the user.
