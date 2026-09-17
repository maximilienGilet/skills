---
name: safe-refactor
description: Use when restructuring, extracting, renaming, moving, or simplifying existing code while preserving behavior, especially across shared code, public interfaces, legacy code, or large blast radii.
---

# Safe Refactor

## Overview

A refactor changes structure without changing observable behavior. Preserve the contract, keep the repository green in reviewable stages, and stop when the work is actually a feature or migration.

**REQUIRED SUB-SKILLS:** Use `impact-check`, `codebase-design`, `verification-before-completion`, and `requesting-code-review`.

## 1. Classify the Work

Choose one before editing:

- `BEHAVIOR-PRESERVING` — same inputs, outputs, errors, side effects, ordering, timing guarantees, data, and public contract
- `MIGRATION` — old and new interfaces or data must coexist
- `BEHAVIOR CHANGE` — any observable contract changes
- `INCONCLUSIVE` — existing behavior is not understood well enough

Only the first two continue under this skill. For `BEHAVIOR CHANGE`, stop and obtain explicit requirements and approval through a feature workflow. Do not hide changed concurrency, ordering, defaults, or errors behind the word “refactor.”

## 2. Establish the Safety Envelope

Run `impact-check`. Record affected callers, interfaces, dynamic references, generated artifacts, data, packages, and external consumers.

Capture the current green baseline. Add characterization tests for behavior the existing suite does not protect, especially side effects, errors, ordering, and legacy quirks. A large untested extraction does not proceed on inspection alone.

If the baseline is already red, separate and document those failures before editing.

## 3. Choose the Smallest Safe Sequence

Prefer stages that are independently reviewable and green:

1. add characterization coverage
2. create or deepen the target seam without switching callers
3. migrate a bounded caller set
4. verify, then repeat
5. remove the obsolete path only after no consumers remain

Use expand-contract for public interfaces, schemas, deployed consumers, or compatibility windows.

An atomic mechanical change is acceptable only when intermediate states cannot compile, the complete blast radius is verified, semantic rename tooling is used where available, and no behavior changes are mixed in.

Do not bundle cleanup, fixes, formatting churn, dependency changes, or speculative abstractions.

## 4. Verify Every Stage

After each stage, run the narrowest relevant tests and diagnostics. At the end, run characterization tests, affected broader suites, type/lint/build checks, downstream package checks, generated-artifact checks, and searches for obsolete references.

Inspect the final diff against the original contract. Obtain independent review of the impact map, stage sequence, and behavior-preservation evidence. Resolve findings and rerun affected checks.

## Stop Conditions

Stop when behavior is ambiguous, characterization is impossible at a truthful seam, a stage requires an unapproved contract change, verification turns red, external consumers are unknown for a breaking change, or the refactor increases coupling without a clear seam.

## Output

```text
Classification
<status and preserved contract>

Safety envelope
<baseline, characterization, impact map>

Stages
<small reversible sequence>

Verification
<fresh commands and outcomes>

Independent review
<verdict and resolved findings>

Residual risks
<remaining unknowns>
```
