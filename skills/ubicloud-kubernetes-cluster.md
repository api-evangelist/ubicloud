---
name: ubicloud-kubernetes-cluster
description: Create a Ubicloud managed Kubernetes cluster and fetch its kubeconfig.
api: openapi/ubicloud-openapi.yml
operations:
- createKubernetesCluster
- getKubernetesClusterDetails
- getKubernetesKubeconfigFile
- createKubernetesNodepool
- resizeKubernetesNodepool
- listProjectKubernetesClusters
- deleteKubernetesCluster
generated: '2026-10-09'
method: generated
---

# Create a Ubicloud managed Kubernetes cluster and fetch its kubeconfig.

## Steps
1. Call `createKubernetesCluster` with required `version` and `worker_size` (optional `cp_nodes`, `worker_nodes`).
2. Poll `getKubernetesClusterDetails`; then download credentials with `getKubernetesKubeconfigFile`.
3. Add or scale capacity with `createKubernetesNodepool` / `resizeKubernetesNodepool`.
4. Remove with `deleteKubernetesCluster` (destructive: confirm first).

## Rules
- Auth: `Authorization: Bearer <personal access token>` created on the project Tokens page; base URL `https://api.ubicloud.com`.
- Idempotency: resources are addressed by a name unique per project+location, which the API uses as the idempotency token, so retrying a create with the same reference is safe.
- Errors: 403 = unauthorized user access, 419 = invalid token (from https://www.ubicloud.com/docs/api-reference/overview).
