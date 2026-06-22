---
name: detecting-wmi-persistence
display_name: detecting-wmi-persistence
platform: Codex
category: Security, forensics, and incident response
---

# detecting-wmi-persistence - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-wmi-persistence` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When hunting for WMI event subscription persistence (MITRE ATT&CK T1546.003)

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-wmi-persistence, then write the task. Fallback prompt: Use the detecting-wmi-persistence skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-wmi-persistence` |
| Canonical name | `detecting-wmi-persistence` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When hunting for WMI event subscription persistence (MITRE ATT&CK T1546.003)

## Original SKILL.md

---
name: detecting-wmi-persistence
description: Detect WMI event subscription persistence by analyzing Sysmon Event IDs
  19, 20, and 21 for malicious EventFilter, EventConsumer, and FilterToConsumerBinding
  creation.
domain: cybersecurity
subdomain: threat-hunting
tags:
- threat-hunting
- wmi
- persistence
- sysmon
- t1546.003
- mitre-attack
- windows
- dfir
version: '1.0'
author: mahipal
license: Apache-2.0
d3fend_techniques:
- Application Protocol Command Analysis
- Network Isolation
- Network Traffic Analysis
- Client-server Payload Profiling
- Platform Monitoring
nist_csf:
- DE.CM-01
- DE.AE-02
- DE.AE-07
- ID.RA-05
mitre_attack:
- T1546.003
- T1047
- T1059.001
---

# Detecting WMI Persistence

## When to Use

- When hunting for WMI event subscription persistence (MITRE ATT&CK T1546.003)
- After detecting suspicious WMI activity in endpoint telemetry
- During incident response to identify attacker persistence mechanisms
- When Sysmon alerts trigger on Event IDs 19, 20, or 21
- During purple team exercises testing WMI-based persistence

## Prerequisites

- Sysmon v6.1+ deployed with WMI event logging enabled (Event IDs 19, 20, 21)
- Windows Security Event Log forwarding configured
- SIEM with Sysmon data ingested (Splunk, Elastic, Sentinel)
- PowerShell access for WMI enumeration on endpoints
- Sysinternals Autoruns for manual WMI subscription review

## Workflow

1. **Collect Telemetry**: Parse Sysmon Event IDs 19 (WmiEventFilter), 20 (WmiEventConsumer), 21 (WmiEventConsumerToFilter).
2. **Identify Suspicious Consumers**: Flag CommandLineEventConsumer and ActiveScriptEventConsumer types executing code.
3. **Analyze Event Filters**: Examine WQL queries in EventFilters for process start triggers or timer-based execution.
4. **Correlate Bindings**: Match FilterToConsumerBindings linking suspicious filters to consumers.
5. **Check Persistence Locations**: Query WMI namespaces root\subscription and root\default for active subscriptions.
6. **Validate Findings**: Cross-reference with known-good WMI subscriptions (SCCM, AV products).
7. **Document and Remediate**: Remove malicious subscriptions and update detection rules.

## Key Concepts

| Concept | Description |
|---------|-------------|
| Sysmon Event 19 | WmiEventFilter creation detected |
| Sysmon Event 20 | WmiEventConsumer creation detected |
| Sysmon Event 21 | WmiEventConsumerToFilter binding detected |
| T1546.003 | Event Triggered Execution: WMI Event Subscription |
| CommandLineEventConsumer | Executes system commands when filter triggers |
| ActiveScriptEventConsumer | Runs VBScript/JScript when filter triggers |

## Tools & Systems

| Tool | Purpose |
|------|---------|
| Sysmon | Windows event monitoring for WMI activity |
| WMI Explorer | GUI tool for browsing WMI namespaces |
| Autoruns | Sysinternals tool listing persistence mechanisms |
| PowerShell Get-WMIObject | Enumerate WMI event subscriptions |
| Splunk | SIEM analysis of Sysmon WMI events |
| Velociraptor | Endpoint WMI artifact collection |

## Output Format

```
Hunt ID: TH-WMI-[DATE]-[SEQ]
Technique: T1546.003
Host: [Hostname]
Event Type: [EventFilter|EventConsumer|Binding]
Consumer Type: [CommandLine|ActiveScript]
WQL Query: [Filter query text]
Command: [Executed command or script]
Risk Level: [Critical/High/Medium/Low]
Recommended Action: [Remove subscription, investigate lateral movement]
```

