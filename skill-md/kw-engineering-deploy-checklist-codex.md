---
name: kw-engineering-deploy-checklist
display_name: kw-engineering-deploy-checklist
platform: Codex
category: General and specialized workflows
---

# kw-engineering-deploy-checklist - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-deploy-checklist` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-deploy-checklist, then write the task. Fallback prompt: Use the kw-engineering-deploy-checklist skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-deploy-checklist` |
| Canonical name | `kw-engineering-deploy-checklist` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: deploy-checklist
name: kw-engineering-deploy-checklist
description: Pre-deployment verification checklist. Use when about to ship a release, deploying a change with database migrations or feature flags, verifying CI status and approvals before going to production, or documenting rollback triggers ahead of time.
argument-hint: "[service or release name]"
---

# /deploy-checklist

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Generate a pre-deployment checklist to verify readiness before shipping.

## Usage

```
/deploy-checklist $ARGUMENTS
```

## Output

```markdown
## Deploy Checklist: [Service/Release]
**Date:** [Date] | **Deployer:** [Name]

### Pre-Deploy
- [ ] All tests passing in CI
- [ ] Code reviewed and approved
- [ ] No known critical bugs in release
- [ ] Database migrations tested (if applicable)
- [ ] Feature flags configured (if applicable)
- [ ] Rollback plan documented
- [ ] On-call team notified

### Deploy
- [ ] Deploy to staging and verify
- [ ] Run smoke tests
- [ ] Deploy to production (canary if available)
- [ ] Monitor error rates and latency for 15 min
- [ ] Verify key user flows

### Post-Deploy
- [ ] Confirm metrics are nominal
- [ ] Update release notes / changelog
- [ ] Notify stakeholders
- [ ] Close related tickets

### Rollback Triggers
- Error rate exceeds [X]%
- P50 latency exceeds [X]ms
- [Critical user flow] fails
```

## Customization

Tell me about your deploy and I'll customize the checklist:
- "We use feature flags" → adds flag verification steps
- "This includes a database migration" → adds migration-specific checks
- "This is a breaking API change" → adds consumer notification steps

## If Connectors Available

If **~~source control** is connected:
- Pull the release diff and list of changes
- Verify all PRs are approved and merged

If **~~CI/CD** is connected:
- Check build and test status automatically
- Verify pipeline is green before deploy

If **~~monitoring** is connected:
- Pre-fill rollback trigger thresholds from current baselines
- Set up post-deploy metric watch

## Tips

1. **Run before every deploy** — Even routine ones. Checklists prevent "I forgot to..."
2. **Customize once, reuse** — Tell me your stack and I'll remember your deploy process.
3. **Include rollback criteria** — Decide when to roll back before you deploy, not during.

