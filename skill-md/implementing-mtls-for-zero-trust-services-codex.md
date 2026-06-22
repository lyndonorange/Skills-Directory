---
name: implementing-mtls-for-zero-trust-services
display_name: implementing-mtls-for-zero-trust-services
platform: Codex
category: General and specialized workflows
---

# implementing-mtls-for-zero-trust-services - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `implementing-mtls-for-zero-trust-services` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When deploying or configuring implementing mtls for zero trust services capabilities in your environment

## How To Use It In Codex

In Codex, click the chat box, press /, choose implementing-mtls-for-zero-trust-services, then write the task. Fallback prompt: Use the implementing-mtls-for-zero-trust-services skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `implementing-mtls-for-zero-trust-services` |
| Canonical name | `implementing-mtls-for-zero-trust-services` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

- When deploying or configuring implementing mtls for zero trust services capabilities in your environment

## Original SKILL.md

---
name: implementing-mtls-for-zero-trust-services
description: 'Configures mutual TLS (mTLS) authentication between microservices using
  Python cryptography library for certificate generation and ssl module for TLS verification.
  Validates certificate chains, checks expiration, and audits mTLS deployment status.
  Use when implementing zero-trust service-to-service authentication.

  '
domain: cybersecurity
subdomain: security-operations
tags:
- mtls
- zero-trust
- mutual-tls
- service-authentication
- certificate-management
- microservices-security
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1078
- T1190
- T1059
- T1553
- T1573
---

# Implementing mTLS for Zero Trust Services


## When to Use

- When deploying or configuring implementing mtls for zero trust services capabilities in your environment
- When establishing security controls aligned to compliance requirements
- When building or improving security architecture for this domain
- When conducting security assessments that require this implementation

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Generate CA certificates, issue service certificates, and configure mutual TLS
verification for service-to-service authentication.

```python
from cryptography import x509
from cryptography.x509.oid import NameOID
from cryptography.hazmat.primitives import hashes, serialization
from cryptography.hazmat.primitives.asymmetric import rsa
import datetime

# Generate CA key and certificate
ca_key = rsa.generate_private_key(public_exponent=65537, key_size=4096)
ca_cert = (x509.CertificateBuilder()
    .subject_name(x509.Name([x509.NameAttribute(NameOID.COMMON_NAME, "Internal CA")]))
    .issuer_name(x509.Name([x509.NameAttribute(NameOID.COMMON_NAME, "Internal CA")]))
    .public_key(ca_key.public_key())
    .serial_number(x509.random_serial_number())
    .not_valid_before(datetime.datetime.utcnow())
    .not_valid_after(datetime.datetime.utcnow() + datetime.timedelta(days=3650))
    .add_extension(x509.BasicConstraints(ca=True, path_length=None), critical=True)
    .sign(ca_key, hashes.SHA256()))
```

## Examples

```python
import ssl
context = ssl.SSLContext(ssl.PROTOCOL_TLS_CLIENT)
context.load_cert_chain("client.pem", "client-key.pem")
context.load_verify_locations("ca.pem")
context.verify_mode = ssl.CERT_REQUIRED
```

