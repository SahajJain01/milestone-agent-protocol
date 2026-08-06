# Milestone Agent Protocol

A portable, milestone-first project context protocol for coding agents. It gives a repository one
authoritative unfinished-work record, immutable architectural decisions, evidence-safe client
provenance, scoped `AGENTS.md` guidance, and a deterministic way to initialize or upgrade the
structure later.

External feature lists are reconciled through an evidence-to-scope loop: audit existing coverage,
cross-question material product ambiguity one feature at a time, and formalize only accepted gaps
without duplicating work or treating client input as implementation authorization. Material
questions the human explicitly skips remain visible as client-ready blocked tasks under their owning
milestones; returned answers are absorbed into milestone facts before those tasks are removed.

The protocol is agent-agnostic. A plugin is not required.

## Use from any LLM agent

Open the target repository in an agent with web access and say:

```text
Initialize this repository using
https://github.com/SahajJain01/milestone-agent-protocol
```

The agent must read [`PROTOCOL.md`](PROTOCOL.md) and [`protocol.yaml`](protocol.yaml), inspect the
target repository, and initialize or reconcile the structure without overwriting project-specific
content. Fresh initialization requires the declared protocol paths to be available. Every subsequent
reconciliation uses the target's verified `.agent/protocol.lock.yaml`.

Running the same instruction again is supported. The agent reads `.agent/protocol.lock.yaml`,
compares the recorded version and digest with this repository, and either:

- performs a no-op conformance audit,
- applies every required migration in order,
- or stops safely when it finds a fork, downgrade, incomplete migration chain, or conflicting local
  change.

## Optional Codex command

Codex users may install the thin skill in
[`skills/initialize-agent-protocol`](skills/initialize-agent-protocol/SKILL.md), then ask:

```text
Install the initialize-agent-protocol skill from
https://github.com/SahajJain01/milestone-agent-protocol/tree/main/skills/initialize-agent-protocol
```

After installation:

```text
Use $initialize-agent-protocol to initialize this repository.
```

The installed skill fetches the same public protocol; it does not depend on the rest of its original
checkout remaining on disk. `PROTOCOL.md` remains the canonical contract for every agent.

## License

[MIT](LICENSE)
