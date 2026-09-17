---
name: ci-repair
description: Use when a CI job, build pipeline, test matrix, or automated check is failing or flaky and the user wants the cause diagnosed and repaired without weakening the gate.
---

# CI Repair

## Overview

Restore the original CI guarantee, not merely a green badge. Find the earliest causal failure, reproduce it as closely as possible, and preserve coverage.

**REQUIRED SUB-SKILLS:** Use `diagnosing-bugs` for investigation. If repository code, tests, or workflow configuration must change, finish through `verified-fix`.

## Workflow

### 1. Capture the failing unit

Record the commit, workflow, job, matrix cell, attempt, runner image, relevant tool versions, exact command, first causal error, and later cascade failures. Redact secrets.

Ignore downstream cancellations and secondary errors until the first failure is understood.

### 2. Classify before editing

Choose one primary class and cite evidence:

- product regression
- test defect
- nondeterministic product/test behavior
- environment or platform mismatch
- dependency/cache/artifact failure
- runner capacity or external infrastructure incident
- inconclusive

A timeout, retry success, or local pass is evidence, not a root cause.

### 3. Build a CI-faithful reproduction

Re-run the exact failing command with matching lockfile, environment, working directory, architecture, runtime, and matrix values where practical. Compare a passing cell or previous green commit to isolate the variable.

For intermittent failures, loop the smallest trigger until the failure rate is measurable. Do not diagnose a flake from one red and one green run.

If reproduction requires unavailable secrets or hosted infrastructure, use redacted logs and the narrowest rerun that preserves the original conditions; state the visibility limit.

### 4. Repair the cause

Apply the smallest class-appropriate correction.

- Keep supported matrix cells and required checks enabled.
- Do not weaken assertions, add `allow_failure`, skip tests, regenerate lockfiles, or widen global timeouts to hide a failure.
- Add retries only at a proven transient external boundary, using bounded backoff and preserved final failure. Never retry an entire test or job to conceal nondeterminism.
- Change a timeout only after measuring a valid bounded operation and documenting why the previous limit was wrong.

### 5. Prove the gate

Run the minimal reproducer, exact CI command, affected broader checks, and all affected matrix cells. For flakes, run enough repetitions to demonstrate the failure-rate change. Then obtain a fresh CI result for the same commit when the harness permits it.

Do not claim repaired while the exact required gate remains red, skipped, cancelled, or unobserved.

## Output

```text
Classification
<class and causal evidence>

Root cause
<earliest confirmed cause>

Repair
<minimal change without reduced coverage>

Verification
<local/CI commands, matrix cells, repetitions, outcomes>

Gate status
<PASSING | BLOCKED | INCONCLUSIVE>

Residual risks
<remaining environmental or flaky risk>
```

## Stop Conditions

Stop and report `BLOCKED` or `INCONCLUSIVE` when required logs are missing, the failure cannot be reproduced or distinguished from infrastructure, secrets are unavailable, or a required CI cell cannot be rerun. Do not manufacture green evidence.
