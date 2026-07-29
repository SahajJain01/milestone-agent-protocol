# ADR 0002: Use a positive-only initialization contract

- **Status:** Accepted
- **Date:** 2026-07-29
- **Supersedes:** The target-classification and record-policy clauses of ADR 0001

## Context

The reusable source should describe the structure it owns using a positive managed-path boundary.
Every reconciled installation needs deterministic provenance, while future updates still need a
safe path for repositories initialized by a released protocol version.

## Decision

- The manifest declares the complete set of required target paths and managed rule identities.
- Fresh initialization is allowed only when protocol-managed paths do not already exist.
- Reconciliation and upgrades require a valid `.agent/protocol.lock.yaml`.
- Protocol-managed paths without a valid lock are a conflict and produce no writes.
- Files outside the declared scope remain project-owned and unchanged.

## Reason

A positive ownership boundary is small, clear, and deterministic.

## Consequences

- Version 2.0.0 requires a valid lock for reconciliation.
- Versioned installations retain same-version reconciliation and ordered upgrades.
- Ambiguous ownership produces a conflict report and no writes.
