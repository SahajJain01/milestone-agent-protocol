---
id: legacy-unlocked-to-2.3.0
from: legacy-unlocked
to: 2.3.0
---

# Adopt a verified legacy-unlocked target into protocol 2.3.0

## Preconditions

- The source `protocol.yaml`, `PROTOCOL.md`, every template, every migration, and this adoption
  specification pass their declared digest and inventory checks.
- The target is a Git repository with an immutable baseline commit.
- `.agent/protocol.lock.yaml` is absent from the current tree and every reachable ref. A deleted or
  malformed historical lock fails this precondition.
- Every path in `required_target_paths` other than `.agent/protocol.lock.yaml` exists, is tracked, and
  is clean at the baseline commit.
- A reachable evidence commit shows the intentional milestone-first conversion by introducing or
  converting `.agent/todo.md`, `.agent/decisions/index.md`, and the root `AGENTS.md` routing needed to
  use them.
- Existing records make no conflicting claim about protocol source, version, digest, or ownership;
  their IDs, links, and project prose can be preserved without guessing material facts.
- The agent presents the source/ref/resolved commit, baseline commit, evidence commit, managed-path
  status, proposed patch, and local divergences before writing.
- The human explicitly authorizes adoption using that exact canonical source, requested ref,
  resolved source commit, baseline commit, and evidence commit. Generic initialization is
  insufficient.

## Operations

1. Allocate the next unused decision ID after checking the current target and Git history. Add and
   index an accepted adoption decision recording this specification ID, canonical source/ref,
   resolved source commit, baseline commit, evidence commit, authorization date, and the fact that no
   prior semantic version is claimed.
2. Reconcile declared target paths semantically to the 2.3.0 structural contract. Preserve target
   prose, priorities, milestones, tasks, decisions, external evidence, source anchors, local guides,
   and unrelated paths. Add only provably missing rules and fields; surface material ambiguity rather
   than guessing.
3. Record justified local divergences once. Do not claim earlier semantic migrations or copy source
   repository product details into the target.
4. Verify the complete target and its safe repository-specific gate. Confirm a second 2.3.0
   reconciliation would produce zero diff.
5. Write `.agent/protocol.lock.yaml` last with the validated source/version/digest, current managed
   paths and rules, `last_applied: 2.3.0`, `applied_migrations: []`, and
   `applied_adoptions: [legacy-unlocked-to-2.3.0]`.
6. Add a `legacy_adoption` block containing `specification`, `adopted_at`, `baseline_commit`,
   `evidence_commit`, and `authorization_decision`.

## Verification

- The pre-adoption baseline and evidence commits are reachable and match the authorization decision.
- No protocol lock exists anywhere in pre-adoption reachable history.
- Every managed diff from the baseline is part of the reviewed deterministic adoption patch; paths
  outside declared protocol scope are unchanged.
- Required paths, current rule identities, milestone/task/decision schemas, immutable IDs, internal
  links, external-evidence anchors, and source anchors validate.
- The target decision and lock record the same source/ref/resolved commit, specification, baseline,
  evidence commit, and adoption date without asserting a prior protocol version.
- The target's safe verification command and `git diff --check` pass.
- A repeated 2.3.0 initialization uses the lock and produces zero diff.

## Interrupted adoption

The indexed adoption decision is the only durable pre-lock recovery anchor. If the operation stops
after that decision is written, resume only when its source/specification/baseline/evidence tuple
matches the validated source and every managed diff is an exact subset of this specification's
reviewed patch. Otherwise stop without creating a lock.

## Abort behavior

Stop without creating a lock when any precondition, ownership check, authorization tuple, structural
reconciliation, or verification fails. Revert only operation-owned changes that can be identified
safely; never stash, reset, force-checkout, delete target records, or reinterpret a historical lock
as legacy-unlocked state.
