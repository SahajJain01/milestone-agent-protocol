# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-001 — Publish the reusable protocol

**End goal:** Any web-capable LLM can initialize or safely upgrade the milestone-first context
structure in an arbitrary repository from one public GitHub URL.

**Close when:** The public repository is fetchable, canonical files and the optional skill validate,
fresh initialization preserves a disposable fixture, same-version rerun is a no-op, an ordered
upgrade succeeds, and independent review approves the result.

### T-001 — Build, verify, and publish version 1.0.0

**State:** Active

**Source / code:** User request dated 2026-07-29; `PROTOCOL.md`; `protocol.yaml`; `templates/`;
`migrations/`; `skills/initialize-agent-protocol/`.

**Dependencies:** Cotopaxi ADR 0009 establishes the no-live-journal contract.

**Acceptance:**

- Canonical protocol and metadata define fresh, legacy, reconcile, upgrade, fork, downgrade, and
  conflict behavior.
- The Codex skill validates but remains optional.
- Disposable fixture initialization, rerun, and upgrade checks pass without altering user files.
- The repository is public, committed, pushed, and independently reviewed.
