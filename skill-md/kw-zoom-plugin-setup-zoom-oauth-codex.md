---
name: kw-zoom-plugin-setup-zoom-oauth
display_name: kw-zoom-plugin-setup-zoom-oauth
platform: Codex
category: General and specialized workflows
---

# kw-zoom-plugin-setup-zoom-oauth - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-zoom-plugin-setup-zoom-oauth` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use this skill when auth is the blocker or when auth choices will shape the entire integration.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-zoom-plugin-setup-zoom-oauth, then write the task. Fallback prompt: Use the kw-zoom-plugin-setup-zoom-oauth skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-zoom-plugin-setup-zoom-oauth` |
| Canonical name | `kw-zoom-plugin-setup-zoom-oauth` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use this skill when auth is the blocker or when auth choices will shape the entire integration.

## Original SKILL.md

---
knowledge-work-plugin: zoom-plugin
upstream-skill: setup-zoom-oauth
name: kw-zoom-plugin-setup-zoom-oauth
description: Implement Zoom authentication correctly. Use when setting up app credentials, choosing an OAuth grant, requesting scopes, handling token refresh, or debugging auth failures.
---

# /setup-zoom-oauth

Use this skill when auth is the blocker or when auth choices will shape the entire integration.

## Scope

- App type selection
- OAuth grant selection
- Scope planning
- Token exchange and refresh
- Auth debugging and environment assumptions

## Workflow

1. Determine the app model and who is authorizing whom.
2. Choose the correct grant flow.
3. Identify minimum scopes for the user flow.
4. Define token storage and refresh behavior.
5. Route into the deepest relevant reference docs only after the above is clear.

## Primary References

- [oauth](../oauth/SKILL.md)
- [general](../general/SKILL.md)
- [rest-api](../rest-api/SKILL.md)

## Common Mistakes

- Picking a grant before clarifying the actor and tenant model
- Asking for broad scopes before confirming the exact workflow
- Forgetting refresh-token behavior and token lifecycle handling
- Reusing an old refresh token after a successful refresh instead of storing the newly returned one
- Treating auth failures as API failures without checking app configuration first

