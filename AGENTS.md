# PROJECT KNOWLEDGE BASE

## OVERVIEW

`milestone-agent-protocol` is a platform-neutral, versioned protocol for initializing and upgrading
milestone-first agent context in arbitrary repositories. `PROTOCOL.md` is normative; templates,
migrations, adoption specifications, references, and the optional Codex skill support it without
duplicating authority.

## CANONICAL CONTEXT

1. Read `.agent/todo.md` for active milestones, closure conditions, and current tasks.
2. Read `.agent/decisions/index.md`, then only task-relevant accepted decisions.
3. Read `.agent/client-log.md` only for external provenance.
4. Inspect `PROTOCOL.md`, `protocol.yaml`, and the smallest relevant template, migration, adoption,
   or adapter.

The protocol and metadata are authoritative for behavior; decisions explain why; todo owns unfinished
work.

## STRUCTURE

```text
PROTOCOL.md                         # canonical any-LLM contract
protocol.yaml                       # version, digests, templates, migrations, adoptions
templates/                          # target-tailored starting structures
migrations/                         # immutable declarative upgrade specifications
adoptions/                          # immutable pre-lock adoption specifications
references/                         # non-normative explanations and examples
skills/initialize-agent-protocol/   # optional thin Codex adapter
.agent/                             # this repository's own canonical context
```

## WORKING PROTOCOL

- Advance one task under one milestone and preserve immutable IDs.
- When external evidence proposes features, archive the complete safe intake as unverified, audit
  one coherent feature against code/tests and existing scope, and cross-question only material human
  choices before accepting or formalizing its gap. Persist explicitly skipped material questions as
  blocked tasks under their owning milestones, block those milestones until reconciliation, and
  provide a grouped unsent client-question handoff. Never batch-promote unanswered items.
- Reopen a closed milestone only to restore or preserve its original end goal. Reuse its historical
  ID and outcome contract, record a dated reason and stable evidence anchor, and allocate new task
  IDs. Create a new milestone when the end goal changes materially.
- Keep normative rules in `PROTOCOL.md`; adapters and references point to it instead of copying it.
- Bump the semantic version for every published normative change.
- Add an immutable contiguous migration for changes that existing initialized repositories must
  adopt. Update `protocol.yaml` digests after content is final.
- Keep pre-lock adoption distinct from version migration: require a declared specification, a
  history-backed audit, and explicit post-audit human authorization without inventing a prior
  version.
- Prove fresh initialization, same-version idempotence, and applicable upgrade paths on disposable
  fixtures.
- Create and reconcile only paths declared by the protocol manifest.
- Run the skill validator and `git diff --check`; verify all declared template, migration, adoption,
  and entrypoint digests plus internal links.
- Commit and push only focused, verified protocol units.

## AUTHORIZATION

Repository creation and public publication require explicit user authorization. Initialization of a
target authorizes only protocol-record changes; never infer product edits, commits, pushes,
deployments, messages, or other external effects.

## DEFINITION OF DONE

- `PROTOCOL.md`, `protocol.yaml`, templates, migrations, adoptions, and the skill agree.
- Declared digests, links, schemas, fixture behavior, and idempotence checks pass.
- Existing target content and unrelated dirty work remain unchanged.
- The active task is removed after completion; Git retains history.
