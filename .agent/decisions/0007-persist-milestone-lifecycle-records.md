# ADR 0007: Persist milestone lifecycle records outside the active todo

- **Status:** Accepted
- **Date:** 2026-08-07
- **Supersedes:** The Git-only closure storage and reconstruction portions of ADR 0003

## Context

ADR 0003 correctly keeps completed work out of `.agent/todo.md`, but it makes Git history the only
durable source for a closed milestone's identity, outcome contract, and reopen/reclose cycles. That
is logically workable yet operationally brittle for shallow clones, rewritten or unavailable
history, deterministic tooling, and any future read-only projection of milestone state.

The user requested a durable milestone archive, backward-compatible upgrades for existing protocol
installations, and explicit deferral of visualization. The archive must not become a second active
planning system or invent historical facts during migration.

## Decision

- `.agent/todo.md` remains the sole authority for unfinished milestones and tasks.
- Every initialized target contains `.agent/milestones/index.md`. The index declares its historical
  coverage and links one `.agent/milestones/M-###.md` lifecycle record per archived milestone.
- A milestone lifecycle record preserves the immutable milestone ID, name, `End goal`, and
  `Close when`. Its numbered closure, reopening, and correction entries are append-only; corrections
  identify the entry they supersede instead of silently rewriting history.
- Before a milestone leaves the active todo, its verified closure is written to the lifecycle record
  and indexed. Closure entries preserve the date, concise outcome, stable closure evidence, and
  completed task IDs, but not completed task bodies or a duplicate backlog.
- Reopening appends a reopening entry and restores the matching milestone contract to the active
  todo with only new task IDs. Reclosure appends the next closure entry before removing the milestone
  from the todo again.
- Migration to this rule creates an honest forward-only archive boundary and does not synthesize
  records for milestones closed under older versions. An older Git-only milestone may be imported
  on demand only when stable history proves its latest identity, outcome contract, closure, and task
  IDs without ambiguity; otherwise reopening fails closed.
- Git remains the audit trail and fallback evidence for pre-archive history, but it is no longer the
  only record for closures made after archive coverage begins.
- Visualization, generated frontend code, dependencies, hosting, deployment, and publication remain
  outside this revision.

## Reason

Separating the active queue from an append-only lifecycle archive preserves the protocol's
milestone-first focus while making closure and reopening deterministic from the current tree. An
explicit coverage boundary avoids false claims about older history, and evidence-backed on-demand
import provides compatibility without making every migration reconstruct arbitrary Git history.

## Consequences

- Protocol 2.4.0 adds a required milestone index, a lifecycle-record template, the
  `durable-milestone-lifecycle-archive` managed rule, and a contiguous migration from 2.3.0.
- Current-version legacy adoption initializes the same honest coverage boundary without claiming
  closures that cannot be proved.
- Agents must stage archive and todo changes as one semantic operation and recover only exact,
  provable partial operations.
- ADR 0003 continues to govern outcome identity and new task allocation; its Git-only storage and
  reconstruction requirements are superseded by this decision.
