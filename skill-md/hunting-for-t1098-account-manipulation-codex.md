---
name: hunting-for-t1098-account-manipulation
display_name: hunting-for-t1098-account-manipulation
platform: Codex
category: Security, forensics, and incident response
---

# hunting-for-t1098-account-manipulation - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `hunting-for-t1098-account-manipulation` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

MITRE ATT&CK T1098 (Account Manipulation) covers adversary actions to maintain or expand access to compromised accounts, including adding credentials, modifying group memberships, SID history injection, and creating shad

## How To Use It In Codex

In Codex, click the chat box, press /, choose hunting-for-t1098-account-manipulation, then write the task. Fallback prompt: Use the hunting-for-t1098-account-manipulation skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `hunting-for-t1098-account-manipulation` |
| Canonical name | `hunting-for-t1098-account-manipulation` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

MITRE ATT&CK T1098 (Account Manipulation) covers adversary actions to maintain or expand access to compromised accounts, including adding credentials, modifying group memberships, SID history injection, and creating shad

## Original SKILL.md

---
name: hunting-for-t1098-account-manipulation
description: Hunt for MITRE ATT&CK T1098 account manipulation including shadow admin
  creation, SID history injection, group membership changes, and credential modifications
  using Windows Security Event Logs.
domain: cybersecurity
subdomain: threat-hunting
tags:
- threat-hunting
- mitre-attack
- t1098
- account-manipulation
- active-directory
- persistence
version: '1.0'
author: mahipal
license: Apache-2.0
d3fend_techniques:
- Token Binding
- Restore Access
- Application Protocol Command Analysis
- Password Authentication
- Biometric Authentication
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
- T1003
---
# Hunting for T1098 Account Manipulation

## Overview

MITRE ATT&CK T1098 (Account Manipulation) covers adversary actions to maintain or expand access to compromised accounts, including adding credentials, modifying group memberships, SID history injection, and creating shadow admin accounts. This skill covers detecting these techniques through Windows Security Event Log analysis (Event IDs 4738, 4728, 4732, 4756, 4670, 5136), correlating group membership changes with privilege escalation indicators, and identifying anomalous account modification patterns.


## When to Use

- When investigating security incidents that require hunting for t1098 account manipulation
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Windows Security Event Logs (EVTX format) or SIEM access
- Python 3.9+ with `python-evtx`, `lxml` libraries
- Understanding of Active Directory group structure and SID architecture
- Familiarity with MITRE ATT&CK T1098 sub-techniques

## Steps

### Step 1: Parse Account Modification Events
Extract Event IDs 4738 (user account changed), 4728/4732/4756 (member added to security groups), and 5136 (directory service object modified).

### Step 2: Detect Privileged Group Changes
Flag additions to Domain Admins, Enterprise Admins, Schema Admins, Administrators, and Backup Operators groups.

### Step 3: Identify Shadow Admin Indicators
Detect accounts receiving AdminSDHolder protection, direct privilege assignment, or SID history injection.

### Step 4: Correlate with Attack Timeline
Cross-reference account changes with authentication events to identify initial compromise and persistence establishment.

## Expected Output

JSON report with detected account manipulation events, privileged group changes, shadow admin indicators, and timeline correlation.

