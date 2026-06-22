---
name: pm-skills-prioritize-assumptions
display_name: prioritize-assumptions
platform: Universal Agents
category: Business creation, ideas, and validation
---

# prioritize-assumptions - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `prioritize-assumptions` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

name: pm-skills-prioritize-assumptions

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the prioritize-assumptions skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `prioritize-assumptions` |
| Canonical name | `pm-skills-prioritize-assumptions` |
| Platform | `Universal Agents` |
| Category | Business creation, ideas, and validation |

## Description

name: pm-skills-prioritize-assumptions

## Original SKILL.md

---
name: pm-skills-prioritize-assumptions
description: "Prioritize assumptions using an Impact × Risk matrix and suggest experiments for each. Use when triaging a list of assumptions, deciding what to test first, or applying the assumption prioritization canvas."
---

## Prioritize Assumptions

Triage assumptions using an Impact × Risk matrix and suggest targeted experiments.

### Context

You are helping prioritize assumptions for **$ARGUMENTS**.

If the user provides files with assumptions or research data, read them first.

### Domain Context

**ICE** works well for assumption prioritization: Impact (Opportunity Score × # Customers) × Confidence (1–10) × Ease (1–10). Opportunity Score = Importance × (1 − Satisfaction), normalized to 0–1 (Dan Olsen). **RICE** splits Impact into Reach × Impact separately: (R × I × C) / E. See the `prioritization-frameworks` skill for full formulas and templates.

### Instructions

The user will provide a list of assumptions to prioritize. Apply the following framework:

1. **For each assumption**, evaluate two dimensions:
   - **Impact**: The value created by validating this assumption AND the number of customers affected (in ICE: Impact = Opportunity Score × # Customers)
   - **Risk**: Defined as (1 - Confidence) × Effort

2. **Categorize each assumption** using the Impact × Risk matrix:
   - **Low Impact, Low Risk** → Defer testing until higher-priority assumptions are addressed
   - **High Impact, Low Risk** → Proceed to implementation (low risk, high reward)
   - **Low Impact, High Risk** → Reject the idea (not worth the investment)
   - **High Impact, High Risk** → Design an experiment to test it

3. **For each assumption requiring testing**, suggest an experiment that:
   - Maximizes validated learning with minimal effort
   - Measures actual behavior, not opinions
   - Has a clear success metric and threshold

4. **Present results** as a prioritized matrix or table.

Think step by step. Save as markdown if the output is substantial.

---

### Further Reading

- [Assumption Prioritization Canvas: How to Identify And Test The Right Assumptions](https://www.productcompass.pm/p/assumption-prioritization-canvas)
- [Continuous Product Discovery Masterclass (CPDM)](https://www.productcompass.pm/p/cpdm) (video course)

