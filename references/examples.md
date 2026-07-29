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

## Safe repeated initialization

A target locked at version `1.1.0` is initialized again against source version `1.3.0`. The agent
validates and applies `1.1.0-to-1.2.0`, then `1.2.0-to-1.3.0`, verifies the result, and updates the
lock last. If either migration is absent or conflicts with a project-owned edit, the agent stops with
the old lock intact.
