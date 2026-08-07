# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-006 — Adopt verified pre-lock protocol repositories

**State:** Active

**End goal:** Repositories deliberately initialized with milestone-first protocol records before
protocol locks existed can explicitly adopt the current release with project content and immutable
IDs preserved, auditable provenance recorded, and unrelated or previously locked targets still
failing closed.

**Close when:** The normative protocol, adoption specification, templates, locked upgrade migration,
references, metadata, and adapter agree on the legacy-unlocked adoption contract; fresh, locked
upgrade, eligible adoption, ambiguity-rejection, interrupted-adoption, and same-version idempotence
fixtures pass; the Cotopaxi pre-lock shape passes the candidate audit; and the focused release is
published.

### T-006 — Define and publish explicit legacy-unlocked adoption

**State:** Active

**Source / code:** User direction dated 2026-08-07; ADRs 0001–0002 and 0006; `PROTOCOL.md`;
`protocol.yaml`; `adoptions/`; `templates/`; `migrations/`; `references/`;
`skills/initialize-agent-protocol/`.

**Dependencies:** None.

**Acceptance:**

- Adoption never guesses a prior semantic version and requires explicit human authorization after a
  target-specific audit proves no lock exists anywhere in reachable history, managed paths are clean
  at a recorded baseline commit, and a stable commit evidences the intended pre-lock structure.
- Eligible targets are reconciled semantically to the current structural rules without replacing
  project prose or immutable IDs, record a target adoption decision, and write the protocol lock last
  with distinct adoption provenance.
- Deleted or malformed historical locks, dirty managed paths, conflicting source claims, ambiguous
  ownership, failed structure, and failed verification abort without creating or advancing a lock.
- The release includes a declared adoption digest, a contiguous migration for already locked
  repositories, aligned templates/references/adapter guidance, and verified manifest digests.
- Disposable fixtures prove fresh initialization, locked upgrade, eligible legacy adoption,
  ambiguity rejection, interrupted recovery, and post-adoption same-version idempotence; the
  Cotopaxi repository is audited as the motivating real-world candidate without product-file edits.
