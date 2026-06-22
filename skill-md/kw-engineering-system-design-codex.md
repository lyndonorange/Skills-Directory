---
name: kw-engineering-system-design
display_name: kw-engineering-system-design
platform: Codex
category: General and specialized workflows
---

# kw-engineering-system-design - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-system-design` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Help design systems and evaluate architectural decisions.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-system-design, then write the task. Fallback prompt: Use the kw-engineering-system-design skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-system-design` |
| Canonical name | `kw-engineering-system-design` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Help design systems and evaluate architectural decisions.

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: system-design
name: kw-engineering-system-design
description: Design systems, services, and architectures. Trigger with "design a system for", "how should we architect", "system design for", "what's the right architecture for", or when the user needs help with API design, data modeling, or service boundaries.
---

# System Design

Help design systems and evaluate architectural decisions.

## Framework

### 1. Requirements Gathering
- Functional requirements (what it does)
- Non-functional requirements (scale, latency, availability, cost)
- Constraints (team size, timeline, existing tech stack)

### 2. High-Level Design
- Component diagram
- Data flow
- API contracts
- Storage choices

### 3. Deep Dive
- Data model design
- API endpoint design (REST, GraphQL, gRPC)
- Caching strategy
- Queue/event design
- Error handling and retry logic

### 4. Scale and Reliability
- Load estimation
- Horizontal vs. vertical scaling
- Failover and redundancy
- Monitoring and alerting

### 5. Trade-off Analysis
- Every decision has trade-offs. Make them explicit.
- Consider: complexity, cost, team familiarity, time to market, maintainability

## Output

Produce clear, structured design documents with diagrams (ASCII or described), explicit assumptions, and trade-off analysis. Always identify what you'd revisit as the system grows.

