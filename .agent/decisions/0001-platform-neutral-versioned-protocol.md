# ADR 0001: Use a platform-neutral versioned protocol with a thin optional adapter

- **Status:** Accepted
- **Date:** 2026-07-29
- **Supersedes:** None

## Context

The protocol must work when a user gives any capable LLM one public repository URL. It must also
support repositories already initialized by an earlier version without overwriting local context.
Codex can offer a convenient skill command, but making that skill normative would exclude other
agents.

## Decision

- `PROTOCOL.md` is the platform-neutral normative entrypoint and `protocol.yaml` declares its
  semantic version, digest, templates, and immutable migrations.
- Initialized targets record current provenance in `.agent/protocol.lock.yaml`.
- Repeated initialization reconciles the target: same-version runs are idempotent, upgrades require a
  complete ordered migration chain, and forks, downgrades, or local conflicts fail closed.
- `skills/initialize-agent-protocol` is a thin optional Codex adapter that routes to the same
  canonical files.
- Only paths declared by the protocol manifest are managed.

## Reason

Plain Markdown and YAML are readable by any web-capable agent. A versioned lock and declarative
migrations make later changes explicit and repeatable, while the thin adapter improves Codex
ergonomics without creating a second protocol.

## Consequences

- Normative changes require a version bump, updated digest, and migration when existing targets need
  reconciliation.
- Templates and adapters cannot override or duplicate `PROTOCOL.md`.
- A lock advances only after validation; local project content remains project-owned.
- Public releases must prove fresh initialization, idempotent rerun, and relevant upgrades.
