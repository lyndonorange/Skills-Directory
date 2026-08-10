---
name: aegis
display_name: aegis
platform: Codex
category: General and specialized workflows
---

# aegis - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `aegis` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal, host-neutral adaptation of Christopher Kahler's AEGIS for evidence-led codebase diagnosis, adversarial review, risk synthesis, and controlled remediation planning. Use when the user invokes AEGIS; asks for a c

## How To Use It In Codex

In Codex, click the chat box, press /, choose aegis, then write the task. Fallback prompt: Use the aegis skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `aegis` |
| Canonical name | `aegis` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Universal, host-neutral adaptation of Christopher Kahler's AEGIS for evidence-led codebase diagnosis, adversarial review, risk synthesis, and controlled remediation planning. Use when the user invokes AEGIS; asks for a c


## Original SKILL.md

---
name: aegis
description: Universal, host-neutral adaptation of Christopher Kahler's AEGIS for evidence-led codebase diagnosis, adversarial review, risk synthesis, and controlled remediation planning. Use when the user invokes AEGIS; asks for a comprehensive audit across architecture, data, correctness, security, privacy, testing, reliability, performance, maintainability, operability, change risk, team risk, or runtime reality; or wants audit findings converted into PAUL-ready work without assuming Claude Code or automatic multi-agent execution.
---

# AEGIS

Audit a codebase with disciplined doubt: separate evidence from interpretation, challenge confident conclusions, and turn verified risks into bounded work.

## Universal Contract

- Follow applicable repository instructions and authorization boundaries first.
- Treat audit and review requests as read-only. Do not remediate unless the user also requests fixes.
- Run as one agent by default. Use specialist subagents only when the user explicitly requests delegation and the host permits it.
- Do not install scanners, start services, upload code, or send source to remote tools without explicit authorization.
- Use available local tools as evidence sources; missing tools reduce coverage and must be disclosed.
- Never claim a clean domain from absence of evidence. Report `covered`, `partially covered`, `not covered`, or `not applicable`.

## Route the Request

| Request | Route |
|---|---|
| Broad codebase assessment | Diagnostic phases 0-5 |
| One risk domain | Focused audit with the same evidence schema |
| Challenge an existing review | Devil's Advocate pass |
| Compare docs/config/runtime behavior | Reality Gap pass |
| Prioritize findings | Risk synthesis |
| Create remediation guidance | Transform phases 6-8 |
| Implement fixes | Hand approved work to PAUL |

Read [framework.md](references/framework.md) before a comprehensive audit.

## Diagnostic Workflow

1. **Context and threat model:** establish purpose, users, critical data, constraints, deployment reality, success/failure criteria, and explicit non-goals.
2. **Signal gathering:** inspect code, tests, manifests, dependencies, configuration, history, CI/CD, deployment files, and available runtime evidence. Record facts before opinions.
3. **Domain review:** cover all 14 domains or explicitly record why a domain is not applicable or not covered.
4. **Reality and change-risk review:** test whether documentation matches configuration and behavior; identify blast radius, ownership concentration, and fragile boundaries.
5. **Adversarial review:** attack the strongest claims, seek ignored evidence, and state an alternate narrative that could fit the facts.
6. **Synthesis:** deduplicate findings, resolve disagreements, rank by likelihood and impact, and identify what is likely to fail first.

For each claim, label:

- `observation`: directly seen in files, commands, logs, or runtime behavior;
- `interpretation`: what the observation probably means;
- `judgment`: severity or action recommendation;
- `unknown`: material evidence that is missing.

## Finding Contract

Each actionable finding must include:

- stable ID and domain;
- title and severity;
- confidence and evidence quality;
- exact evidence with file/line, command, or artifact provenance;
- observed behavior and expected behavior;
- impact, likelihood, and blast radius;
- assumptions and counterevidence;
- recommended intervention level;
- verification needed to close it.

Do not inflate finding counts with style preferences, duplicate symptoms, or speculative vulnerabilities.

## Transform and PAUL Handoff

Transform remains non-mutating until the user requests fixes.

1. Group confirmed findings into coherent remediation themes.
2. Choose the smallest safe intervention: configuration, local fix, bounded refactor, architectural change, or explicit risk acceptance.
3. Model coupling, regression probability, rollback, and verification.
4. Convert approved remediation into PAUL phases and plans with Given/When/Then acceptance criteria.
5. Let PAUL own approval, APPLY, fresh verification, and UNIFY. AEGIS does not bypass PAUL gates.

## Outputs

Default to a concise report in chat. Save audit state or reports only when requested. A useful final report contains scope, coverage matrix, prioritized findings, Devil's Advocate challenges, unresolved unknowns, and a remediation sequence.

## References

- Read [framework.md](references/framework.md) for domains, phases, coverage, and severity rules.
- Read [upstream.md](references/upstream.md) for pinned source provenance and compatibility limits.
