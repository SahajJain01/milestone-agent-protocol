---
id: legacy-state-to-X.Y.Z
from: legacy-state
to: X.Y.Z
---

# Adopt verified legacy state into protocol X.Y.Z

## Preconditions

- List deterministic source, Git-history, baseline, ownership, authorization, and target checks.
- Require explicit human confirmation after presenting the complete candidate audit.
- Reject any state that could bypass an existing, deleted, malformed, or conflicting lock.

## Operations

1. Record the authorization and provenance in the next indexed target decision.
2. Reconcile only declared structural rules while preserving project-owned content and IDs.
3. Verify the complete change set and write the protocol lock last with distinct adoption metadata.

## Verification

- List structural, provenance, idempotence, link, interruption, and target-specific checks.

## Abort behavior

Stop without creating a lock. Revert only operation-owned changes that can be identified safely;
never use destructive Git operations.
