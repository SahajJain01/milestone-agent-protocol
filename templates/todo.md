# Milestones and active work

This is the authoritative record of unfinished work. Milestones are ordered by current priority.
Completed tasks and closed milestones leave this file after the milestone lifecycle archive is
updated. Git retains completed task bodies and the audit history.

<!--
Do not invent work to populate this template. If repository evidence shows no unfinished work,
replace the example block with: "No active milestones."

Do not promote an unverified external feature list into this file as a batch. Audit one coherent
feature against existing behavior and scope, answer its material product questions with the human or
explicitly preserve skipped questions under accepted ownership, and link the accepted outcome to a
dated `.agent/client-log.md` anchor. Fully covered behavior adds no task; partial gaps refine their
existing owner before a new milestone is considered.

Every milestone has `State: Active` or `State: Blocked`. If the human explicitly skips a material
question that belongs to an accepted milestone, add one `Blocked` client-question task per
independently answerable question, preserve its exact client-ready wording, and set the milestone to
`Blocked`. It cannot close until every such answer is archived and absorbed into `Accepted facts`
and affected scope records. Then remove the completed question task and restore `Active` only when
no other blocker remains. Do not create a speculative milestone if no accepted outcome exists yet.

To reopen a closed milestone, read its indexed `.agent/milestones/M-###.md` lifecycle record, restore
the same ID, name, `End goal`, and `Close when`, append a reopening entry to that record, and add
`**Reopened:** YYYY-MM-DD — Reason and stable evidence anchor.`, and add at least one unfinished task
with a new, never-used task ID. If the milestone predates archive coverage, import it first only when
stable Git evidence is unambiguous. Do not copy completed tasks back into this file.

Before removing a closed milestone, create or extend its indexed lifecycle record with the original
outcome contract, the next numbered closure entry, stable closure evidence, and completed task IDs.
Do not copy completed task bodies into the archive.

## M-001 — Observable outcome

**State:** Active

**End goal:** Durable outcome, not a component, sprint, or collection of chores.

**Close when:** Observable closure condition, including any real runtime or external evidence.

**Accepted facts:**

- Include only externally answered facts that materially constrain this outcome, each with a stable
  `.agent/client-log.md` anchor; otherwise omit this field.

### T-001 — Independently verifiable task

**State:** Active

**Source / code:** Real repository paths, accepted evidence, or decision anchors.

**Dependencies:** Task and milestone IDs, or `None`.

**Acceptance:**

- Concrete condition on the matching surface.
- Required verification or external evidence.

### T-002 — Ask the client one unresolved material question

**State:** Blocked

**Question for client:** Exact client-ready wording ending in a question mark?

**Source / code:** Cross-questioning session plus the stable unverified or accepted evidence anchor.

**Dependencies:** Client response.

**Acceptance:**

- The returned answer is archived under a dated accepted client-log anchor.
- The resulting fact is added to the owning milestone and any affected task or decision is refined.
- This task remains in the final grouped client-question handoff until resolved.
-->
