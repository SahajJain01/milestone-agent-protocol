---
id: legacy-to-1.0.0
from: legacy
to: 1.0.0
---

# Adopt protocol version 1.0.0

## Preconditions

- The source `protocol.yaml` and `PROTOCOL.md` digest validate.
- The target repository and Git status have been inspected.
- Existing agent-context files, IDs, accepted decisions, and dirty paths are known.
- The complete proposed patch can preserve all project-owned content.

## Operations

1. Create or semantically reconcile root `AGENTS.md` with the canonical context order,
   milestone-first protocol, decision protocol, evidence boundary, verification commands, and
   authorization boundaries.
2. Create or migrate `.agent/todo.md` without changing existing milestone/task identity. Convert
   parallel active-work boards into one milestone-first record only when ownership and acceptance can
   be established from evidence.
3. Create or reconcile `.agent/decisions/index.md`; preserve immutable decision files and allocate a
   new adoption decision only when justified.
4. Create or reconcile `.agent/client-log.md` without importing secrets, raw identifiers, or full PII.
5. Remove live instructions to read from or append to `.agent/journal.md`. Preserve an existing
   journal file and its entries unchanged as a frozen historical archive.
6. Validate structure, links, IDs, source anchors, user-file preservation, and safe project checks.
7. Write `.agent/protocol.lock.yaml` last with version `1.0.0` and migration
   `legacy-to-1.0.0`.

## Verification

- Every required target path exists.
- Milestone, task, and decision IDs are unique and retain historical identity.
- No live journal, diary, roadmap, handoff, or done-board instruction remains.
- Existing product files and unrelated dirty changes are unchanged.
- `git diff --check` and safe target verification pass.

## Abort behavior

If any precondition, ownership check, link, ID, or verification fails, do not write the lock. Preserve
the target and report the exact conflict. Never stash, reset, force-checkout, or overwrite the
conflicting content.
