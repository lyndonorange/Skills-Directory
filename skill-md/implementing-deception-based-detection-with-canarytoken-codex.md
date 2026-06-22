---
name: implementing-deception-based-detection-with-canarytoken
display_name: implementing-deception-based-detection-with-canarytoken
platform: Codex
category: General and specialized workflows
---

# implementing-deception-based-detection-with-canarytoken - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `implementing-deception-based-detection-with-canarytoken` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Canary Tokens are lightweight tripwire mechanisms that alert when an attacker accesses a resource. This skill uses the Thinkst Canary REST API to programmatically create tokens (web bugs, DNS tokens, MS Word documents, A

## How To Use It In Codex

In Codex, click the chat box, press /, choose implementing-deception-based-detection-with-canarytoken, then write the task. Fallback prompt: Use the implementing-deception-based-detection-with-canarytoken skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `implementing-deception-based-detection-with-canarytoken` |
| Canonical name | `implementing-deception-based-detection-with-canarytoken` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Canary Tokens are lightweight tripwire mechanisms that alert when an attacker accesses a resource. This skill uses the Thinkst Canary REST API to programmatically create tokens (web bugs, DNS tokens, MS Word documents, A

## Original SKILL.md

---
name: implementing-deception-based-detection-with-canarytoken
description: Deploy and monitor Canary Tokens via the Thinkst Canary API for deception-based
  breach detection using web bug tokens, DNS tokens, document tokens, and AWS key
  tokens.
domain: cybersecurity
subdomain: deception-technology
tags:
- canarytoken
- deception
- honeytokens
- breach-detection
- Thinkst-Canary
- tripwire
- early-warning
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- DE.AE-06
- PR.IR-01
mitre_attack:
- T1078
- T1190
- T1059
- T1078.004
- T1530
---

# Implementing Deception-Based Detection with Canarytoken

## Overview

Canary Tokens are lightweight tripwire mechanisms that alert when an attacker accesses a resource. This skill uses the Thinkst Canary REST API to programmatically create tokens (web bugs, DNS tokens, MS Word documents, AWS API keys), deploy them to strategic locations, monitor for triggered alerts, and generate deception coverage reports.


## When to Use

- When deploying or configuring implementing deception based detection with canarytoken capabilities in your environment
- When establishing security controls aligned to compliance requirements
- When building or improving security architecture for this domain
- When conducting security assessments that require this implementation

## Prerequisites

- Thinkst Canary Console or canarytokens.org account
- API auth token from Canary Console
- Python 3.9+ with `requests`
- File system access for deploying document and file tokens

## Steps

1. Authenticate to the Canary Console API using auth_token
2. Create web bug (HTTP) tokens for embedding in documents and web pages
3. Create DNS tokens for monitoring DNS resolution attempts
4. Create MS Word document tokens for file share deployment
5. List all active tokens and their trigger history
6. Query recent alerts for triggered token events
7. Generate deception coverage report with deployment recommendations

## Expected Output

- JSON report listing all deployed Canary Tokens, trigger history, alert details, and coverage analysis
- Deployment map showing token types across network segments

