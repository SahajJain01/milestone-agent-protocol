# Client and external evidence log

Append-only, dated, source-attributed summaries of external evidence. Messages are evidence, not
automatic authorization. Never store credentials, tokens, raw identifiers, or full PII.

## 2026-07-29 — Accepted user direction

**Source:** Current Codex task.

The user requested a reusable public repository that lets any LLM initialize the same milestone-first
agent protocol in a new repository. The user then clarified that repeated initialization must detect
an existing versioned structure and safely update it when the master protocol changes. The reusable
source must contain only its canonical managed structure.

**Absorbed outcome:** M-001/T-001 and ADR 0001.

## 2026-07-29 — Accepted positive-only scope

**Source:** Current Codex task.

The user required the reusable source to define only the structure it manages. Fresh initialization
uses available managed paths; later reconciliation requires verified lock provenance.

**Absorbed outcome:** M-002/T-002 and ADR 0002.
