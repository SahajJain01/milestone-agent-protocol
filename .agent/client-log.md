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

## 2026-07-30 — Accepted milestone reopening

**Source:** Current Codex task.

The user requested that a delivered milestone be reopenable when later evidence, such as a bug found
weeks after delivery, requires another task against that milestone.

**Absorbed outcome:** M-003/T-003 and ADR 0003.

## 2026-08-06 — Accepted evidence-to-scope cross-questioning

**Source:** Current Codex task.

After using the protocol in a product repository, the user identified the feature-by-feature
cross-questioning process as valuable: safely archive a received client feature list, audit whether
each feature already exists and whether it fully covers the request, then resolve material product
questions with the human before formalizing a gap as a milestone or task. The user requested that
the reusable protocol enforce this behavior for future initialized and upgraded repositories.

**Absorbed outcome:** M-004/T-004 and ADR 0004.

## 2026-08-06 — Accepted skipped client-question lifecycle

**Source:** Current Codex task.

The user clarified that when the human cannot answer a material cross-question and says to skip it,
the protocol must preserve that exact question as unfinished work under the corresponding milestone.
At the end of cross-questioning, the agent must provide a consolidated client-ready question list.
The milestone remains blocked while any skipped-question task is unresolved. When the client answers,
the agent records the response as accepted evidence, incorporates the resulting facts into the
milestone, completes and removes the question task, and unblocks the milestone only after all such
questions are resolved.

**Absorbed outcome:** M-005/T-005 and ADR 0005.

## 2026-08-07 — Unverified milestone-visualization proposal

**Source:** Current Codex task.

The user proposed a frontend that would expose repository milestones for greater customer
transparency. The audit found that the current protocol keeps only unfinished milestones in the
working tree and relies on Git history for closed milestone definitions and reopen/reclose cycles,
which leaves no stable current-tree milestone history for a future read-only projection.

**Disposition:** Visualization, frontend generation, hosting, and publication are deferred. The
underlying milestone-history gap was reviewed separately and accepted below.

## 2026-08-07 — Accepted durable milestone lifecycle archive

**Source:** Current Codex task following review of the reopening contract.

The user requested a protocol revision that preserves completed milestone lifecycle records outside
the active todo, keeps visualization out of the present scope, and provides backward-compatible
migration for repositories initialized with earlier protocol versions. Existing historical closures
must not be invented during upgrade; Git-only milestones may be imported later only from stable,
unambiguous evidence.

**Absorbed outcome:** M-007/T-007 and ADR 0007.
