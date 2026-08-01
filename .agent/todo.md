# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-003 — Support reopening closed milestones

**End goal:** Repositories can resume work against a previously delivered milestone without losing
the milestone's identity or rewriting completed-task history.

**Close when:** The normative protocol, templates, migration, references, metadata, and adapter agree
on an auditable reopen-and-reclose lifecycle, all repository verification passes, and the focused
2.1.0 change is published.

### T-003 — Define milestone reopening semantics

**State:** Active

**Source / code:** User direction dated 2026-07-30; `PROTOCOL.md`; `protocol.yaml`; `templates/`;
`migrations/`; `references/`; `skills/initialize-agent-protocol/`.

**Dependencies:** None.

**Acceptance:**

- A closed milestone can return to the active todo under its original immutable milestone ID.
- Reopening records dated evidence, preserves the original outcome contract, and uses new task IDs.
- New outcomes remain new milestones rather than being disguised as reopened work.
- Version, migration, templates, metadata digests, references, and the optional skill agree.
