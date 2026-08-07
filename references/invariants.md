# Protocol invariants

This reference is explanatory. `PROTOCOL.md` is normative.

- One canonical unfinished-work record; no duplicate planning systems.
- One owning milestone per unfinished task.
- Every open milestone is explicitly `Active` or `Blocked`; unresolved skipped client questions make
  their owning milestone `Blocked` until resolution.
- Immutable milestone, task, decision, migration, and adoption identities.
- Reopening restores a historical milestone identity and outcome contract while adding only new task
  identities.
- Observable outcome closure remains separate from implementation completion.
- Source/tests establish behavior; decisions explain why; external evidence is not authorization.
- Unreviewed external features and features with no accepted owning outcome remain unverified;
  audited, accepted portions advance one coherent feature at a time without guessing skipped facts.
- Fully supported requests create coverage findings, partial gaps refine their existing owner, and
  new milestones represent only genuinely distinct accepted outcomes.
- Every explicitly skipped material question with accepted milestone ownership remains a blocked,
  client-ready task and appears in the end-of-pass handoff. Returned answers enter the client log and
  milestone facts before the task leaves the active todo.
- Repository-specific guidance is discovered, never copied from the protocol source.
- Reinitialization preserves project content and converges without duplicate records.
- Protocol state is recorded by the current lock and Git history.
- A lockless target is adopted only through a declared legacy specification, an immutable clean
  baseline, a reachable pre-lock evidence commit, and explicit human confirmation of that exact
  tuple. Adoption never invents a prior version or bypasses a historical lock.
- Same semantic version with a different digest is a fork, not an invisible update.
- A lock advances only after the corresponding structure, migrations, or adoption verifies.
