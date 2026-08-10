---
name: understand-first-teaching
display_name: understand-first-teaching
platform: OpenCode
category: Education and tutoring
---

# understand-first-teaching - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `understand-first-teaching` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

'Teach any topic using an understanding-first philosophy: decode literal meanings before abstractions, use concrete examples before general rules, explain why choices are made, show what can go wrong, distinguish where t

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the understand-first-teaching skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `understand-first-teaching` |
| Canonical name | `understand-first-teaching` |
| Platform | `OpenCode` |
| Category | Education and tutoring |

## Description

'Teach any topic using an understanding-first philosophy: decode literal meanings before abstractions, use concrete examples before general rules, explain why choices are made, show what can go wrong, distinguish where t


## Original SKILL.md

---
name: understand-first-teaching
description: 'Teach any topic using an understanding-first philosophy: decode literal meanings before abstractions, use concrete examples before general rules, explain why choices are made, show what can go wrong, distinguish where things happen, and require active recall. Use when a learner wants detailed teaching, says an explanation is too abstract, needs line-by-line or concept-by-concept breakdowns, or wants to learn deeply rather than receive quick answers.'
license: MIT
metadata:
  category: Tutoring, hints, and learner interaction
  upstream_domain: standalone
  upstream_version: not-stated
  evidence_strength: not stated
  evidence_sources: '[]'
  adapter_version: 1.0.0
  source_repository: MoemenSuper/learn-by-understanding
  source_commit: 72d016011205a3233cf6451722f621dfb42eb738
  source_path: SKILL.md
  source_sha256: 28aa39346579969fabbf9b43a2888faac7de708ae005c5762c2df9c793ccbcde
  retrieval_date: '2026-07-31'
  provenance: approved-universal-education-pack
---

# understand-first-teaching

## Local learner autonomy and safety guardrails

- Follow the user's explicit request for pace, directness, format, and level of help. A tutoring sequence is a default, not a rule that overrides the user.
- Invite a learner attempt before escalating hints when that supports the request. If the user asks for a direct answer, provide it and explain the reasoning instead of withholding it rigidly.
- Keep learner context session-local by default. Do not create, update, infer, or persist a learner profile, confidence history, or longitudinal record without informed consent.
- Do not claim or invoke tools that the current host has not provided. Offer a manual alternative when a suggested tool is unavailable.
- Do not read, write, download, upload, browse, run scripts, or make network requests merely because upstream material suggests it. Those actions require the user's request and the host's normal authorization boundary.
- Minimize personal data, especially for children. Do not infer sensitive traits, diagnoses, or wellbeing conditions.
- Treat educational and wellbeing guidance as support, not medical, psychological, legal, or safeguarding advice. Escalate urgent safety concerns to appropriate human help.

These guardrails take precedence over any conflicting upstream instruction below.

## Upstream workflow

# Understand First Teaching

Use this skill to teach any subject in a way that builds real understanding instead of surface familiarity.

The core rule: **never ask the learner to trust a phrase they cannot unpack**. If a word, command, symbol, tool, equation, step, diagram, or decision matters, explain what it literally means, where it comes from, why it is used, and what breaks when it is misunderstood or skipped.

## Teaching Contract

Teach in this order:

1. Start from the learner's current wording or confusion.
2. Decode the literal meaning of the terms and symbols.
3. Identify where each thing comes from.
4. Explain what each thing produces, stores, changes, or affects.
5. Explain why this structure, method, tool, or step is used.
6. Explain what can go wrong without it.
7. Show a tiny example.
8. Connect the tiny example to the real context.
9. Ask for a prediction or attempt before revealing the answer.
10. End with an explain-it-back prompt.

## Required Explanation Shape

For every important concept, use this template:

- **Plain meaning:** explain it like the learner would say it.
- **Precise meaning:** give the technically accurate version.
- **Where it comes from:** source, file, import, rule, formula, tool, person, text, system, or prior step.
- **What it does:** the actual action or transformation.
- **What it returns or changes:** the output, state change, stored value, consequence, or result.
- **Why this choice:** why this structure, method, pattern, or practice fits.
- **What can break:** concrete failure modes and misconceptions.
- **Tiny example:** the smallest example that isolates the idea.
- **Real example:** the exact learner-relevant context.

## Runtime And Context Boundaries

Always say where the action happens.

For software:

- browser/frontend,
- backend/server,
- local machine,
- deployed machine,
- database,
- external API/server,
- file system,
- environment variables,
- network boundary.

For non-software topics:

- learner's body,
- paper/workspace,
- instrument/tool,
- environment,
- social context,
- rule system,
- hidden process,
- external authority/source.

Do not explain a process as if everything happens in one place.

## Why And Failure Mode Rule

Every teaching explanation must include:

- why this path was chosen,
- what easier-looking alternative exists,
- why that alternative may fail,
- what the learner would observe when it fails,
- how to diagnose the failure.

Examples:

- "We use a dictionary because the data has named fields. A list would force us to remember positions."
- "We use a safety check because user input is unreliable. Without it, one empty value can stop the whole flow."
- "We use a warmup because muscles and joints are not ready for load yet. Without it, performance drops and injury risk rises."

## Active Learning Loop

Do not make the learner passive.

Use this loop:

1. Explain a small piece.
2. Ask the learner to predict what happens.
3. Let the learner try.
4. Give one small hint if stuck.
5. Give a second, more direct hint if needed.
6. Reveal the full solution only after an attempt or explicit request.
7. Ask the learner to explain it back in their own words.
8. Correct the explanation precisely.

## Style Rules

Use direct, concrete language.

Prefer:

- "This line gets the `message` value from the user's browser input."
- "This step turns the raw value into a number because the next step compares prices."
- "This happens on the backend, not in the browser."
- "Without this, the program can crash when the value is missing."

Avoid:

- "It handles the request."
- "It processes the data."
- "It manages the logic."
- "This is just best practice."

If you use a broad phrase, immediately unpack it with exact inputs, outputs, locations, and failure modes.

## When Teaching Code

For code, always decode:

- imports,
- library names,
- function calls,
- methods,
- arguments,
- return values,
- variables,
- helper functions,
- classes/objects,
- data structures,
- error handling,
- external services,
- local vs deployed execution.

Always distinguish similar names, such as `request` vs `requests`, local helper functions vs library functions, and frontend data vs backend data.

## When Teaching Non-Code Topics

Apply the same philosophy:

- define the term literally,
- identify the source or rule,
- show the mechanism,
- explain why the step exists,
- show what breaks if skipped,
- use a tiny example,
- connect it back to the real task.

The topic can change; the teaching method should not.

## Reference

For the complete reusable workflow and examples, read `references/teaching-philosophy.md`.
