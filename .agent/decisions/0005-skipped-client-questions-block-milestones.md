# ADR 0005: Preserve skipped client questions as milestone blockers

- **Status:** Accepted
- **Date:** 2026-08-06
- **Supersedes:** None

## Context

During evidence-to-scope cross-questioning, the human may know enough to establish an owning product
outcome but be unable to answer one or more material questions without consulting the client. Leaving
those questions only in chat loses the dependency; guessing silently changes scope; and keeping the
whole feature merely unverified hides otherwise accepted work from its corresponding milestone.

Source: `.agent/client-log.md`, "2026-08-06 — Accepted skipped client-question lifecycle."

## Decision

When the human explicitly skips or cannot answer a material cross-question and an accepted owning
milestone can be identified:

1. Record every unresolved client-facing question in one or more `Blocked` client-question tasks
   under that milestone. Each task includes exact client-ready wording, its evidence source, and
   acceptance requiring a client response to be archived and reconciled.
2. Mark the owning milestone `Blocked`. It cannot close while any skipped client-question task
   remains unfinished, even if implementation work can continue safely.
3. At the end of the cross-questioning pass, present a consolidated unsent question list grouped by
   milestone and task ID. Drafting the list does not authorize sending it.
4. When answers return, append a dated accepted client-log record, add the accepted facts to the
   corresponding milestone, and refine its outcome, closure, task acceptance, or a durable decision
   wherever the answer materially affects them.
5. Complete and remove the question task only after that reconciliation is verified. Return the
   milestone to `Active` only when no skipped client-question task remains, unless another explicit
   blocker still applies.

If the unanswered choice prevents identifying any accepted outcome at all, the feature remains
unverified until enough evidence exists to place it honestly; the protocol must not invent a
speculative milestone merely to hold a question.

## Reason

The active milestone hierarchy is the authoritative unfinished-work record. Keeping client questions
there makes their ownership, blocking effect, and resolution criteria visible, while the client log
preserves provenance and the milestone records the accepted product facts.

## Consequences

- Skipped material questions cannot disappear between a cross-questioning session and client
  follow-up.
- Client-question tasks are planning dependencies, not implementation tasks or authorization to
  contact the client.
- A milestone with any unresolved skipped client question is visibly blocked from closure.
- Returned answers update both evidence provenance and the corresponding milestone contract before
  the temporary question tasks leave the active todo.
