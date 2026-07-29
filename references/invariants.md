# Protocol invariants

This reference is explanatory. `PROTOCOL.md` is normative.

- One canonical unfinished-work record; no duplicate planning systems.
- One owning milestone per unfinished task.
- Immutable milestone, task, decision, and migration identities.
- Observable outcome closure remains separate from implementation completion.
- Source/tests establish behavior; decisions explain why; external evidence is not authorization.
- Repository-specific guidance is discovered, never copied from the protocol source.
- Reinitialization preserves project content and converges without duplicate records.
- Protocol state is a current lock plus Git history, never a session journal.
- Same semantic version with a different digest is a fork, not an invisible update.
- A lock advances only after the corresponding structure and migrations verify.
