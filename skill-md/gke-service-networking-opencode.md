---
name: gke-service-networking
display_name: gke-service-networking
platform: OpenCode
category: General and specialized workflows
---

# gke-service-networking - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `gke-service-networking` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Configures GKE edge networking, traffic routing, load balancing, and private service endpoints. Use when configuring Gateway API manifests, standard Ingress, Cloud Armor WAF security policies, Container-Native Load Balan

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the gke-service-networking skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gke-service-networking` |
| Canonical name | `gke-service-networking` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Configures GKE edge networking, traffic routing, load balancing, and private service endpoints. Use when configuring Gateway API manifests, standard Ingress, Cloud Armor WAF security policies, Container-Native Load Balan

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: gke-service-networking
description: "Configures GKE edge networking, traffic routing, load balancing, and private service endpoints. Use when configuring Gateway API manifests, standard Ingress, Cloud Armor WAF security policies, Container-Native Load Balancing (NEGs), Private Service Connect (PSC), or Google-managed SSL certificates on GKE. Don't use for core cluster IP planning, Dataplane V2 network policies, or node NAT egress (use gke-networking instead)."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# GKE Service Networking Skill

This skill provides workflows for exposing applications running on GKE securely
to the internet or internal networks.

## Workflows

### 1. Configure Gateway API (Recommended)

The Gateway API is the modern way to manage routing in Kubernetes.

**Prerequisites**: Gateway API must be enabled on the cluster (enabled by
default in GKE 1.24+).

**Example Gateway Manifest:**

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: {gateway_name}
  namespace: {namespace}
spec:
  gatewayClassName: gke-l7-global-external-managed # GKE managed external L7 load balancer
  listeners:
    - name: http
      protocol: HTTP
      port: 80
```

**Example HTTPRoute Manifest:**

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: HTTPRoute
metadata:
  name: {route_name}
  namespace: {namespace}
spec:
  parentRefs:
    - name: {gateway_name}
  rules:
    - matches:
        - path:
            type: PathPrefix
            value: /
      backendRefs:
        - name: {service_name}
          port: 80
```

### 2. Configure Standard GKE Ingress

Use standard Ingress for simpler use cases or legacy setups.

**Example Ingress Manifest:**

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: {ingress_name}
  namespace: {namespace}
  annotations:
    kubernetes.io/ingress.class: "gce"
spec:
  rules:
    - http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: {service_name}
                port:
                  number: 80
```

### 3. Secure with Cloud Armor

Cloud Armor provides WAF and DDoS protection.

**Enable Cloud Armor via BackendConfig:**

1.  Create a Security Policy in Cloud Armor (usually via gcloud or Terraform).
2.  Reference it in a `BackendConfig` in GKE.

**Example BackendConfig:**

```yaml
apiVersion: cloud.google.com/v1
kind: BackendConfig
metadata:
  name: {backend_config_name}
  namespace: {namespace}
spec:
  securityPolicy:
    name: {security_policy_name}
```

1.  Associate `BackendConfig` with your `Service` via annotations:

    ```yaml
    # In your Kubernetes Service manifest metadata.annotations:
    cloud.google.com/backend-config: '{"default": "{backend_config_name}"}'
    # Or for specific port mappings:
    cloud.google.com/backend-config: '{"ports": {"80": "{backend_config_name}"}}'
    ```

### 4. Configure Google-Managed SSL Certificates

Automatically provision and renew SSL certificates.

**Example ManagedCertificate (Legacy Ingress):**

```yaml
apiVersion: networking.gke.io/v1
kind: ManagedCertificate
metadata:
  name: {certificate_name}
spec:
  domains:
    - {domain_name}
```

Reference it in Ingress annotations: `networking.gke.io/managed-certificates:
{certificate_name}`.

**Gateway API Approach:** For standard Certificate Manager integration, create a
`CertificateMap` and reference it directly in the Gateway metadata annotations
using `networking.gke.io/cert-map: {certificate_map_name}`, or reference a
Kubernetes Secret in the HTTPS listener:

```yaml
apiVersion: gateway.networking.k8s.io/v1
kind: Gateway
metadata:
  name: {gateway_name}
  namespace: {namespace}
  annotations:
    networking.gke.io/cert-map: {certificate_map_name} # For Certificate Manager maps
spec:
  gatewayClassName: gke-l7-global-external-managed
  listeners:
    - name: https
      protocol: HTTPS
      port: 443
      tls:
        mode: Terminate
        certificateRefs:
          - kind: Secret
            name: {secret_name} # Or directly reference a Kubernetes Secret
```

### 5. Enable Container-Native Load Balancing (Recommended)

Container-native load balancing allows load balancers to target Kubernetes Pods
directly, rather than targeting nodes. This improves latency and distribution.

**Prerequisites**: Cluster must be VPC-native.

**How it works**:

-   For GKE Ingress and Gateway API, container-native load balancing is enabled
    by default via Network Endpoint Groups (NEGs).
-   To verify or explicitly enable it for a Service, use the
    `cloud.google.com/neg` annotation.

**Example Service Manifest:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {service_name}
  annotations:
    cloud.google.com/neg: '{"ingress": true}' # Enabled for Ingress
spec:
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  selector:
    app: {app_name}
  type: ClusterIP
```

### 6. Configure Private Service Connect (PSC)

Private Service Connect allows you to expose services in one VPC to consumers in
another VPC securely, without VPC peering.

**Steps:**

1.  Create an internal load balancer for your service.
2.  Create a `ServiceAttachment` referencing the load balancer.

**Example ServiceAttachment Manifest:**

```yaml
apiVersion: networking.gke.io/v1
kind: ServiceAttachment
metadata:
  name: {attachment_name}
  namespace: {namespace}
spec:
  connectionPreference: ACCEPT_AUTOMATIC
  natSubnets:
    - {nat_subnet_name} # Subnet dedicated for PSC NAT
  resourceRef:
    kind: Service
    name: {service_name}
```

Share the `ServiceAttachment` URI with consumers to create a PSC endpoint in
their VPC.

## Best Practices

1.  **Prefer Gateway API**: It offers more flexibility and role separation than
    Ingress.
2.  **Enable Cloud Armor**: Always protect public-facing endpoints with Cloud
    Armor.
3.  **Use Managed Certificates**: Avoid managing certificate renewals manually.
4.  **Use Container-Native Load Balancing**: Always use NEGs for HTTP(S) load
    balancing to reduce latency and improve traffic distribution.
