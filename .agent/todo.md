# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-005 — Preserve skipped client questions through resolution

**State:** Active

**End goal:** Initialized repositories retain explicitly skipped material client questions as blocked
tasks under their accepted owning milestones, hand them back in client-ready form, and absorb returned
answers into milestone facts before unblocking those outcomes.

**Close when:** The normative protocol, templates, migration, references, metadata, and adapter agree
on the skipped-question blocking and answer-reconciliation lifecycle, fresh and upgrade fixtures
prove safe and idempotent adoption, all repository verification passes, and the focused 2.2.0 change
is published.

### T-005 — Persist and resolve skipped client questions

**State:** Active

**Source / code:** 2026-08-06 accepted client-log follow-up; ADR 0005; `PROTOCOL.md`;
`protocol.yaml`; `templates/`; `migrations/`; `references/`.

**Dependencies:** None.

**Acceptance:**

- An explicitly skipped material question becomes a blocked client-question task under its accepted
  owning milestone, and that milestone is marked blocked until all such tasks resolve.
- The end-of-pass handoff lists every unresolved client question in client-ready wording, grouped by
  milestone/task identity, without authorizing an outbound message.
- A returned answer is archived as accepted evidence, absorbed into the corresponding milestone's
  facts and affected scope records, and only then permits the question task to complete and leave the
  active todo.
- The normative protocol, templates, migration, references, metadata digests, and optional adapter
  agree, and fresh, upgrade, resolution, and same-version idempotence fixtures pass.
