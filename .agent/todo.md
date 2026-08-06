# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file; Git retains their history.

## M-004 — Formalize external feature intake through cross-questioning

**End goal:** Initialized repositories convert client or other external feature requests into
accepted milestones and tasks only after auditing existing coverage and resolving material product
ambiguity with the human one coherent feature at a time.

**Close when:** The normative protocol, templates, migration, references, metadata, and adapter agree
on an evidence-to-scope cross-questioning lifecycle, fresh and upgrade fixtures prove safe and
idempotent adoption, all repository verification passes, and the focused 2.2.0 change is published.

### T-004 — Require evidence audit and human cross-questioning before scope promotion

**State:** Active

**Source / code:** User direction dated 2026-08-06; `PROTOCOL.md`; `protocol.yaml`; `templates/`;
`migrations/`; `references/`; `skills/initialize-agent-protocol/`.

**Dependencies:** None.

**Acceptance:**

- External feature lists remain unverified evidence until each coherent feature is reconciled.
- Agents audit source, tests, decisions, and existing milestones before asking focused questions.
- Fully supported, partially supported, and missing behavior lead to evidence, task refinement, or a
  new milestone without duplicate scope.
- Material unknowns are resolved through concise human cross-questioning before promotion to
  accepted tasks or decisions, while implementation and external effects remain separately
  authorized.
- Version, migration, templates, metadata digests, references, and the optional skill agree, with
  fresh, upgrade, and same-version idempotence evidence.
