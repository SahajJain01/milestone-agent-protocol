# Milestone Agent Protocol

A portable, milestone-first project context protocol for coding agents. It gives a repository one
authoritative unfinished-work record, immutable architectural decisions, evidence-safe client
provenance, scoped `AGENTS.md` guidance, and a deterministic way to initialize or upgrade the
structure later.

Closed milestones live in an indexed, append-only lifecycle archive while completed task bodies
leave the active todo. This preserves milestone outcome contracts and closure/reopening evidence in
the current tree without turning the archive into a second backlog or relying exclusively on Git
history. Protocol 2.4.0 adds the archive through a contiguous migration for earlier locked releases;
upgrades declare a forward-only coverage boundary instead of inventing older closures.

External feature lists are reconciled through an evidence-to-scope loop: audit existing coverage,
cross-question material product ambiguity one feature at a time, and formalize only accepted gaps
without duplicating work or treating client input as implementation authorization. Material
questions the human explicitly skips remain visible as client-ready blocked tasks under their owning
milestones; returned answers are absorbed into milestone facts before those tasks are removed.

The protocol is agent-agnostic. A plugin is not required.

This repository does not generate a visualization, frontend, hosting configuration, or deployment.
The lifecycle archive is a platform-neutral data contract that a separately authorized read-only
tool may consume in the future.

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
- reports an eligible pre-lock adoption candidate and waits for explicit confirmation,
- or stops safely when it finds a fork, downgrade, incomplete migration chain, or conflicting local
  change.

## Adopt a repository that predates protocol locks

Repositories containing milestone-first records but no `.agent/protocol.lock.yaml` remain conflicts
under an ordinary initialization request. The current protocol declares a separate, fail-closed
2.4.0 adoption path for targets whose Git history proves they were deliberately structured before
locks existed. It creates a forward-only milestone archive only after the required audit and explicit
authorization; it does not fabricate earlier closures.

Ask the agent to audit first:

```text
Audit this repository for legacy-unlocked adoption using
https://github.com/SahajJain01/milestone-agent-protocol
```

The agent validates the declared adoption specification and reports the canonical source, requested
ref, resolved source commit, immutable target baseline commit, historical evidence commit, exact
managed-path patch, and local divergences without writing. Adoption begins only after the human
explicitly confirms that complete tuple. The resulting target decision and lock record adoption
without inventing a prior version; all later runs use normal locked reconciliation.

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
checkout remaining on disk. It can audit a declared legacy-unlocked candidate but still waits for
the protocol-required explicit confirmation before writing. `PROTOCOL.md` remains the canonical
contract for every agent.

## License

[MIT](LICENSE)
