---
name: ubicloud-managed-postgres
description: Create and operate a Ubicloud managed PostgreSQL database.
api: openapi/ubicloud-openapi.yml
operations:
- createPostgresDatabase
- getPostgresDatabaseDetails
- listPostgresDatabases
- createLocationPostgresFirewallRule
- createPostgresDatabaseReadReplica
- restartPostgresDatabase
- deletePostgresDatabase
generated: '2026-10-09'
method: generated
---

# Create and operate a Ubicloud managed PostgreSQL database.

## Steps
1. Call `createPostgresDatabase` with required `size` and `storage_size` (optional `version`, `ha_type`, `flavor`, `pg_config`, `tags`).
2. Poll `getPostgresDatabaseDetails` until ready; list with `listPostgresDatabases`.
3. Open access with `createLocationPostgresFirewallRule`; scale reads with `createPostgresDatabaseReadReplica`.
4. Restart with `restartPostgresDatabase`; remove with `deletePostgresDatabase` (destructive: confirm first).

## Rules
- Auth: `Authorization: Bearer <personal access token>` created on the project Tokens page; base URL `https://api.ubicloud.com`.
- Idempotency: resources are addressed by a name unique per project+location, which the API uses as the idempotency token, so retrying a create with the same reference is safe.
- Errors: 403 = unauthorized user access, 419 = invalid token (from https://www.ubicloud.com/docs/api-reference/overview).
