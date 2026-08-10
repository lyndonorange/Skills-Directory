---
name: gke-multitenancy
display_name: gke-multitenancy
platform: OpenCode
category: General and specialized workflows
---

# gke-multitenancy - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `gke-multitenancy` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Plans and configures multi-tenancy on GKE. Covers namespace isolation, RBAC planning for teams, resource quotas, LimitRanges, network isolation, and cost allocation. Use when designing GKE multi-tenancy, configuring GKE

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the gke-multitenancy skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gke-multitenancy` |
| Canonical name | `gke-multitenancy` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Plans and configures multi-tenancy on GKE. Covers namespace isolation, RBAC planning for teams, resource quotas, LimitRanges, network isolation, and cost allocation. Use when designing GKE multi-tenancy, configuring GKE

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: gke-multitenancy
description: "Plans and configures multi-tenancy on GKE. Covers namespace isolation, RBAC planning for teams, resource quotas, LimitRanges, network isolation, and cost allocation. Use when designing GKE multi-tenancy, configuring GKE namespaces, setting up resource quotas, or isolating GKE teams. Don't use for single-tenant cluster configuration or general deployment instructions (use gke-basics or gke-app-onboarding instead)."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# GKE Multi-Tenancy

This reference covers enterprise multi-tenancy patterns on GKE, including
namespace isolation, RBAC planning, resource quotas, and network segmentation.

> **MCP Tools:** `apply_k8s_manifest`, `get_k8s_resource`, `check_k8s_auth`,
> `describe_k8s_resource`, `delete_k8s_resource`

## When to Use

-   Multiple teams sharing a single GKE cluster
-   Isolating workloads by environment (dev/staging/prod) within one cluster
-   Implementing least-privilege access control
-   Cost allocation across teams or projects

## Multi-Tenancy Models

| Model                         | Isolation    | Complexity | Cost           |
| ----------------------------- | ------------ | ---------- | -------------- |
| **Namespace-per-team**        | Soft (RBAC + | Low        | Lowest (shared |
:                               : Network      :            : cluster)       :
:                               : Policy)      :            :                :
| **Namespace-per-environment** | Soft         | Low        | Low            |
| **Node pool-per-team**        | Medium       | Medium     | Medium         |
:                               : (dedicated   :            :                :
:                               : compute)     :            :                :
| **Cluster-per-team**          | Hard (full   | High       | Highest        |
:                               : isolation)   :            :                :

> **Golden path recommendation**: Start with namespace-per-team for cost
> efficiency. Escalate to stronger isolation only when compliance requires it.

## Namespace Isolation Setup

### 1. Create Namespaces

```bash
kubectl create namespace team-a
kubectl create namespace team-b
kubectl label namespace team-a team=a
kubectl label namespace team-b team=b
```

### 2. RBAC Configuration

**Principle**: Grant minimal permissions per namespace. Never bind to
`system:authenticated`.

```yaml
# Namespace-scoped role for a team
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: team-a-developer
  namespace: team-a
rules:
- apiGroups: ["", "apps", "batch"]
  resources: ["pods", "deployments", "services", "configmaps", "jobs"]
  verbs: ["get", "list", "watch", "create", "update", "patch", "delete"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: team-a-developers
  namespace: team-a
subjects:
- kind: Group
  name: "team-a@example.com"  # Google Group
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: team-a-developer
  apiGroup: rbac.authorization.k8s.io
```

**RBAC best practices:** Use Google Groups for subject bindings. Prefer
namespace-scoped Roles over ClusterRoles. See the `gke-platform-security` skill
for full RBAC hardening guidance.

### 3. Resource Quotas

Prevent any single team from consuming all cluster resources:

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: team-a-quota
  namespace: team-a
spec:
  hard:
    requests.cpu: "10"
    requests.memory: "20Gi"
    limits.cpu: "20"
    limits.memory: "40Gi"
    pods: "50"
    services: "10"
    persistentvolumeclaims: "10"
```

### 4. LimitRanges

Set default and maximum resource constraints per container:

```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: team-a-limits
  namespace: team-a
spec:
  limits:
  - type: Container
    default:
      cpu: "500m"
      memory: "512Mi"
    defaultRequest:
      cpu: "100m"
      memory: "128Mi"
    max:
      cpu: "4"
      memory: "8Gi"
```

> [!IMPORTANT] **Mandatory Defaults**: When defining `min` or `max` limits in a
> `LimitRange`, you **must** also define corresponding `default` and
> `defaultRequest` values. If you set a `min` or `max` without defaults, any pod
> deployed without explicit resource requests/limits will be rejected by the
> admission controller.

### 5. Network Isolation

Apply default-deny per namespace (see the `gke-workload-security` skill), then
allow intra-team traffic:

```yaml
# Allow same-namespace pods to talk + DNS
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-same-namespace
  namespace: team-a
spec:
  podSelector: {}
  ingress:
  - from:
    - podSelector: {}
  egress:
  - to:
    - podSelector: {}
  - to:  # Allow DNS
    - namespaceSelector: {}
      podSelector:
        matchLabels:
          k8s-app: kube-dns
    ports:
    - protocol: UDP
      port: 53
```

## Cost Allocation

### Labels for Cost Attribution

```bash
# Label namespaces for billing
kubectl label namespace team-a cost-center=engineering
kubectl label namespace team-b cost-center=data-science
```

### GKE Cost Allocation

Enable GKE cost allocation to break down costs by namespace and label:

```bash
gcloud container clusters update <CLUSTER_NAME> --region <REGION> \
  --enable-cost-allocation
```

View in Cloud Billing > GKE Cost Allocation.
