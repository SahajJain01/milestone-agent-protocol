# Minimal examples

These examples illustrate `PROTOCOL.md`; they are not extra rules.

## Empty active todo

```markdown
# Milestones and active work

This is the authoritative record of unfinished work. Completed work remains in Git history.

No active milestones.
```

## One active outcome

```markdown
## M-004 — Publish a verified command-line release

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

## Reopened outcome

Suppose `M-004` was closed and removed after `T-011` completed. Weeks later, issue `#482` shows that
the published command-line release fails on a supported clean machine. Reconstruct the latest closed
definition from Git history and return it to the active todo:

```markdown
## M-004 — Publish a verified command-line release

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

`M-004` keeps its identity and outcome contract, while `T-019` is new. `T-011` remains completed in
Git history. If the requested work instead introduces a different release outcome, allocate a new
milestone.

## Safe repeated initialization

A target locked at version `1.1.0` is initialized again against source version `1.3.0`. The agent
validates and applies `1.1.0-to-1.2.0`, then `1.2.0-to-1.3.0`, verifies the result, and updates the
lock last. If either migration is absent or conflicts with a project-owned edit, the agent stops with
the old lock intact.

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
