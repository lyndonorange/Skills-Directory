---
name: bmad-edit-prd
display_name: bmad-edit-prd
platform: OpenCode
category: General and specialized workflows
---

# bmad-edit-prd - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `bmad-edit-prd` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

'DEPRECATED — consolidated into bmad-prd update intent - this skill will be removed in v7 in favor of `bmad-prd`.'

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the bmad-edit-prd skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `bmad-edit-prd` |
| Canonical name | `bmad-edit-prd` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

'DEPRECATED — consolidated into bmad-prd update intent - this skill will be removed in v7 in favor of `bmad-prd`.'


## Original SKILL.md

---
name: bmad-edit-prd
description: 'DEPRECATED — consolidated into bmad-prd update intent - this skill will be removed in v7 in favor of `bmad-prd`.'
---

# DEPRECATED — forwards to bmad-prd (update intent)

This skill was consolidated into `bmad-prd`. It is retained as a thin compatibility shim so existing invocations by name and `_bmad/custom/bmad-edit-prd.toml` override files keep working. New work should invoke `bmad-prd` directly — it detects create / update / validate intent from the conversation.

## On Activation

1. Resolve customization: `python3 {project-root}/_bmad/scripts/resolve_customization.py --skill {skill-root} --key workflow`. This picks up any `{project-root}/_bmad/custom/bmad-edit-prd.toml` and `bmad-edit-prd.user.toml` overrides for the legacy fields (`activation_steps_prepend`, `activation_steps_append`, `persistent_facts`, `on_complete`).

2. Load `{project-root}/_bmad/bmm/config.yaml` (and `config.user.yaml` if present) to resolve `{user_name}` and `{communication_language}`.

3. Emit a deprecation notice to the user in `{communication_language}`:

   > Notice: `bmad-edit-prd` is deprecated and will be removed in a future release. It now forwards to `bmad-prd` with update intent. To silence this notice and access the full new customization surface (`prd_template`, `validation_checklist`, `doc_standards`, `external_sources`, `external_handoffs`, `output_dir`, `output_folder_name`), migrate `_bmad/custom/bmad-edit-prd.toml` to `_bmad/custom/bmad-prd.toml` and invoke `bmad-prd` directly next time. Customization fields that were in this version still remain in the new version and will be respected if present in `_bmad/custom/bmad-prd.toml`, but the new version also supports additional fields that you can take advantage of by migrating.

4. Invoke `bmad-prd` with the following context. Pass these as the activating context so `bmad-prd` honors them instead of resolving its own customization from scratch:

   - **Intent:** `update` — skip `bmad-prd`'s usual intent detection step.
   - **Pre-resolved legacy customization** — use these in place of resolving from `bmad-prd`'s own `customize.toml` for the four legacy fields. For everything else (`prd_template`, `validation_checklist`, `validation_report_template`, `doc_standards`, `output_dir`, `output_folder_name`, `external_sources`, `external_handoffs`), use `bmad-prd`'s own defaults and overrides as normal:
     - `activation_steps_prepend` = the resolved value from step 1
     - `activation_steps_append` = the resolved value from step 1
     - `persistent_facts` = the resolved value from step 1
     - `on_complete` = the resolved value from step 1
   - **Original user input:** forward whatever the user said when invoking this skill verbatim (the target PRD path, the change signal, etc.).

   `bmad-prd` takes the workflow from here. Do not execute any further steps in this shim.
