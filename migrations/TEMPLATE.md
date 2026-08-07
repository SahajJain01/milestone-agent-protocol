---
id: X.Y.Z-to-A.B.C
from: X.Y.Z
to: A.B.C
---

# Migrate protocol X.Y.Z to A.B.C

## Preconditions

- List deterministic version, digest, structure, ownership, and repository-state checks.
- When adding a managed path, require its prior absence or report project-owned content as a conflict.

## Operations

1. Describe semantic changes using stable rule identities.
2. Preserve project-owned content, immutable record IDs, and append-only lifecycle history.
3. Update `.agent/protocol.lock.yaml` only after every operation verifies.

## Verification

- List structural, idempotence, link, safety, and target-specific checks.

## Abort behavior

Stop with no lock update. Revert only changes that the current operation can identify safely; never
use destructive Git operations.
