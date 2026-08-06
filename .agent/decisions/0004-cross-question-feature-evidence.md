# ADR 0004: Cross-question external feature evidence before accepting scope

- **Status:** Accepted
- **Date:** 2026-08-06
- **Supersedes:** None

## Context

Client messages and meeting notes often arrive as lists of requested features. Treating the list as
accepted scope creates speculative or duplicate milestones, while merely archiving it can leave the
product ambiguity unresolved. A product-repository session demonstrated a useful middle path: retain
the complete safe intake as unverified evidence, inspect actual coverage, and resolve one feature's
material questions with the human before formalizing its gap.

## Decision

The protocol requires an evidence-to-scope cross-questioning loop for client or other external
feature input:

1. Archive the safe, source-attributed feature intake as unverified evidence without treating it as
   authorization.
2. Reconcile one coherent feature at a time against implemented source and tests, accepted
   decisions, and the active milestone/task hierarchy.
3. Report whether the requested behavior is fully supported, partially supported, or missing, with
   concrete coverage and gap evidence.
4. Ask concise human questions only for unresolved choices that materially affect the outcome,
   boundaries, state transitions, operator/customer behavior, data or configuration authority,
   failure handling, effects, acceptance evidence, ownership, or priority. Continue until the
   feature is sufficiently precise to accept, defer, reject, or leave unverified.
5. Link accepted answers back to the evidence anchor. Refine the existing owning task when its
   outcome is unchanged; split independently verifiable work or create a new milestone only for a
   genuinely distinct outcome. Never duplicate scope that already exists.

Fully covered behavior produces a coverage finding rather than invented work. Existing authoritative
evidence avoids redundant questions. Promotion into planning records does not authorize product
implementation, deployment, publication, messages, or other external effects.

## Reason

This workflow preserves the client log as evidence while making the human the authority for product
meaning. Auditing first prevents unnecessary questions and duplicate scope; feature-by-feature
questioning makes milestone end goals and task acceptance conditions concrete enough to execute and
verify.

## Consequences

- Unreviewed items in a multi-feature intake remain explicitly unverified while reviewed items can
  advance independently.
- Agents must show existing coverage before proposing work and must distinguish a partial gap from a
  missing capability.
- Questions stay material and incremental instead of becoming a generic requirements questionnaire.
- Accepted answers need stable provenance links in resulting tasks and durable decisions.
- Protocol 2.2.0 adds a managed cross-questioning rule and a contiguous migration from 2.1.0.
