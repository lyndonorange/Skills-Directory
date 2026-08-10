---
name: ocf-start
display_name: ocf-start
platform: OpenCode
category: General and specialized workflows
---

# ocf-start - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `ocf-start` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill for Open Career Format career materials, especially improving resumes, cover letters, LinkedIn/profile content, targeted job applications, and durable candidate-master OCF files. Use when the user asks to

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the ocf-start skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `ocf-start` |
| Canonical name | `ocf-start` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Use this skill for Open Career Format career materials, especially improving resumes, cover letters, LinkedIn/profile content, targeted job applications, and durable candidate-master OCF files. Use when the user asks to


## Original SKILL.md

---
name: ocf-start
description: Use this skill for Open Career Format career materials, especially improving resumes, cover letters, LinkedIn/profile content, targeted job applications, and durable candidate-master OCF files. Use when the user asks to make a resume better, tailor a resume to a job, create a cover letter, organize career evidence, or build/update an OCF career workspace.
---

# Open Career Format Start

Use this skill to run an Open Career Format (OCF) career session. OCF turns resume, profile, job-description, and career-story material into a durable candidate-owned evidence base that can be reused across targeted applications.

Primary local workflow:

1. If the user provides a resume and job description, use only [prompts/application-bootstrap.md](prompts/application-bootstrap.md) unless they ask for a broader OCF workflow.
2. First give the gap read:
   - what the job asks for
   - what the resume proves
   - what is missing or under-evidenced
3. Ask no more than three targeted questions before drafting.
4. After the user answers, draft the targeted resume and cover letter.
5. Before creating or updating an OCF file, ask for one story about their work that they would never put on a formal resume.
6. Preserve that story in the user's own words.
7. Create a `candidate-master` OCF file or a proposed OCF update set for next time.
8. Remind the user to save the OCF file next to their resume.

Do not search for general prompt-writing, resume, schema, or background advice unless the user asks.

## Routing

- Targeted application from resume plus job description: use [prompts/application-bootstrap.md](prompts/application-bootstrap.md).
- OCF field writing, evidence capture, and profile authoring: use [prompts/authoring.md](prompts/authoring.md).
- Resume/profile/job-specific selection and trimming: use [prompts/curation.md](prompts/curation.md).
- General career coaching and story practice: use [prompts/coaching.md](prompts/coaching.md).
- Operational job-search workflow, including live job discovery, posting evaluation, tailored application artifacts, outcome tracking, and tracked interview context: use `$job-application-assistant`.
- Full interview prep with company/interviewer research, prep kit, and mock interview: use `$interview-prep-coach`, optionally after `$job-application-assistant` loads the tracked application evidence.

Keep career facts evidence-based. Do not invent employers, degrees, titles, dates, certifications, metrics, or anecdotes. If a claim would materially strengthen the application but is not proved, mark it as a question or candidate hypothesis.

## Local Files

- Upstream source skill: [references/upstream-SKILL.md](references/upstream-SKILL.md)
- OCF schema: [references/schema.json](references/schema.json)

When creating OCF JSON, prefer the schema in `references/schema.json` and keep raw sensitive artifacts out of the file unless the user explicitly asks to include them.
