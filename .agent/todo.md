# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-002 — Publish a positive-only initialization contract

**End goal:** The reusable protocol defines only its managed structure and supports reconciliation
only with verified protocol provenance.

**Close when:** The current tree uses a positive managed-path contract, fresh initialization and
locked upgrades remain defined, declared digests validate, and the focused change is pushed.

### T-002 — Establish positive managed scope and lock-required reconciliation

**State:** Active

**Source / code:** User direction dated 2026-07-29; `PROTOCOL.md`; `protocol.yaml`; `templates/`;
`migrations/`; `skills/initialize-agent-protocol/`.

**Acceptance:**

- Fresh targets contain no protocol-managed paths; reconciliation requires a valid lock.
- Only declared paths and rules are created or reconciled.
- Current repository content uses positive managed-scope vocabulary.
- Version, migrations, templates, metadata digests, and the optional skill agree.
