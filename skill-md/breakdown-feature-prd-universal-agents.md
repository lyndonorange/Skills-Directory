---
name: breakdown-feature-prd
display_name: breakdown-feature-prd
platform: Universal Agents
category: Product, growth, marketing, and PM
---

# breakdown-feature-prd - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `breakdown-feature-prd` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Generate detailed Product Requirements Documents (PRDs) for SaaS platform features from parent epics, epic PRDs, architecture docs, or high-level feature ideas. Use when a user asks to break down an epic into a feature P

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the breakdown-feature-prd skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `breakdown-feature-prd` |
| Canonical name | `breakdown-feature-prd` |
| Platform | `Universal Agents` |
| Category | Product, growth, marketing, and PM |

## Description

Generate detailed Product Requirements Documents (PRDs) for SaaS platform features from parent epics, epic PRDs, architecture docs, or high-level feature ideas. Use when a user asks to break down an epic into a feature P


## Original SKILL.md

---
name: breakdown-feature-prd
description: Generate detailed Product Requirements Documents (PRDs) for SaaS platform features from parent epics, epic PRDs, architecture docs, or high-level feature ideas. Use when a user asks to break down an epic into a feature PRD, create SaaS feature requirements, define product goals, personas, user stories, functional and non-functional requirements, acceptance criteria, out-of-scope boundaries, or save a PRD under /docs/ways-of-work/plan/{epic-name}/{feature-name}/prd.md for engineering handoff.
---

# Breakdown Feature PRD

## Role

Act as an expert Product Manager for a large-scale SaaS platform. Convert a parent epic and feature idea into a complete Product Requirements Document that engineering can use as the single source of truth for technical specification and implementation planning.

## Discovery

Before writing the PRD:

1. Read the parent epic, epic PRD, architecture documents, roadmap notes, existing requirements, and nearby feature docs when paths are provided or discoverable.
2. Identify the epic name, feature name, target users, business problem, success metrics, and known constraints.
3. If critical information is missing, ask concise clarifying questions before creating the PRD.
4. If minor details are missing but the PRD can proceed, document assumptions explicitly in the PRD.
5. Preserve existing product terminology and folder conventions.

## Output Location

When asked to save the PRD, write it to:

```text
/docs/ways-of-work/plan/{epic-name}/{feature-name}/prd.md
```

Use lowercase hyphen-case for `{epic-name}` and `{feature-name}` unless the repository already uses a different convention.

If the user asks only for draft content in chat, output the complete Markdown PRD without writing a file.

## PRD Requirements

The PRD must be specific, testable, and scoped. It must include:

- Clear feature name.
- Links to parent epic PRD and architecture documents when available.
- Problem, solution, and expected impact.
- Target personas.
- User stories covering primary paths and edge cases.
- Functional requirements with unambiguous system behavior.
- Non-functional requirements for performance, security, privacy, accessibility, reliability, observability, and compliance when relevant.
- Acceptance criteria that can validate completion.
- Out-of-scope boundaries to prevent scope creep.

## PRD Template

Use this structure:

```markdown
# [Feature Name]

## 1. Feature Name

[Clear, concise, descriptive feature name.]

## 2. Epic

- Parent Epic PRD: [label](path-or-url)
- Parent Architecture: [label](path-or-url)
- Related Documents:
  - [label](path-or-url)

## 3. Goal

### Problem

[Describe the user problem or business need in 3-5 sentences.]

### Solution

[Explain how this feature solves the problem.]

### Impact

[List expected outcomes and metrics, such as activation, engagement, conversion, retention, support deflection, operational efficiency, or risk reduction.]

## 4. User Personas

- **[Persona Name]**: [Role, context, goals, pain points, and permissions or plan tier if relevant.]

## 5. User Stories

- **US-001**: As a [user persona], I want to [perform an action] so that I can [achieve a benefit].
- **US-002**: As a [user persona], I want to [perform an action] so that I can [achieve a benefit].

## 6. Requirements

### Functional Requirements

- **FR-001**: [Specific system behavior.]
- **FR-002**: [Specific system behavior.]

### Non-Functional Requirements

- **NFR-001 Performance**: [Latency, scale, throughput, or resource requirement.]
- **NFR-002 Security**: [Auth, authorization, audit, abuse prevention, or data handling requirement.]
- **NFR-003 Accessibility**: [WCAG/mobile/platform accessibility requirement.]
- **NFR-004 Privacy**: [PII, retention, consent, or data minimization requirement.]
- **NFR-005 Reliability**: [Failure mode, retry, degradation, or uptime requirement.]
- **NFR-006 Observability**: [Events, logs, metrics, dashboards, or alerts.]

## 7. Acceptance Criteria

### [User Story Or Requirement Name]

- [ ] Given [context], when [action], then [observable outcome].
- [ ] Given [context], when [edge case], then [observable outcome].

## 8. Out Of Scope

- [Explicitly excluded capability, user segment, integration, platform, workflow, or edge case.]

## 9. Assumptions And Open Questions

### Assumptions

- **A-001**: [Assumption.]

### Open Questions

- **Q-001**: [Question and owner if known.]
```

## Quality Rules

- Use numbered IDs for user stories, requirements, assumptions, and questions.
- Make requirements independently testable.
- Avoid vague words like "easy", "fast", "robust", or "seamless" unless paired with measurable criteria.
- Include edge cases such as empty states, permission failures, invalid inputs, loading states, retries, and partial failures where relevant.
- Add out-of-scope items for anything a stakeholder could reasonably assume is included but is not.
- Do not invent links to documents that do not exist; use plain text references or mark as unavailable.
- If saving the file, create parent directories as needed and report the final path.
