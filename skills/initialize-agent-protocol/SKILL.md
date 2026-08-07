---
name: initialize-agent-protocol
description: Initialize, reconcile, explicitly adopt eligible pre-lock records into, or upgrade the milestone-first agent context protocol in a repository. Use when a user asks to initialize, adopt, reconcile, refresh, or update a repository from the milestone-agent-protocol source, including repositories initialized before locks existed or by an older released version.
---

# Initialize Agent Protocol

## Overview

This is a thin Codex adapter for the platform-neutral protocol at the repository root. Do not
duplicate or reinterpret the protocol in this skill.

## Workflow

1. Use the protocol repository URL in the user's request. If the user invokes the skill without a
   source URL, default to `https://github.com/SahajJain01/milestone-agent-protocol`.
2. Fetch `protocol.yaml` from that repository and ref, then fetch the declared `PROTOCOL.md`
   completely. Do not assume this installed skill has a parent checkout containing those files.
3. Validate the entrypoint, template, migration, and adoption digests before changing the target.
4. Follow the fetched `PROTOCOL.md` for discovery, fresh initialization, same-version reconciliation,
   version upgrades, conflicts, verification, and reporting.
5. Treat the user's initialize or update request as authorization only for target protocol records.
   Preserve product files, unrelated dirty work, and external-effect boundaries.

## Reinitialization

Assume the target may already be initialized. Read `.agent/protocol.lock.yaml` when present, compare
its version and digest with the validated source, and apply only a complete ordered migration chain.
A conforming same-version rerun must produce no diff. Never overwrite local divergence, silently
downgrade, accept a same-version digest fork, or update the lock before verification.

## Legacy-unlocked adoption

Missing managed-path provenance remains a conflict by default. When the source manifest declares an
applicable legacy adoption, follow its fetched `PROTOCOL.md` procedure exactly: audit without writes,
report the canonical source, requested ref, resolved source commit, target baseline commit, and
evidence commit, and show the complete protocol-record patch and divergences. Proceed only after the
human explicitly confirms that exact tuple; do not reuse a generic initialize request as adoption
authorization.

Validate the adoption specification again before writing, create its indexed target decision as the
recovery anchor, reconcile only declared paths, and write the lock last with adoption provenance
separate from migrations. Never invent a prior version or use adoption to bypass a historical lock.

## Failure behavior

If the source is inaccessible or invalid, a migration or adoption is missing, adoption lacks exact
post-audit authorization, ownership is ambiguous, or verification fails, stop without creating or
advancing the lock. Report the exact blocker and a safe manual patch when possible. Never guess a
fallback protocol.
