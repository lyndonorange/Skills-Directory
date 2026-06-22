---
name: performing-osint-with-spiderfoot
display_name: performing-osint-with-spiderfoot
platform: Codex
category: Security, forensics, and incident response
---

# performing-osint-with-spiderfoot - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-osint-with-spiderfoot` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

SpiderFoot is an open-source OSINT automation tool with 200+ modules that integrates with data sources for threat intelligence and attack surface mapping. This skill uses the SpiderFoot REST API and CLI (sf.py/spiderfoot

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-osint-with-spiderfoot, then write the task. Fallback prompt: Use the performing-osint-with-spiderfoot skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-osint-with-spiderfoot` |
| Canonical name | `performing-osint-with-spiderfoot` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

SpiderFoot is an open-source OSINT automation tool with 200+ modules that integrates with data sources for threat intelligence and attack surface mapping. This skill uses the SpiderFoot REST API and CLI (sf.py/spiderfoot

## Original SKILL.md

---
name: performing-osint-with-spiderfoot
description: Automate OSINT collection using SpiderFoot REST API and CLI for target
  profiling, module-based reconnaissance, and structured result analysis across 200+
  data sources
domain: cybersecurity
subdomain: threat-intelligence
tags:
- osint
- spiderfoot
- reconnaissance
- threat-intelligence
- attack-surface
- target-profiling
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- ID.RA-01
- ID.RA-05
- DE.CM-01
- DE.AE-02
mitre_attack:
- T1591
- T1592
- T1593
- T1589
- T1595
---

# Performing OSINT with SpiderFoot

## Overview

SpiderFoot is an open-source OSINT automation tool with 200+ modules that integrates with data sources for threat intelligence and attack surface mapping. This skill uses the SpiderFoot REST API and CLI (sf.py/spiderfoot-cli) to create and manage scans, select modules by use case (footprint, investigate, passive), parse structured results for domains, IPs, email addresses, leaked credentials, and DNS records, and generate target intelligence profiles.


## When to Use

- When conducting security assessments that involve performing osint with spiderfoot
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- SpiderFoot 4.0+ installed or SpiderFoot HX cloud account
- Python 3.8+ with requests library
- SpiderFoot server running on default port 5001
- Optional: API keys for VirusTotal, Shodan, HaveIBeenPwned modules

## Steps

1. Connect to SpiderFoot REST API or use CLI interface
2. Create a new scan with target specification (domain, IP, email, name)
3. Select scan modules by use case (all, footprint, investigate, passive)
4. Monitor scan progress via API polling
5. Retrieve and parse scan results by data element type
6. Extract key findings: subdomains, IPs, emails, leaked credentials
7. Generate structured OSINT intelligence report

## Expected Output

JSON report containing OSINT findings organized by data type (domains, IPs, emails, credentials, DNS records), module source attribution, and target profile summary with risk indicators.

