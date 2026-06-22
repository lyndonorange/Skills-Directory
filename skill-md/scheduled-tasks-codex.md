---
name: scheduled-tasks
display_name: scheduled-tasks
platform: Codex
category: General and specialized workflows
---

# scheduled-tasks - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `scheduled-tasks` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use the `scheduler` tool to manage saved tasks. Always inspect existing tasks before creating, updating, deleting, or running one.

## How To Use It In Codex

In Codex, click the chat box, press /, choose scheduled-tasks, then write the task. Fallback prompt: Use the scheduled-tasks skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `scheduled-tasks` |
| Canonical name | `scheduled-tasks` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use the `scheduler` tool to manage saved tasks. Always inspect existing tasks before creating, updating, deleting, or running one.

## Original SKILL.md

---
name: scheduled-tasks
description: Use for complex Agent Zero scheduler work, including creating, updating, deleting, running, waiting for, timezone-correcting, or auditing scheduled, planned, and adhoc tasks.
---

# Scheduler Tasks

Use the `scheduler` tool to manage saved tasks. Always inspect existing tasks before creating, updating, deleting, or running one.

## Actions

- `list_tasks`: optional `state[]`, `type[]`, `next_run_within`, `next_run_after`
- `find_task_by_name`: `name`
- `show_task`: `uuid`
- `run_task`: `uuid`, optional `context`
- `update_task`: `uuid`, optional `name`, `system_prompt`, `prompt`, `attachments[]`, `schedule`, `timezone`, `plan[]`, `state`, `dedicated_context`
- `delete_task`: `uuid`
- `create_scheduled_task`: `name`, `system_prompt`, `prompt`, optional `attachments[]`, `schedule`, `timezone`, `dedicated_context`
- `create_adhoc_task`: `name`, `system_prompt`, `prompt`, optional `attachments[]`, `dedicated_context`
- `create_planned_task`: `name`, `system_prompt`, `prompt`, optional `attachments[]`, `plan[]`, `dedicated_context`
- `wait_for_task`: `uuid`

## Schedule Fields

Schedules use cron-like fields. Do not put ISO datetimes into `schedule`.

- `minute`
- `hour`
- `day`
- `month`
- `weekday`
- `timezone`

Use IANA timezones such as `Europe/Rome`. Omit timezone to use the current user timezone. Planned task datetimes go in `plan`, not `schedule`, and should be ISO strings such as `2026-05-09T18:25:00`.

For one future reminder, prefer `create_planned_task` with:

```json
{
  "action": "create_planned_task",
  "name": "drink water",
  "prompt": "Remind the user to drink water.",
  "plan": ["2026-05-11T09:15:00"],
  "dedicated_context": true
}
```

For a recurring or cron-shaped scheduled task, use `create_scheduled_task` with:

```json
{
  "action": "create_scheduled_task",
  "name": "weekday stretch",
  "prompt": "Remind the user to stretch.",
  "schedule": {
    "minute": "15",
    "hour": "9",
    "day": "*",
    "month": "*",
    "weekday": "1-5",
    "timezone": "Europe/Rome"
  },
  "dedicated_context": true
}
```

## Safety

- Do not create recursive task prompts that schedule more tasks.
- Do not run a task just because it is scheduled; run only if the user asks.
- Created tasks use a dedicated context unless `dedicated_context` is explicitly `false`.
- For destructive operations, identify the task by UUID after lookup.

## Example

```json
{
  "tool_name": "scheduler",
  "tool_args": {
    "action": "find_task_by_name",
    "name": "daily backup"
  }
}
```

