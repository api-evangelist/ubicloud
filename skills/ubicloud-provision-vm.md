---
name: ubicloud-provision-vm
description: Register an SSH key and provision, inspect and control a Ubicloud virtual
  machine.
api: openapi/ubicloud-openapi.yml
operations:
- registerSshPublicKey
- createVM
- getVMDetails
- listProjectVMs
- restartVM
- stopVm
- startVM
- deleteVM
generated: '2026-10-09'
method: generated
---

# Register an SSH key and provision, inspect and control a Ubicloud virtual machine.

## Steps
1. Optionally register an SSH key with `registerSshPublicKey`.
2. Call `createVM` (POST /project/{project_id}/location/{location}/vm/{vm_reference}); `public_key` is required, optional `size`, `boot_image`, `storage_size`, `enable_ip4`, `private_subnet_id`, `unix_user`, `init_script`, `gpu`.
3. Poll `getVMDetails` until the VM is running; list with `listProjectVMs`.
4. Control lifecycle with `restartVM`, `stopVm`, `startVM`; remove with `deleteVM` (destructive: confirm first).

## Rules
- Auth: `Authorization: Bearer <personal access token>` created on the project Tokens page; base URL `https://api.ubicloud.com`.
- Idempotency: resources are addressed by a name unique per project+location, which the API uses as the idempotency token, so retrying a create with the same reference is safe.
- Errors: 403 = unauthorized user access, 419 = invalid token (from https://www.ubicloud.com/docs/api-reference/overview).
