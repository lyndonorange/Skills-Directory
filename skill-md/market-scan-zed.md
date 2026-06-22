---
name: pm-skills-market-scan
display_name: market-scan
platform: Zed
category: Business creation, ideas, and validation
---

# market-scan - Zed Skill Package

## What This Is

This is a friend-safe Markdown copy of `market-scan` for Zed. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- **Name**: market-scan

## How To Use It In Zed

In Zed, open the Agent panel and type: Use the market-scan skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `market-scan` |
| Canonical name | `pm-skills-market-scan` |
| Platform | `Zed` |
| Category | Business creation, ideas, and validation |

## Description

- **Name**: market-scan

## Original SKILL.md

---
name: pm-skills-market-scan
description: "Run a strategic market scan by combining SWOT, PESTLE, Porter's Five Forces, and Ansoff Matrix analysis into one macro environment and competitive strategy overview. Use for market entry, board strategy review, investor prep, annual planning, or understanding a product's strategic environment."
---
# Market Scan

## Metadata
- **Name**: market-scan
- **Description**: Run multiple strategic analysis frameworks to understand a competitive and macro environment.
- **Invocation**: `/market-scan [market, company, product, or uploaded brief]`
- **Related skills**: `pm-skills-swot-analysis`, `pm-skills-pestle-analysis`, `pm-skills-porters-five-forces`, `pm-skills-ansoff-matrix`
- **Category**: Business creation, ideas, and validation

## When To Use

Use this skill when the user wants to understand a market, product category, competitive environment, or macro strategic situation. Typical prompts:

- `/market-scan EdTech market for corporate learning`
- `/market-scan [upload a market brief or strategy doc]`
- `/market-scan Our fintech product -- preparing for board strategy review`

Use web research when current market conditions, regulations, competitors, or trend data matter. Do not rely only on generic strategic-framework knowledge when the user asks about a real current market.

## Workflow

### Step 1: Understand The Context

Ask only for missing information:

- What product, company, or market are we analyzing?
- What is the purpose: strategic planning, market entry, investor prep, board review, annual review, or something else?
- Should all four frameworks run, or should any framework be emphasized?
- What is the current position in this market?

If the user provided a brief, strategy doc, or enough context, proceed without unnecessary questions.

### Step 2: Run The Analysis

Apply these frameworks in sequence, letting each framework build on the prior findings:

1. **SWOT Analysis** using `pm-skills-swot-analysis`
   - Internal strengths and weaknesses
   - External opportunities and threats
   - Actionable recommendations for each quadrant

2. **PESTLE Analysis** using `pm-skills-pestle-analysis`
   - Political, Economic, Social, Technological, Legal, and Environmental factors
   - Impact, trend direction, and timeframe for each factor
   - Specific regulations, market data, and trend signals when available

3. **Porter's Five Forces** using `pm-skills-porters-five-forces`
   - Competitive rivalry
   - Supplier power
   - Buyer power
   - Threat of substitutes
   - Threat of new entrants
   - Overall industry attractiveness rating

4. **Ansoff Matrix** using `pm-skills-ansoff-matrix`
   - Market penetration
   - Market development
   - Product development
   - Diversification
   - Risk-adjusted growth opportunities

### Step 3: Synthesize Across Frameworks

Cross-reference findings across all frameworks:

- **Converging signals**: what multiple frameworks agree on
- **Strategic imperatives**: actions that appear critical across analyses
- **Key risks**: threats and forces to mitigate
- **Growth opportunities**: best risk-adjusted opportunities

The synthesis is the most valuable section. Make the frameworks talk to each other rather than presenting four disconnected analyses.

### Step 4: Generate The Report

Save or present the output as Markdown.

```markdown
# Strategic Market Scan: [Market/Product]

**Date**: [today]
**Purpose**: [strategic planning / market entry / investor prep / board review / annual review]

## Executive Summary
[5-7 sentences covering the strategic situation and key recommendations]

## SWOT Analysis

| Strengths | Weaknesses |
| --- | --- |
| [internal positives] | [internal negatives] |

| Opportunities | Threats |
| --- | --- |
| [external positives] | [external negatives] |

**SWOT Actions**: [leverage S+O, mitigate W+T]

## PESTLE Analysis

| Factor | Current State | Impact | Trend | Timeframe |
| --- | --- | --- | --- | --- |

## Porter's Five Forces

| Force | Intensity | Key Drivers | Implications |
| --- | --- | --- | --- |

**Industry Attractiveness**: [High / Medium / Low]

## Ansoff Growth Matrix

| Strategy | Opportunity | Risk Level | Investment | Priority |
| --- | --- | --- | --- | --- |
| Market Penetration | [specifics] | Low | [est.] | [H/M/L] |
| Market Development | [specifics] | Medium | [est.] | [H/M/L] |
| Product Development | [specifics] | Medium | [est.] | [H/M/L] |
| Diversification | [specifics] | High | [est.] | [H/M/L] |

## Cross-Framework Synthesis

**Converging signals**: [what all frameworks agree on]

**Strategic imperatives**: [must-do actions]

**Key risks**: [highest-priority threats]

**Best opportunities**: [risk-adjusted growth plays]

## Strategic Recommendations

1. [Recommendation with supporting evidence from multiple frameworks]
2. [Recommendation with supporting evidence from multiple frameworks]
3. [Recommendation with supporting evidence from multiple frameworks]

## Monitoring Plan

| Signal | What to Watch | Source | Check Frequency |
| --- | --- | --- | --- |
```

### Step 5: Offer Next Steps

Close by offering one to three concrete continuations:

- "Want me to build a product strategy based on these findings?"
- "Should I analyze specific competitors identified in Porter's analysis?"
- "Want me to design a pricing strategy for the market penetration opportunity?"

## Quality Bar

- Ground the analysis in current market data when the market is real and time-sensitive.
- Make PESTLE factors specific: regulations, market data, and trend signals, not generic observations.
- Make Porter's Five Forces concrete by naming specific forces, players, substitutes, and barriers.
- Make Ansoff opportunities specific enough to evaluate, not generic "enter new markets" statements.
- Treat the synthesis as the main deliverable.

