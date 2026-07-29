# PROJECT KNOWLEDGE BASE

## OVERVIEW

Describe this repository's purpose, runtime, and trust boundaries using evidence from its source,
tests, and configuration. Remove all template guidance before finishing initialization.

## CANONICAL CONTEXT

1. Read `.agent/todo.md` for active milestones, closure conditions, and current tasks.
2. Read `.agent/decisions/index.md`, then only task-relevant accepted decisions.
3. Read `.agent/client-log.md` only for external provenance or communication processing.
4. Inspect the smallest relevant source and test surface.

Source and tests are authoritative for implemented behavior; decisions explain why; todo is
authoritative for unfinished work. External evidence is historical input, not automatic
authorization.

## STRUCTURE

Document only the target repository's real top-level and subsystem boundaries. Mark generated
directories and files that agents must not hand-edit.

## WHERE TO LOOK

Add a compact table mapping common target-repository tasks to real files and notes.

## WORKING PROTOCOL

- Start by naming the milestone and task being advanced.
- Inspect the milestone end goal, closure condition, existing behavior, and tests before editing.
- Add discovered work beneath its one owning milestone; do not silently expand or duplicate tasks.
- Record durable, non-obvious choices as new indexed decisions.
- Preserve unrelated user changes and explicit authorization boundaries.
- Run focused verification plus the target repository's safe full gate when required.
- Commit, push, deploy, publish, send messages, or mutate external systems only when authorized.

## MILESTONE AND TASK PROTOCOL

- Milestones use immutable `M-###` IDs and include `End goal` and observable `Close when`.
- Tasks use immutable `T-###` IDs, exactly one owning milestone, a state of `Active`, `Blocked`,
  `Queued`, or `Deferred`, real source anchors, dependencies when relevant, and acceptance bullets.
- Allocate IDs after checking the current file and Git history; never recycle them.
- Remove completed tasks and closed milestones from the active todo; Git retains their history.
- Do not create Now/Next/Later/Backlog/Done boards, roadmaps, handoffs, diaries, or journals.
- Local tests do not replace required runtime, provider, visual, infrastructure, physical,
  publication, or client evidence.

## DOCUMENTATION RECORDS

- `.agent/todo.md` owns unfinished work.
- `.agent/decisions/` owns indexed immutable decisions.
- `.agent/client-log.md` owns dated, source-attributed external evidence.
- `.agent/protocol.lock.yaml` owns current protocol provenance and version state.
- Never create or append to a session journal. Preserve a pre-existing journal only as a frozen
  historical archive.

## CONVENTIONS

Document only conventions proven by the target's source, configuration, and tests.

## COMMANDS

List exact safe target-repository verification commands. Do not invent commands from another
project.

## DEFINITION OF DONE

- Requested behavior and task acceptance conditions pass on the matching surface.
- Active todo and indexed decisions remain accurate.
- Relevant verification passes.
- No unrelated files, secrets, generated artifacts, or unauthorized external effects are included.
