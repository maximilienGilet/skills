---
name: verified-fix
description: Use when fixing a bug end to end with regression protection and independent review, when the user asks for a verified fix, or when a defect affects shared, critical, payment, security, or data-integrity behavior.
---

# Verified Fix

## Overview

A fix is verified only when the exact symptom is reproduced, protected by a regression gate, eliminated by the smallest root-cause correction, and accepted by an independent review. Passing code is not enough; preserve the evidence chain.

**REQUIRED SUB-SKILLS:** Use `diagnosing-bugs`, `test-driven-development`, `verification-before-completion`, `requesting-code-review`, and `receiving-code-review`.

## Evidence Chain

1. **Define the defect.** Record the observed behavior, expected behavior, affected scope, and one explicit completion criterion.
2. **Diagnose.** Build a tight reproduction, watch it fail, trace the root cause, and compare similar working paths. Do not patch a symptom.
3. **Lock the regression.** Add the smallest test at the seam that reproduces the real bug. Run it and confirm the expected failure before editing production code. If no truthful automated seam exists, document why and retain the runnable reproduction as the gate; never add a shallow test for appearances.
4. **Fix minimally.** Change only what the confirmed root cause requires. Exclude cleanup and speculative hardening.
5. **Verify freshly.** Run the regression test, the original reproduction, relevant broader tests, type/build checks, and diagnostics. Inspect the final diff for accidental scope.
6. **Review independently.** Give a fresh reviewer the defect, root cause, requirements, diff, and verification evidence. Do not provide the implementation narrative as proof.
7. **Close the loop.** For every valid finding, update the regression coverage when needed, fix it, rerun all affected verification, and have the reviewer re-check the changed area.
8. **Report evidence.** State root cause, changed files, red-green proof, commands and outcomes, review verdict, and residual risks.

## Non-Negotiable Rules

- The user may waive this workflow, but then the result is not a `verified-fix` and must not be reported as one.
- A request to skip tests or independent review does not satisfy this skill.
- Never claim success from an agent report, an old test run, or targeted tests alone when shared callers can be affected.
- Stop when the symptom cannot be reproduced, verification remains red, review has an unresolved blocker, or three attempted fixes failed.

## Completion Contract

```text
Root cause
<confirmed cause and evidence>

Fix
<minimal change>

Verification
<fresh commands and outcomes, including red-green proof>

Independent review
<verdict and resolved findings>

Residual risks
<none, or explicit risks>
```

## Common Mistakes

- Accepting “obvious one-line fix” as diagnosis.
- Writing a test after the fix and calling it regression proof.
- Letting the author’s diff inspection replace independent review.
- Fixing a reviewer finding without rerunning affected checks.
- Calling a partial or waived process verified.
