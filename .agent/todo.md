# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-004 — Formalize external feature intake through cross-questioning

**State:** Active

**End goal:** Initialized repositories convert client or other external feature requests into
accepted milestones and tasks only after auditing existing coverage and resolving material product
ambiguity with the human one coherent feature at a time.

**Close when:** The normative protocol, templates, migration, references, metadata, and adapter agree
on an evidence-to-scope cross-questioning lifecycle, fresh and upgrade fixtures prove safe and
idempotent adoption, all repository verification passes, and the focused 2.2.0 change is published.

**Reopened:** 2026-08-06 — Accepted follow-up in `.agent/client-log.md` requires skipped material
client questions to remain visible as milestone-blocking tasks until their answers are reconciled.

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
