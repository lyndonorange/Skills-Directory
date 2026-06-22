---
name: detecting-mimikatz-execution-patterns
display_name: detecting-mimikatz-execution-patterns
platform: Codex
category: Security, forensics, and incident response
---

# detecting-mimikatz-execution-patterns - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-mimikatz-execution-patterns` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When proactively hunting for indicators of detecting mimikatz execution patterns in the environment

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-mimikatz-execution-patterns, then write the task. Fallback prompt: Use the detecting-mimikatz-execution-patterns skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-mimikatz-execution-patterns` |
| Canonical name | `detecting-mimikatz-execution-patterns` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When proactively hunting for indicators of detecting mimikatz execution patterns in the environment

## Original SKILL.md

---
name: detecting-mimikatz-execution-patterns
description: Detect Mimikatz execution through command-line patterns, LSASS access
  signatures, binary indicators, and in-memory detection of known modules.
domain: cybersecurity
subdomain: threat-hunting
tags:
- threat-hunting
- mitre-attack
- mimikatz
- credential-dumping
- edr
- t1003
- proactive-detection
version: '1.0'
author: mahipal
license: Apache-2.0
d3fend_techniques:
- Execution Isolation
- Process Termination
- Hardware-based Process Isolation
- Web Session Access Mediation
- Process Suspension
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

# Detecting Mimikatz Execution Patterns

## When to Use

- When proactively hunting for indicators of detecting mimikatz execution patterns in the environment
- After threat intelligence indicates active campaigns using these techniques
- During incident response to scope compromise related to these techniques
- When EDR or SIEM alerts trigger on related indicators
- During periodic security assessments and purple team exercises

## Prerequisites

- EDR platform with process and network telemetry (CrowdStrike, MDE, SentinelOne)
- SIEM with relevant log data ingested (Splunk, Elastic, Sentinel)
- Sysmon deployed with comprehensive configuration
- Windows Security Event Log forwarding enabled
- Threat intelligence feeds for IOC correlation

## Workflow

1. **Formulate Hypothesis**: Define a testable hypothesis based on threat intelligence or ATT&CK gap analysis.
2. **Identify Data Sources**: Determine which logs and telemetry are needed to validate or refute the hypothesis.
3. **Execute Queries**: Run detection queries against SIEM and EDR platforms to collect relevant events.
4. **Analyze Results**: Examine query results for anomalies, correlating across multiple data sources.
5. **Validate Findings**: Distinguish true positives from false positives through contextual analysis.
6. **Correlate Activity**: Link findings to broader attack chains and threat actor TTPs.
7. **Document and Report**: Record findings, update detection rules, and recommend response actions.

## Key Concepts

| Concept | Description |
|---------|-------------|
| T1003.001 | LSASS Memory |
| T1003.006 | DCSync |
| T1558.003 | Kerberoasting |
| T1558.001 | Golden Ticket |

## Tools & Systems

| Tool | Purpose |
|------|---------|
| CrowdStrike Falcon | EDR telemetry and threat detection |
| Microsoft Defender for Endpoint | Advanced hunting with KQL |
| Splunk Enterprise | SIEM log analysis with SPL queries |
| Elastic Security | Detection rules and investigation timeline |
| Sysmon | Detailed Windows event monitoring |
| Velociraptor | Endpoint artifact collection and hunting |
| Sigma Rules | Cross-platform detection rule format |

## Common Scenarios

1. **Scenario 1**: Standard sekurlsa::logonpasswords credential dump
2. **Scenario 2**: PowerShell Invoke-Mimikatz reflective loading
3. **Scenario 3**: DCSync from non-DC host
4. **Scenario 4**: Golden ticket creation for persistence

## Output Format

```
Hunt ID: TH-DETECT-[DATE]-[SEQ]
Technique: T1003.001
Host: [Hostname]
User: [Account context]
Evidence: [Log entries, process trees, network data]
Risk Level: [Critical/High/Medium/Low]
Confidence: [High/Medium/Low]
Recommended Action: [Containment, investigation, monitoring]
```

