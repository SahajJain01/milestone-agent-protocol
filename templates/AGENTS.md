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

- Milestones use immutable `M-###` IDs and include a state of `Active` or `Blocked`, `End goal`, and
  observable `Close when`.
- Tasks use immutable `T-###` IDs, exactly one owning milestone, a state of `Active`, `Blocked`,
  `Queued`, or `Deferred`, real source anchors, dependencies when relevant, and acceptance bullets.
- Allocate IDs after checking the current file and Git history; never recycle them.
- Reopen a closed milestone only for work that restores or preserves its original end goal. Reuse
  its historical ID and outcome contract, record a dated reason and evidence anchor, and add only
  new task IDs. Create a new milestone when the end goal changes materially.
- Remove completed tasks and closed milestones from the active todo; Git retains their history.
- Local tests do not replace required runtime, provider, visual, infrastructure, physical,
  publication, or client evidence.
- A milestone containing any unfinished skipped client-question task is `Blocked` and cannot close;
  unrelated safe tasks may continue.

## DOCUMENTATION RECORDS

- `.agent/todo.md` owns unfinished work.
- `.agent/decisions/` owns indexed immutable decisions.
- `.agent/client-log.md` owns dated, source-attributed external evidence.
- `.agent/protocol.lock.yaml` owns current protocol provenance and version state.
- Create and reconcile only paths declared by the protocol manifest.

## EXTERNAL FEATURE INTAKE

- Archive a received client or external feature batch in `.agent/client-log.md` as unverified
  evidence before treating any item as scope; exclude secrets, raw identifiers, full PII, and
  unrelated content.
- Reconcile one coherent feature at a time. Audit implemented source/tests, accepted decisions, and
  existing milestones/tasks before asking product questions.
- Report whether the feature is fully supported, partially supported, or missing. Cite coverage,
  identify the exact gap, and create no work for behavior that already fully covers the request.
- Cross-question the human only on unresolved choices that materially affect behavior, boundaries,
  states, data authority, UX, failure handling, effects, verification, ownership, or priority. Keep
  questions incremental; do not guess or use a generic questionnaire.
- Link accepted answers to a dated evidence anchor. Refine existing scope when its outcome is
  unchanged; split independently verifiable work or create a new milestone only for a distinct
  durable outcome. Leave all unreviewed items explicitly unverified.
- If the human explicitly skips or cannot answer a material question, preserve each independently
  answerable question as a `Blocked` client-question task under its accepted owning milestone and
  mark that milestone `Blocked`. Keep exact client-ready wording and do not invent a milestone when
  no accepted outcome can yet be identified.
- At the end of the pass, provide one unsent question list grouped by milestone/task ID. When answers
  return, archive them as accepted evidence, add their facts to the corresponding milestone, update
  affected scope records, remove the completed question tasks, and unblock the milestone only when
  no skipped question or other blocker remains.
- Formalizing scope authorizes planning-record changes only, not implementation or external effects.

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
