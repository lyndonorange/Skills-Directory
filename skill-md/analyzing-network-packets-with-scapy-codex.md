---
name: analyzing-network-packets-with-scapy
display_name: analyzing-network-packets-with-scapy
platform: Codex
category: Security, forensics, and incident response
---

# analyzing-network-packets-with-scapy - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `analyzing-network-packets-with-scapy` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Scapy is a Python packet manipulation library that enables crafting, sending, sniffing, and dissecting network packets at granular protocol layers. This skill covers using Scapy for security-relevant tasks including TCP/

## How To Use It In Codex

In Codex, click the chat box, press /, choose analyzing-network-packets-with-scapy, then write the task. Fallback prompt: Use the analyzing-network-packets-with-scapy skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `analyzing-network-packets-with-scapy` |
| Canonical name | `analyzing-network-packets-with-scapy` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Scapy is a Python packet manipulation library that enables crafting, sending, sniffing, and dissecting network packets at granular protocol layers. This skill covers using Scapy for security-relevant tasks including TCP/

## Original SKILL.md

---
name: analyzing-network-packets-with-scapy
description: Craft, send, sniff, and dissect network packets using Scapy for protocol
  analysis, network reconnaissance, and traffic anomaly detection in authorized security
  testing
domain: cybersecurity
subdomain: network-security
tags:
- scapy
- packet-analysis
- network-forensics
- protocol-dissection
- pcap
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
- T1040
- T1071
- T1046
- T1557
---

# Analyzing Network Packets with Scapy

## Overview

Scapy is a Python packet manipulation library that enables crafting, sending, sniffing, and dissecting network packets at granular protocol layers. This skill covers using Scapy for security-relevant tasks including TCP/UDP/ICMP packet crafting, pcap file analysis, protocol field extraction, SYN scan implementation, DNS query analysis, and detecting anomalous traffic patterns such as unusually fragmented packets or malformed headers.


## When to Use

- When investigating security incidents that require analyzing network packets with scapy
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Python 3.8+ with `scapy` library installed (`pip install scapy`)
- Root/administrator privileges for raw socket operations (sniffing, sending)
- Npcap (Windows) or libpcap (Linux) for packet capture
- Authorization to perform packet operations on target network

## Steps

1. Read and parse pcap/pcapng files with `rdpcap()` for offline analysis
2. Extract protocol layers (IP, TCP, UDP, DNS, HTTP) and field values
3. Compute traffic statistics: top talkers, protocol distribution, port frequency
4. Detect SYN flood patterns by analyzing TCP flag ratios
5. Identify DNS exfiltration indicators via query length and entropy analysis
6. Craft custom probe packets for authorized network testing
7. Export findings as structured JSON report

## Expected Output

JSON report containing packet statistics, protocol distribution, top source/destination IPs, detected anomalies (SYN floods, DNS tunneling indicators, fragmentation attacks), and per-flow summaries.

