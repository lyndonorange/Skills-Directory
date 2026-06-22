---
name: performing-red-team-phishing-with-gophish
display_name: performing-red-team-phishing-with-gophish
platform: Codex
category: Security, forensics, and incident response
---

# performing-red-team-phishing-with-gophish - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-red-team-phishing-with-gophish` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

python scripts/agent.py --gophish-url https://localhost:3333 --api-key <key> --campaign-name "Q1 Awareness" --output phishing_report.json

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-red-team-phishing-with-gophish, then write the task. Fallback prompt: Use the performing-red-team-phishing-with-gophish skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-red-team-phishing-with-gophish` |
| Canonical name | `performing-red-team-phishing-with-gophish` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

python scripts/agent.py --gophish-url https://localhost:3333 --api-key <key> --campaign-name "Q1 Awareness" --output phishing_report.json

## Original SKILL.md

---
name: performing-red-team-phishing-with-gophish
description: Automate GoPhish phishing simulation campaigns using the Python gophish
  library. Creates email templates with tracking pixels, configures SMTP sending profiles,
  builds target groups from CSV, launches campaigns, and analyzes results including
  open rates, click rates, and credential submission statistics for security awareness
  assessment.
domain: cybersecurity
subdomain: security-operations
tags:
- red-teaming
- phishing-simulation
- gophish
- social-engineering
- campaign-automation
- security-awareness
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1078
- T1190
- T1059
- T1003
- T1110
---


## When to Use

- When conducting security assessments that involve performing red team phishing with gophish
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

1. Install dependencies: `pip install gophish requests`
2. Deploy GoPhish server and obtain an API key from Settings.
3. Use the Python gophish library to automate campaign setup:
   - Create email templates with HTML body and tracking
   - Configure SMTP sending profiles
   - Import target groups from CSV
   - Create landing pages for credential capture
   - Launch and monitor campaigns
4. Analyze campaign results: opens, clicks, submitted data, reported.

```bash
# For authorized penetration testing and lab environments only
python scripts/agent.py --gophish-url https://localhost:3333 --api-key <key> --campaign-name "Q1 Awareness" --output phishing_report.json
```

## Examples

### Create Campaign via API
```python
from gophish import Gophish
from gophish.models import Campaign, Template, Group, SMTP, Page
api = Gophish("api_key", host="https://localhost:3333", verify=False)  # Self-signed cert on localhost lab
campaign = Campaign(name="Q1 Test", groups=[Group(name="Sales Team")],
    template=Template(name="IT Password Reset"), smtp=SMTP(name="Internal SMTP"),
    page=Page(name="Credential Page"))
api.campaigns.post(campaign)
```

