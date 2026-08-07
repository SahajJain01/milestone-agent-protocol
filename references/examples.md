# Minimal examples

These examples illustrate `PROTOCOL.md`; they are not extra rules.

## Empty active todo

```markdown
# Milestones and active work

This is the authoritative record of unfinished work. Closed milestone lifecycles are archived;
completed task bodies remain in Git history.

No active milestones.
```

In protocol 2.4.0, the target also has `.agent/milestones/index.md`. A fresh target marks its archive
complete from initialization; an upgraded or adopted target marks it forward-only from the 2.4.0
reconciliation timestamp so earlier Git-only closures are not falsely claimed.

## One active outcome

```markdown
## M-004 — Publish a verified command-line release

**State:** Active

**End goal:** Users can install and run a reproducible signed release.

**Close when:** Package installation, signature verification, and a clean-machine smoke test pass.

### T-011 — Add the release verification job

**State:** Active

**Source / code:** `.github/workflows/release.yml`; `scripts/verify-release.sh`; ADR 0007.

**Dependencies:** None.

**Acceptance:**

- The job verifies the built package and signature.
- A clean fixture installs and runs the package without repository-local dependencies.
```

## Closed and archived outcome

When `M-004` passes its closure contract, create `.agent/milestones/M-004.md`, add its one stable
index row, and then remove the milestone and completed task body from the active todo:

```markdown
# M-004 — Publish a verified command-line release

**End goal:** Users can install and run a reproducible signed release.

**Close when:** Package installation, signature verification, and a clean-machine smoke test pass.

## Closure 1

**Closed:** 2026-07-30

**Outcome:** The signed package installs and runs on the supported clean-machine fixture.

**Closure evidence:**

- Release verification run `build-4821` and signed artifact manifest at commit `abc1234`.

**Completed task IDs:**

- T-011
```

The archive keeps only the task ID. The completed task body and full diff remain in Git history.

## Reopened outcome

Suppose `M-004` was closed and removed after `T-011` completed. Weeks later, issue `#482` shows that
the published command-line release fails on a supported clean machine. Validate the indexed record,
append `Reopening 1` with the issue evidence and new task ID `T-019`, then return the matching outcome
contract to the active todo:

```markdown
## M-004 — Publish a verified command-line release

**State:** Active

**End goal:** Users can install and run a reproducible signed release.

**Close when:** Package installation, signature verification, and a clean-machine smoke test pass.

**Reopened:** 2026-07-30 — Issue #482 reproduces an installation failure on a supported clean
machine.

### T-019 — Fix installation on the affected clean-machine configuration

**State:** Active

**Source / code:** Issue #482; `src/installer`; `tests/install`.

**Dependencies:** None.

**Acceptance:**

- The issue #482 reproduction installs and runs successfully.
- The original package, signature, and clean-machine closure checks pass again.
```

`M-004` keeps its identity and outcome contract, while `T-019` is new. `T-011` remains a reference in
the archive and its body remains in Git history. Reclosure appends `Closure 2` before removing the
milestone from the todo again. If the requested work instead introduces a different release outcome,
allocate a new milestone.

If `M-004` closed before the target's archive coverage began, first reconstruct and import its record
from stable Git commits. Add an `Imported` date and those commit anchors to `Closure 1`. If the latest
contract or closure cannot be proved unambiguously, stop without reopening.

## Safe repeated initialization

A target locked at version `1.1.0` is initialized again against source version `1.3.0`. The agent
validates and applies `1.1.0-to-1.2.0`, then `1.2.0-to-1.3.0`, verifies the result, and updates the
lock last. If either migration is absent or conflicts with a project-owned edit, the agent stops with
the old lock intact.

## Explicit pre-lock adoption

A Git repository already contains tracked `AGENTS.md`, `.agent/todo.md`,
`.agent/client-log.md`, and `.agent/decisions/index.md`, but no protocol lock. Reachable history shows
that one commit deliberately converted the repository to milestone-first work records, and no ref
has ever contained `.agent/protocol.lock.yaml`.

An ordinary initialization reports a legacy-unlocked candidate and writes nothing. The agent
validates the declared adoption specification, confirms the managed paths are clean at baseline
commit `B`, identifies conversion commit `E`, constructs the complete protocol-record patch, and
presents the canonical source, requested ref, resolved source commit, plus `B` and `E`. Only after
the human explicitly confirms that tuple does the agent add an indexed adoption decision, reconcile
current structural rules, verify the target, and write the lock last. The lock records the adoption
ID and decision anchor with no invented prior version. A second initialization is a locked
same-version no-op.

If any reachable ref contains a historical lock, the managed paths are dirty, the conversion commit
is ambiguous, or existing records claim a conflicting source, adoption aborts with no lock. Deleting
a lock can never turn a versioned target into a legacy candidate.

## External feature intake

A client sends a list containing recurring ordering hours, a temporary pause button, and stock
controls. Archive the complete safe list under one dated unverified client-log anchor, then inspect
recurring hours first.

If the repository already stores weekly hours and validates pickup times but does not gate order
confirmation by the current time, report it as partial coverage. Ask only the material questions:
what remains possible while closed, whether future orders are allowed, how multiple daily windows
work, and what the customer is told. Record the accepted answers under a dated anchor, refine an
existing operational-policy task when it already owns that outcome, or create a distinct milestone
only when no current outcome owns it.

The pause and stock requests remain unverified until their own audits. If stock controls later prove
to cover the request completely, cite that behavior and its tests without inventing a stock task.
None of these planning changes authorizes implementation or deployment.

Suppose enough accepted answers place the pause behavior under `M-006`, but the human says, "Skip
whether pausing takes effect immediately or waits for catalog publication; I need to ask the client."
Create a new task such as `T-017` under `M-006`, set both the task and milestone to `Blocked`, and
preserve the exact client-ready question:

```markdown
## M-006 — Temporarily pause new orders

**State:** Blocked

**End goal:** Operators can temporarily stop new confirmations while preserving safe customer use.

**Close when:** The accepted pause contract passes operator and customer acceptance evidence.

### T-017 — Ask when a pause takes effect

**State:** Blocked

**Question for client:** Should Pause and Resume take effect immediately, without using the catalog
Publish action?

**Source / code:** Dated intake anchor and the current cross-questioning session.

**Dependencies:** Client response.

**Acceptance:**

- The answer is archived under a dated accepted client-log anchor.
- The resulting fact is added to M-006 and affected task or decision language is reconciled.
```

At the end of the pass, include `M-006 / T-017` in the consolidated unsent question list. If the
client answers "immediately," add that fact and its evidence anchor to M-006, update any affected
acceptance conditions, remove T-017, and return M-006 to `Active` if it has no other blocker. If the
question was skipped before any accepted outcome could identify an honest milestone, keep the
feature unverified instead of creating a speculative container.
