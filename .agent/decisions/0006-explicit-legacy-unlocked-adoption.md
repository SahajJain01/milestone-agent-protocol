# ADR 0006: Allow explicit evidence-backed adoption of pre-lock repositories

- **Status:** Accepted
- **Date:** 2026-08-07
- **Supersedes:** ADR 0002 only where every lockless target containing protocol-managed paths is a
  terminal conflict even when Git history and explicit human direction can prove a pre-lock adoption

## Context

ADR 0002 correctly made a missing or malformed lock fail closed because similar-looking repository
records do not prove protocol ownership. A real repository can nevertheless predate the lock
contract while retaining a clean, reviewable Git history that proves when its milestone-first
records were deliberately introduced. Treating that case as permanently unrecoverable forces either
invented version provenance or an unsafe wholesale reinitialization.

The user requested a supported recovery path on 2026-08-07 after the Cotopaxi repository exposed
this gap. Its target records and Git history are evidence for the use case, not permission to weaken
the default conflict behavior or overwrite project-specific content.

## Decision

- Keep missing-lock targets in conflict by default. Generic initialize or update requests do not
  authorize legacy adoption.
- Declare immutable legacy-adoption specifications separately from semantic-version migrations.
  Adoption records no guessed prior protocol version and converges an eligible target directly onto
  the current structural contract.
- Require a Git repository, no protocol lock anywhere in reachable history, every required pre-lock
  managed record, clean managed paths at an immutable baseline commit, a reachable evidence commit
  showing the intended milestone-first structure, and no conflicting protocol-source claim.
- Present the candidate audit before writing and require explicit human authorization naming the
  canonical source, requested ref, resolved source commit, baseline commit, and evidence commit.
- Preserve project prose, IDs, evidence, and unrelated paths; reconcile only declared structural
  rules; add an indexed target decision documenting adoption; verify the complete patch; and write
  `.agent/protocol.lock.yaml` last.
- Record adoption through its own specification ID, timestamp, baseline/evidence commits, and target
  decision anchor. A completed adoption uses normal locked reconciliation thereafter.
- Reject deleted or malformed historical locks, dirty managed paths, ambiguous ownership, failed
  conformance, or failed verification without creating a lock.

## Reason

Explicit adoption distinguishes a provable pre-lock installation from an arbitrary repository that
merely resembles the protocol. Git evidence and human confirmation establish ownership without
fabricating a historical version, while current-version reconciliation and lock-last verification
restore deterministic future upgrades.

## Consequences

- The first release containing this contract declares a legacy-unlocked adoption specification and
  a normal migration for already locked targets.
- Adopting targets receive auditable provenance but do not claim migrations they never applied.
- Repositories without sufficient history or authorization remain conflicts and require manual
  provenance recovery or continued project-owned operation.
- Adoption must be covered by eligible, ambiguous, interrupted, and idempotent fixtures in addition
  to the ordinary fresh and locked-upgrade cases.
