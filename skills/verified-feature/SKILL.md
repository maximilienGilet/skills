---
name: verified-feature
description: Use when building or completing a non-trivial feature end to end with approved requirements, impact analysis, test-first implementation, independent review, and user-owned acceptance testing.
---

# Verified Feature

## Overview

A feature is verified only when its behavior is agreed, every material requirement has evidence, review is resolved, and the user accepts the real workflow.

**REQUIRED SUB-SKILLS:** Use `brainstorming`, `writing-plans`, `impact-check`, `test-driven-development`, `verification-before-completion`, `requesting-code-review`, `receiving-code-review`, and `feature-qa`. Use `verified-fix` for defects found after implementation.

## Gate 1: Approved Intent

Clarify users, constraints, non-goals, observable behavior, edge cases, and acceptance criteria through `brainstorming`; obtain explicit approval.

Write and approve an implementation plan with small verifiable slices before production edits. Shortcut pressure may shorten the plan, not remove agreement on behavior.

## Gate 2: Bounded Impact

Run `impact-check`. Resolve or explicitly carry unknown consumers, data changes, permissions, compatibility, rollout, and rollback concerns.

Create a traceability ledger for each material acceptance criterion:

```text
criterion → implementation slice → automated check → manual scenario or N/A reason
```

## Gate 3: Test-First Delivery

Implement one plan slice at a time:

1. write the smallest truthful failing test
2. run it and confirm the expected failure
3. implement the minimum code
4. run focused checks
5. keep the durable plan and ledger current

Do not bundle unrelated cleanup. If requirements change, stop, update the design, impact map, plan, and user approval before continuing.

## Gate 4: Fresh Technical Proof

Run focused and broader tests, diagnostics, type/lint/build, integration or contract checks, and risk-specific validation. Inspect the diff and trace every criterion to fresh evidence.

## Gate 5: Independent Review

Give a fresh reviewer the approved requirements, impact map, plan, diff, and verification evidence. Review both specification coverage and repository standards.

Every valid finding reopens its slice: adjust coverage, fix it, rerun affected checks, and request re-review. Passing tests do not override a missing criterion.

## Gate 6: User Acceptance

Run `feature-qa`. Complete its automated preflight, obtain approval for the risk-based manual plan, and present one scenario at a time. Only the user may mark a manual scenario `PASS`.

Preserve the durable QA report for resume and audit.

## Status

Use exactly one:

- `VERIFIED` — all six gates pass with no unresolved material risk
- `READY FOR USER QA` — technical proof and review pass; user acceptance remains
- `BLOCKED` — any required gate, review finding, failing scenario, or material unknown remains

If the user waives a gate, work may continue only with the waiver recorded, but the feature must not be labeled `VERIFIED`.

## Final Evidence

```text
Status
<VERIFIED | READY FOR USER QA | BLOCKED>

Approved scope
<requirements and non-goals>

Impact and traceability
<criterion ledger>

Verification
<fresh commands and outcomes>

Independent review
<verdict and resolved findings>

User acceptance
<report path and user-owned results>

Residual risks
<none, or explicit unresolved risks>
```
