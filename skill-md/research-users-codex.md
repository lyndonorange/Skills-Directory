---
name: pm-skills-research-users
display_name: research-users
platform: Codex
category: Business creation, ideas, and validation
---

# research-users - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `research-users` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- **Name**: research-users

## How To Use It In Codex

In Codex, click the chat box, press /, choose research-users, then write the task. Fallback prompt: Use the research-users skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `research-users` |
| Canonical name | `pm-skills-research-users` |
| Platform | `Codex` |
| Category | Business creation, ideas, and validation |

## Description

- **Name**: research-users

## Original SKILL.md

---
name: pm-skills-research-users
description: "Synthesize raw user research into actionable personas, behavioral segments, and customer journey maps. Use with survey data, interview notes, feedback, support tickets, analytics, NPS, satisfaction data, or a product description for exploratory user research."
---
# Research Users

## Metadata
- **Name**: research-users
- **Description**: Turn raw research data into actionable user personas, behavioral segments, and customer journey maps.
- **Invocation**: `/research-users [survey results, interview notes, feedback data, support tickets, analytics, or product description]`
- **Related skills**: `pm-skills-user-personas`, `pm-skills-user-segmentation`, `pm-skills-market-segments`, `pm-skills-customer-journey-map`, `pm-skills-discover-journey-map`, `pm-skills-sentiment-analysis`, `pm-skills-interview-script`, `pm-skills-value-proposition`
- **Category**: Business creation, ideas, and validation

## When To Use

Use this skill when the user wants to understand who their users are, how users differ, where users struggle, what users value, or how research should inform product, positioning, pricing, onboarding, or roadmap decisions.

Example invocations:

- `/research-users [upload survey results, interview notes, or feedback data]`
- `/research-users B2B project management tool for agencies -- help me understand our users`
- `/research-users [paste user feedback or support ticket data]`

## Workflow

### Step 1: Accept Research Inputs

Accept any combination of:

- Survey responses: CSV, spreadsheet, or pasted text
- Interview notes or transcripts
- Support tickets or feature requests
- Product analytics or behavioral data
- NPS or satisfaction data
- Product description for exploratory research without direct data

Ask only for missing context:

- What research do you have, and what format is it in?
- What do you want to understand: who users are, how they differ, where friction appears, or what they value?
- What decision will this inform: roadmap, positioning, pricing, onboarding, segmentation, or something else?

If data is thin, be explicit about confidence. Five interviews produce hypotheses, not conclusions.

### Step 2: Build Personas

Apply `pm-skills-user-personas`:

- Identify 3-4 distinct personas from the data
- For each persona: name, role, goals, JTBD, pains, gains, and behavioral patterns
- Include unexpected insights from the data
- Estimate persona prevalence when the data supports it

Personas must influence decisions. Avoid decorative personas.

### Step 3: Segment Users

Apply `pm-skills-user-segmentation` and `pm-skills-market-segments`:

- Create behavioral segments, not only demographic segments
- For each segment: size, JTBD, product fit, willingness to pay, and engagement level
- Identify the highest-value segment and highest-growth segment
- Map segments to personas and show overlap

Behavioral segments are usually more actionable than demographic segments for product decisions.

### Step 4: Map The Customer Journey

Apply `pm-skills-customer-journey-map` or `pm-skills-discover-journey-map`:

- Map the journey: Awareness -> Consideration -> Onboarding -> Active Use -> Expansion -> Advocacy
- For each stage: touchpoints, emotions, pain points, and aha moments
- Identify the biggest drop-off points
- Highlight moments of delight worth amplifying

The journey map should surface emotions, not just actions.

### Step 5: Generate Research Report

Save or present the output as Markdown.

```markdown
# User Research Report: [Product]

**Date**: [today]
**Data sources**: [what was analyzed]
**Sample size**: [if applicable]

## Executive Summary
[3-5 sentences: key findings and implications]

## Personas

### Persona 1: [Name] -- "[Quote that captures them]"
- **Who**: [role, context, experience level]
- **Primary JTBD**: [When..., I want to..., so I can...]
- **Key pains**: [top 3]
- **Key gains**: [what delights them]
- **Behavioral pattern**: [how they use the product]
- **Prevalence**: [X% of user base]

[Repeat for each persona]

## User Segments

| Segment | Size | Primary JTBD | Product Fit | Value | Growth |
| --- | --- | --- | --- | --- | --- |

## Customer Journey Map

| Stage | Touchpoints | Emotion | Pain Points | Opportunities |
| --- | --- | --- | --- | --- |

## Key Insights

1. [Insight with supporting evidence]
2. [Insight with supporting evidence]

## Recommendations

1. [Actionable recommendation tied to findings]
2. [Actionable recommendation tied to findings]

## Open Questions

[What the data did not answer and suggested follow-up research]
```

### Step 6: Offer Next Steps

Offer one to four useful continuations:

- "Want me to create interview scripts to go deeper on a specific persona?"
- "Should I analyze sentiment across these segments?"
- "Want me to build a value proposition for the top persona?"
- "Should I prioritize the journey map pain points as feature opportunities?"

## Quality Bar

- Be transparent about confidence levels when data is thin.
- Make personas useful for product decisions, not decorative.
- Prefer behavioral segmentation over demographic segmentation.
- Capture user emotions in the journey map.
- If no data is provided, generate research-informed hypotheses and recommend how to validate them.

