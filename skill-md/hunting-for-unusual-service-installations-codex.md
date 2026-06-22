---
name: hunting-for-unusual-service-installations
display_name: hunting-for-unusual-service-installations
platform: Codex
category: Security, forensics, and incident response
---

# hunting-for-unusual-service-installations - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `hunting-for-unusual-service-installations` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Attackers frequently install malicious Windows services for persistence and privilege escalation (MITRE ATT&CK T1543.003 — Create or Modify System Process: Windows Service). Event ID 7045 in the System event log records 

## How To Use It In Codex

In Codex, click the chat box, press /, choose hunting-for-unusual-service-installations, then write the task. Fallback prompt: Use the hunting-for-unusual-service-installations skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `hunting-for-unusual-service-installations` |
| Canonical name | `hunting-for-unusual-service-installations` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Attackers frequently install malicious Windows services for persistence and privilege escalation (MITRE ATT&CK T1543.003 — Create or Modify System Process: Windows Service). Event ID 7045 in the System event log records 

## Original SKILL.md

---
name: hunting-for-unusual-service-installations
description: Detect suspicious Windows service installations (MITRE ATT&CK T1543.003)
  by parsing System event logs for Event ID 7045, analyzing service binary paths,
  and identifying indicators of persistence mechanisms.
domain: cybersecurity
subdomain: threat-hunting
tags:
- threat-hunting
- T1543.003
- service-installation
- persistence
- Event-7045
- Sysmon
- Windows-services
version: '1.0'
author: mahipal
license: Apache-2.0
d3fend_techniques:
- Platform Hardening
- System Configuration Permissions
- Restore Object
- Restore Database
- Asset Inventory
nist_csf:
- DE.CM-01
- DE.AE-02
- DE.AE-07
- ID.RA-05
mitre_attack:
- T1046
- T1057
- T1082
- T1083
- T1547
---

# Hunting for Unusual Service Installations

## Overview

Attackers frequently install malicious Windows services for persistence and privilege escalation (MITRE ATT&CK T1543.003 — Create or Modify System Process: Windows Service). Event ID 7045 in the System event log records every new service installation. This skill parses .evtx log files to extract service installation events, flags suspicious binary paths (temp directories, PowerShell, cmd.exe, encoded commands), and correlates with known attack patterns.


## When to Use

- When investigating security incidents that require hunting for unusual service installations
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Python 3.9+ with `python-evtx`, `lxml`
- Windows System event log (.evtx) files
- Access to live System event log (optional, for real-time monitoring)
- Sysmon logs for enhanced process tracking (optional)

## Steps

1. Parse System.evtx for Event ID 7045 (new service installed)
2. Extract service name, binary path, service type, and account
3. Flag services with suspicious binary paths (temp dirs, encoded commands)
4. Detect PowerShell-based service creation patterns
5. Identify services running as LocalSystem with unusual paths
6. Cross-reference with known legitimate service baselines
7. Generate threat hunting report with MITRE ATT&CK T1543.003 mapping

## Expected Output

- JSON report listing all new service installations with risk scores, suspicious indicators, and remediation recommendations
- Timeline of service installation events with binary path analysis

