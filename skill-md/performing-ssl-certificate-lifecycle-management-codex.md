---
name: performing-ssl-certificate-lifecycle-management
display_name: performing-ssl-certificate-lifecycle-management
platform: Codex
category: Security, forensics, and incident response
---

# performing-ssl-certificate-lifecycle-management - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-ssl-certificate-lifecycle-management` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

SSL/TLS certificate lifecycle management encompasses the full process of requesting, issuing, deploying, monitoring, renewing, and revoking X.509 certificates. Poor certificate management is a leading cause of outages an

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-ssl-certificate-lifecycle-management, then write the task. Fallback prompt: Use the performing-ssl-certificate-lifecycle-management skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-ssl-certificate-lifecycle-management` |
| Canonical name | `performing-ssl-certificate-lifecycle-management` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

SSL/TLS certificate lifecycle management encompasses the full process of requesting, issuing, deploying, monitoring, renewing, and revoking X.509 certificates. Poor certificate management is a leading cause of outages an

## Original SKILL.md

---
name: performing-ssl-certificate-lifecycle-management
description: SSL/TLS certificate lifecycle management encompasses the full process
  of requesting, issuing, deploying, monitoring, renewing, and revoking X.509 certificates.
  Poor certificate management is a leading
domain: cybersecurity
subdomain: cryptography
tags:
- cryptography
- ssl
- certificates
- pki
- tls
- key-management
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.DS-01
- PR.DS-02
- PR.DS-10
mitre_attack:
- T1600
- T1573
- T1553
- T1040
---
# Performing SSL Certificate Lifecycle Management

## Overview

SSL/TLS certificate lifecycle management encompasses the full process of requesting, issuing, deploying, monitoring, renewing, and revoking X.509 certificates. Poor certificate management is a leading cause of outages and security incidents. This skill covers automating the entire certificate lifecycle using Python and ACME protocol tools.


## When to Use

- When conducting security assessments that involve performing ssl certificate lifecycle management
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- Familiarity with cryptography concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Objectives

- Generate Certificate Signing Requests (CSRs) programmatically
- Parse and validate X.509 certificates
- Monitor certificate expiration across infrastructure
- Automate renewal using ACME protocol (Let's Encrypt)
- Implement certificate revocation checking (CRL and OCSP)
- Track certificate inventory across multiple domains

## Key Concepts

### Certificate Lifecycle Stages

1. **Request**: Generate key pair and CSR
2. **Issuance**: CA validates and issues certificate
3. **Deployment**: Install certificate on servers
4. **Monitoring**: Track expiration and health
5. **Renewal**: Request new certificate before expiry
6. **Revocation**: Invalidate compromised certificates

### Certificate Types

| Type | Validation | Use Case |
|------|-----------|----------|
| DV (Domain Validation) | Domain ownership | Websites, APIs |
| OV (Organization Validation) | Domain + org identity | Business sites |
| EV (Extended Validation) | Full legal verification | E-commerce, banking |
| Wildcard | *.domain.com | Multi-subdomain |
| SAN/UCC | Multiple domains | Multi-domain hosting |

## Security Considerations

- Set up automated monitoring for all certificates
- Use ECDSA (P-256) certificates for better performance over RSA
- Enable OCSP stapling on all servers
- Implement Certificate Transparency log monitoring
- Maintain inventory of all certificates and their locations
- Plan for CA compromise scenarios (key pinning, backup CAs)

## Validation Criteria

- [ ] CSR generation produces valid PKCS#10 request
- [ ] Certificate parsing extracts all relevant fields
- [ ] Expiration monitoring detects certificates within threshold
- [ ] Certificate chain validation verifies trust path
- [ ] OCSP checking detects revoked certificates
- [ ] Certificate inventory tracks all deployed certificates

