# Milestones and active work

This is the authoritative record of unfinished work. Completed tasks and closed milestones leave this
file after the milestone lifecycle archive is updated. Git retains completed task bodies and the
audit history.

## M-007 — Persist milestone lifecycle history

**State:** Active

**End goal:** Initialized repositories retain a durable, current-tree lifecycle record for each
closed milestone so closure, reopening, and reclosure preserve the original outcome identity without
turning the active todo into a completed-work archive or depending exclusively on Git archaeology.

**Close when:** The normative protocol, templates, migration, current-version legacy adoption,
references, metadata, and adapter agree on the milestone archive contract; disposable fixtures prove
fresh initialization, upgrade from 2.3.0 and the full older migration chain, forward-only historical
coverage, evidence-backed import, close/reopen/reclose recovery, and same-version idempotence; all
repository validation passes; and visualization remains explicitly deferred.

### T-007 — Add a backward-compatible milestone lifecycle archive

**State:** Active

**Source / code:** 2026-08-07 accepted client-log direction; ADRs 0001–0003 and 0007;
`PROTOCOL.md`; `protocol.yaml`; `templates/`; `migrations/`; `adoptions/`; `references/`;
`skills/initialize-agent-protocol/`.

**Dependencies:** None.

**Acceptance:**

- `.agent/todo.md` remains authoritative only for unfinished work while a declared milestone archive
  preserves each milestone's immutable identity, outcome contract, and append-only lifecycle events.
- Closing, reopening, and reclosing update the todo and archive as one recoverable semantic unit,
  reuse milestone identities, allocate only new task IDs, and never copy completed task bodies into
  the archive.
- Upgrades create an honest forward-only coverage boundary without synthesizing historical closure
  records; an older Git-only milestone can be imported only from unambiguous stable evidence.
- Protocol 2.4.0 includes aligned fresh templates, a contiguous 2.3.0 migration, a current-version
  legacy-adoption specification, lock/rule updates, and verified artifact digests.
- Disposable fixtures prove fresh initialization, the full locked migration chain, same-version
  idempotence, close/reopen/reclose behavior, evidence-backed legacy closure import, ambiguity
  rejection, and preservation of project-owned content.
- No frontend, visualization dependency, hosting configuration, deployment, or publication is added.
