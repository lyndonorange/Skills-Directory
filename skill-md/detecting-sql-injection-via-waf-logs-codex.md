---
name: detecting-sql-injection-via-waf-logs
display_name: detecting-sql-injection-via-waf-logs
platform: Codex
category: Security, forensics, and incident response
---

# detecting-sql-injection-via-waf-logs - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-sql-injection-via-waf-logs` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When investigating security incidents that require detecting sql injection via waf logs

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-sql-injection-via-waf-logs, then write the task. Fallback prompt: Use the detecting-sql-injection-via-waf-logs skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-sql-injection-via-waf-logs` |
| Canonical name | `detecting-sql-injection-via-waf-logs` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When investigating security incidents that require detecting sql injection via waf logs

## Original SKILL.md

---
name: detecting-sql-injection-via-waf-logs
description: Analyze WAF (ModSecurity/AWS WAF/Cloudflare) logs to detect SQL injection
  attack campaigns. Parses ModSecurity audit logs and JSON WAF event logs to identify
  SQLi patterns (UNION SELECT, OR 1=1, SLEEP(), BENCHMARK()), tracks attack sources,
  correlates multi-stage injection attempts, and generates incident reports with OWASP
  classification.
domain: cybersecurity
subdomain: security-operations
tags:
- waf-log-analysis
- sql-injection-detection
- modsecurity
- aws-waf
- cloudflare-waf
- web-application-security
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1190
- T1505.003
- T1059.007
---


# Detecting SQL Injection via WAF Logs


## When to Use

- When investigating security incidents that require detecting sql injection via waf logs
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

1. Install dependencies: `pip install requests`
2. Collect WAF logs (ModSecurity audit log, AWS WAF JSON logs, or Cloudflare firewall events).
3. Run the agent to parse and analyze:
   - Detect SQLi payloads via 15+ regex patterns
   - Classify attacks by OWASP injection type (classic, blind, time-based, UNION-based)
   - Identify persistent attackers by IP clustering
   - Correlate multi-request injection campaigns
   - Calculate attack success probability based on response codes

```bash
python scripts/agent.py --log-file /var/log/modsec_audit.log --format modsecurity --output sqli_report.json
```

## Examples

### ModSecurity SQLi Detection
```
Rule 942100 triggered: SQL Injection Attack Detected via libinjection
URI: /api/users?id=1' UNION SELECT username,password FROM users--
Source IP: 203.0.113.42 (47 requests in 5 minutes)
Classification: UNION-based SQLi campaign
```

