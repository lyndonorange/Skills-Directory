---
name: pm-skills-summarize-interview
display_name: summarize-interview
platform: Codex
category: Business creation, ideas, and validation
---

# summarize-interview - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `summarize-interview` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

name: pm-skills-summarize-interview

## How To Use It In Codex

In Codex, click the chat box, press /, choose summarize-interview, then write the task. Fallback prompt: Use the summarize-interview skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `summarize-interview` |
| Canonical name | `pm-skills-summarize-interview` |
| Platform | `Codex` |
| Category | Business creation, ideas, and validation |

## Description

name: pm-skills-summarize-interview

## Original SKILL.md

---
name: pm-skills-summarize-interview
description: "Summarize a customer interview transcript into a structured template with JTBD, satisfaction signals, and action items. Use when processing interview recordings or transcripts, synthesizing discovery interviews, or creating interview summaries."
---

## Summarize Customer Interview

Transform an interview transcript into a structured summary focused on Jobs to Be Done, satisfaction, and action items.

### Context

You are summarizing a customer interview for the product discovery of **$ARGUMENTS**.

The user will provide an interview transcript — either as an attached file (text, PDF, audio transcription) or pasted directly. Read any attached files first.

### Instructions

1. **Read the full transcript** carefully before summarizing.

2. **Fill in the summary template** below. Use "-" if information is unavailable. Replace numeric values with qualitative descriptions if needed (e.g., "not satisfied").

3. **Use clear, simple language** — a primary school graduate should be able to understand the summary.

### Output Template

```
**Date**: [Date and time of the interview]
**Participants**: [Full names and roles]
**Background**: [Background information about the customer]

**Current Solution**: [What solution they currently use]

**What They Like About Current Solution**:
- [Job to be done, desired outcome, importance, and satisfaction level]

**Problems With Current Solution**:
- [Job to be done, desired outcome, importance, and satisfaction level]

**Key Insights**:
- [Unexpected findings or notable quotes]

**Action Items**:
- [Date, Owner, Action — e.g., "2025-01-15, Paweł Huryn, Follow up with customer about pricing"]
```

Save the summary as a markdown document in the user's workspace.

---

### Further Reading

- [User Interviews: The Ultimate Guide to Research Interviews](https://www.productcompass.pm/p/interviewing-customers-the-ultimate)
- [Continuous Product Discovery Masterclass (CPDM)](https://www.productcompass.pm/p/cpdm) (video course)

