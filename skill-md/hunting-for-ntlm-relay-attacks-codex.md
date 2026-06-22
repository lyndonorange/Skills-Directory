---
name: hunting-for-ntlm-relay-attacks
display_name: hunting-for-ntlm-relay-attacks
platform: Codex
category: Security, forensics, and incident response
---

# hunting-for-ntlm-relay-attacks - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `hunting-for-ntlm-relay-attacks` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

NTLM relay attacks intercept and forward NTLM authentication messages to gain unauthorized access to network resources. Attackers use tools like Responder for LLMNR/NBT-NS poisoning and ntlmrelayx for credential relay. T

## How To Use It In Codex

In Codex, click the chat box, press /, choose hunting-for-ntlm-relay-attacks, then write the task. Fallback prompt: Use the hunting-for-ntlm-relay-attacks skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `hunting-for-ntlm-relay-attacks` |
| Canonical name | `hunting-for-ntlm-relay-attacks` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

NTLM relay attacks intercept and forward NTLM authentication messages to gain unauthorized access to network resources. Attackers use tools like Responder for LLMNR/NBT-NS poisoning and ntlmrelayx for credential relay. T

## Original SKILL.md

---
name: hunting-for-ntlm-relay-attacks
description: Detect NTLM relay attacks by analyzing Windows Event 4624 logon type
  3 with NTLMSSP authentication, identifying IP-to-hostname mismatches, Responder
  traffic signatures, SMB signing status, and suspicious authentication patterns across
  the domain.
domain: cybersecurity
subdomain: threat-hunting
tags:
- NTLM-relay
- Windows-events
- Event-4624
- NTLMSSP
- Responder
- SMB-signing
- credential-access
- T1557.001
- Active-Directory
version: '1.0'
author: mahipal
license: Apache-2.0
d3fend_techniques:
- Application Protocol Command Analysis
- Network Isolation
- Network Traffic Analysis
- Client-server Payload Profiling
- Network Traffic Community Deviation
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

# Hunting for NTLM Relay Attacks

## Overview

NTLM relay attacks intercept and forward NTLM authentication messages to gain unauthorized access to network resources. Attackers use tools like Responder for LLMNR/NBT-NS poisoning and ntlmrelayx for credential relay. This skill detects relay activity by querying Windows Security Event 4624 (successful logon) for type 3 network logons with NTLMSSP authentication, identifying mismatches between WorkstationName and source IpAddress, detecting rapid multi-host authentication from single accounts, and auditing SMB signing configuration across domain hosts.


## When to Use

- When investigating security incidents that require hunting for ntlm relay attacks
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Python 3.9+ with Windows Event Log access or exported logs
- Windows Security audit logging enabled (Event ID 4624, 4625, 5145)
- Network access for SMB signing status checks

## Key Detection Areas

1. **IP-hostname mismatch** — WorkstationName in Event 4624 does not resolve to the source IpAddress
2. **NTLMSSP authentication** — logon events using NTLM instead of Kerberos from domain-joined hosts
3. **Machine account relay** — computer accounts (ending in $) authenticating from unexpected IPs
4. **Rapid authentication** — single account authenticating to multiple hosts within seconds
5. **Named pipe access** — Event 5145 showing access to Spoolss, lsarpc, netlogon, samr pipes
6. **SMB signing disabled** — hosts not enforcing SMB signing, enabling relay attacks

## Output

JSON report with suspected relay events, IP-hostname correlation anomalies, SMB signing audit results, and MITRE ATT&CK mapping to T1557.001.

