---
name: initialize-agent-protocol
description: Initialize or upgrade the milestone-first agent context protocol in a repository. Use when a user asks to initialize, adopt, reconcile, refresh, or update a repository from the milestone-agent-protocol source, including repositories that may already contain an older or locally adapted structure.
---

# Initialize Agent Protocol

## Overview

This is a thin Codex adapter for the platform-neutral protocol at the repository root. Do not
duplicate or reinterpret the protocol in this skill.

## Workflow

1. Resolve this skill's repository root.
2. Read `protocol.yaml` and then the declared `PROTOCOL.md` completely.
3. Validate the entrypoint digest and migration inventory before changing the target.
4. Follow `PROTOCOL.md` for discovery, fresh initialization, legacy adoption, same-version
   reconciliation, upgrades, conflicts, verification, and reporting.
5. Treat the user's initialize or update request as authorization only for target protocol records.
   Preserve product files, unrelated dirty work, and external-effect boundaries.

## Reinitialization

Assume the target may already be initialized. Read `.agent/protocol.lock.yaml` when present, compare
its version and digest with the validated source, and apply only a complete ordered migration chain.
A conforming same-version rerun must produce no diff. Never overwrite local divergence, silently
downgrade, accept a same-version digest fork, or update the lock before verification.

## Failure behavior

If the source is inaccessible or invalid, a migration is missing, ownership is ambiguous, or
verification fails, stop without advancing the lock. Report the exact blocker and a safe manual
patch when possible. Never guess a fallback protocol.
