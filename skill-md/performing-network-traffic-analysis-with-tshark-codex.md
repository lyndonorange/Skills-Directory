---
name: performing-network-traffic-analysis-with-tshark
display_name: performing-network-traffic-analysis-with-tshark
platform: Codex
category: Security, forensics, and incident response
---

# performing-network-traffic-analysis-with-tshark - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-network-traffic-analysis-with-tshark` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

This skill automates packet capture analysis using tshark (Wireshark CLI) and pyshark (Python wrapper). It extracts protocol distribution statistics, identifies suspicious network flows (port scans, beaconing, data exfil

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-network-traffic-analysis-with-tshark, then write the task. Fallback prompt: Use the performing-network-traffic-analysis-with-tshark skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-network-traffic-analysis-with-tshark` |
| Canonical name | `performing-network-traffic-analysis-with-tshark` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

This skill automates packet capture analysis using tshark (Wireshark CLI) and pyshark (Python wrapper). It extracts protocol distribution statistics, identifies suspicious network flows (port scans, beaconing, data exfil

## Original SKILL.md

---
name: performing-network-traffic-analysis-with-tshark
description: Automate network traffic analysis using tshark and pyshark for protocol
  statistics, suspicious flow detection, DNS anomaly identification, and IOC extraction
  from PCAP files
domain: cybersecurity
subdomain: network-security
tags:
- tshark
- pyshark
- pcap
- packet-analysis
- network-forensics
- wireshark
- traffic-analysis
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.IR-01
- DE.CM-01
- ID.AM-03
- PR.DS-02
mitre_attack:
- T1046
- T1040
- T1557
- T1071
- T1005
---

# Performing Network Traffic Analysis with TShark

## Overview

This skill automates packet capture analysis using tshark (Wireshark CLI) and pyshark (Python wrapper). It extracts protocol distribution statistics, identifies suspicious network flows (port scans, beaconing, data exfiltration), extracts IOCs (IPs, domains, URLs), and detects DNS tunneling patterns from PCAP files.


## When to Use

- When conducting security assessments that involve performing network traffic analysis with tshark
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- tshark (Wireshark CLI) installed and in PATH
- Python 3.8+ with pyshark library
- PCAP or PCAPNG capture file for analysis

## Steps

1. **Extract Protocol Statistics** — Generate protocol hierarchy and conversation statistics from the capture
2. **Identify Top Talkers** — Rank source/destination IPs by volume and connection count
3. **Detect Suspicious Flows** — Flag port scanning patterns, unusual port usage, and high-frequency connections
4. **Extract Network IOCs** — Pull unique IPs, domains from DNS queries, and URLs from HTTP traffic
5. **Analyze DNS Traffic** — Detect DNS tunneling via high-entropy subdomain queries and excessive TXT records
6. **Generate Analysis Report** — Produce structured report with flow summaries and threat indicators

## Expected Output

- JSON report with protocol statistics and top talkers
- Suspicious flow detections with severity ratings
- Extracted IOCs (IPs, domains, URLs)
- DNS anomaly analysis results

