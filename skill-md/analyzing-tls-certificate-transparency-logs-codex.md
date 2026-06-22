---
name: analyzing-tls-certificate-transparency-logs
display_name: analyzing-tls-certificate-transparency-logs
platform: Codex
category: Security, forensics, and incident response
---

# analyzing-tls-certificate-transparency-logs - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `analyzing-tls-certificate-transparency-logs` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When investigating security incidents that require analyzing tls certificate transparency logs

## How To Use It In Codex

In Codex, click the chat box, press /, choose analyzing-tls-certificate-transparency-logs, then write the task. Fallback prompt: Use the analyzing-tls-certificate-transparency-logs skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `analyzing-tls-certificate-transparency-logs` |
| Canonical name | `analyzing-tls-certificate-transparency-logs` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When investigating security incidents that require analyzing tls certificate transparency logs

## Original SKILL.md

---
name: analyzing-tls-certificate-transparency-logs
description: 'Queries Certificate Transparency logs via crt.sh and pycrtsh to detect
  phishing domains, unauthorized certificate issuance, and shadow IT. Monitors newly
  issued certificates for typosquatting and brand impersonation using Levenshtein
  distance. Use for proactive phishing domain detection and certificate monitoring.

  '
domain: cybersecurity
subdomain: security-operations
tags:
- certificate-transparency
- ct-logs
- crt-sh
- phishing-detection
- tls-monitoring
- security-operations
version: '1.0'
author: mahipal
license: Apache-2.0
atlas_techniques:
- AML.T0073
- AML.T0052
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1583.001
- T1566.002
- T1598.003
- T1583.006
---

# Analyzing TLS Certificate Transparency Logs


## When to Use

- When investigating security incidents that require analyzing tls certificate transparency logs
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Query crt.sh Certificate Transparency database to find certificates issued for
domains similar to your organization's brand, detecting phishing infrastructure.

```python
from pycrtsh import Crtsh

c = Crtsh()
# Search for certificates matching a domain
certs = c.search("example.com")
for cert in certs:
    print(cert["id"], cert["name_value"])

# Get full certificate details
details = c.get(certs[0]["id"], type="id")
```

Key analysis steps:
1. Query crt.sh for all certificates matching your domain pattern
2. Identify certificates with typosquatting variations (Levenshtein distance)
3. Flag certificates from unexpected CAs
4. Monitor for wildcard certificates on suspicious subdomains
5. Cross-reference with known phishing infrastructure

## Examples

```python
from pycrtsh import Crtsh
c = Crtsh()
certs = c.search("%.example.com")
for cert in certs:
    print(f"Issuer: {cert.get('issuer_name')}, Domain: {cert.get('name_value')}")
```

