---
name: feature-qa
description: Use when a large feature needs manual acceptance testing by the user before release, when the user wants to test a feature together, validate a user journey, run UAT, or resume a manual QA campaign.
---

# Feature QA

## Overview

Run a durable, risk-based acceptance campaign where the user operates the product and owns every manual verdict. The agent never self-validates a manual scenario.

## Boundaries

Use `qa` instead when the user only wants to report bugs or file GitHub issues. Create issues only when requested.

## Workflow

1. Inspect the request, plan, branch diff, affected journeys, and run instructions. Ask only for missing scope or environment details.
2. Run the repository's relevant build, typecheck, automated tests, and diagnostics. Resolve failures before manual testing. Use `systematic-debugging` and `test-driven-development` for code fixes.
3. Propose a concise plan ordered by risk. Cover smoke, primary journey, errors, permissions, boundaries, and regressions. Include responsive or accessibility checks only when relevant. Have the user approve or adjust the plan.
4. Create `tasks/qa/YYYY-MM-DD-<feature>.md` as the source of truth. Record scope, environment, preflight evidence, scenarios, defects, retests, and verdict.
5. Present exactly one scenario at a time using the contract below. After the user's reply, update the report before presenting the next scenario.
6. Finish with `READY`, `READY WITH RISKS`, or `BLOCKED`, supported by recorded results.

When resuming, read the report first, summarize its current state, confirm that the environment is still valid, and continue from the first unresolved scenario. Never reconstruct missing results from memory.

## Scenario Contract

```text
Test <n>/<total> — <behavior>

Precondition
<required state>

Actions
1. <user action>

Expected
<observable outcome>

Reply: PASS, FAIL, or BLOCKED, with any observation.
```

Only the user's explicit result can set a manual test to `PASS`. Ambiguous feedback stays unresolved until clarified. Automated evidence cannot substitute for user confirmation.

## Failure Handling

Classify each `FAIL` or `BLOCKED` before acting:

- **Campaign blocker:** prevents remaining critical scenarios or invalidates the environment. Pause, diagnose, fix, run relevant automated checks, then ask the user to repeat the same scenario.
- **Non-blocker:** record the observed and expected behavior, queue the defect, and continue. Repair after the planned campaign unless the user changes priority.

A repair never changes a manual result to `PASS`. Record it as awaiting retest. Add regression scenarios when a repair may affect earlier behavior.

## Verdict Rules

| Verdict | Condition |
|---|---|
| `READY` | All critical scenarios explicitly passed and no unresolved failures remain. |
| `READY WITH RISKS` | Critical scenarios passed and the user explicitly accepts documented non-critical risks. |
| `BLOCKED` | A critical scenario failed, remains blocked, or was not tested. |

## Common Mistakes

- Giving the whole checklist at once instead of guiding one scenario.
- Starting manual testing before green preflight.
- Treating a code fix or automated test as manual acceptance.
- Repairing every non-blocking defect immediately and losing campaign continuity.
- Keeping results only in chat or guessing after compaction.
