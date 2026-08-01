# ADR 0003: Reopen closed milestones under their original identity

- **Status:** Accepted
- **Date:** 2026-07-30
- **Supersedes:** None

## Context

Closed milestones leave the active todo after delivery. Later evidence, such as a production bug,
can show that more work is required to restore the delivered outcome. Treating that work as a new
milestone loses continuity, while restoring completed tasks rewrites history.

## Decision

- A closed milestone may return to the active todo only when new evidence requires work to restore
  or preserve its original end goal.
- Reopening reuses the historical milestone ID, name, end goal, and closure condition and records an
  ISO-dated reason with a stable evidence anchor.
- Every reopened work item receives a new, never-used task ID; completed tasks remain only in Git
  history.
- Work that materially changes the end goal receives a new milestone ID.
- The reopened milestone follows the ordinary closure rules and leaves the active todo again when
  its closure contract passes.

## Reason

The milestone ID represents a durable outcome, not one uninterrupted execution period. Reusing that
identity makes post-delivery repair traceable to the outcome it restores, while dated evidence and
new task IDs preserve an auditable, append-only history.

## Consequences

- Agents must inspect Git history before reopening a milestone or allocating its new task IDs.
- Active todo files gain one optional `Reopened` field for the current reopen cycle.
- Protocol 2.1.0 adds a managed reopening rule and a contiguous migration from 2.0.0.
- Git remains the record of prior closures, completed tasks, and earlier reopen/reclose cycles.
