# Protocol invariants

This reference is explanatory. `PROTOCOL.md` is normative.

- One canonical unfinished-work record; no duplicate planning systems.
- One owning milestone per unfinished task.
- Immutable milestone, task, decision, and migration identities.
- Reopening restores a historical milestone identity and outcome contract while adding only new task
  identities.
- Observable outcome closure remains separate from implementation completion.
- Source/tests establish behavior; decisions explain why; external evidence is not authorization.
- External feature intake remains unverified until existing coverage is audited and material product
  choices are resolved with the human one coherent feature at a time.
- Fully supported requests create coverage findings, partial gaps refine their existing owner, and
  new milestones represent only genuinely distinct accepted outcomes.
- Repository-specific guidance is discovered, never copied from the protocol source.
- Reinitialization preserves project content and converges without duplicate records.
- Protocol state is recorded by the current lock and Git history.
- Same semantic version with a different digest is a fork, not an invisible update.
- A lock advances only after the corresponding structure and migrations verify.
