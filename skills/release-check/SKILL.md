---
name: release-check
description: Use before deploying, publishing, tagging, or announcing a release to determine whether the exact release candidate is ready, conditionally ready, or blocked.
---

# Release Check

## Overview

Produce an evidence-based go/no-go verdict for one exact release candidate. This workflow does not deploy, tag, publish, push, or approve on the user’s behalf.

**REQUIRED SUB-SKILLS:** Use `impact-check`, `verification-before-completion`, and `feature-qa` for material customer-facing changes.

## 1. Pin the Candidate

Record the source commit, comparison base or previous release, target environment, version, artifact identity/checksum, and build provenance.

The artifact and all evidence must refer to the same source state. A dirty working-tree build, mismatched CI commit, or unknown artifact is immediately `BLOCKED` until rebuilt from approved source.

## 2. Inventory Release Risk

Inspect the complete release diff and classify:

- behavior and public-contract changes
- database migrations and persistent data
- dependencies, lockfiles, generated artifacts, and supply-chain inputs
- configuration, secrets presence, permissions, flags, and infrastructure
- compatibility, rollout order, external consumers, and rollback constraints
- user-visible workflows, known issues, and support impact

Never display secret values. Use `impact-check` for material or uncertain blast radius.

## 3. Verify Required Gates

Use fresh evidence from the exact candidate:

- repository-required tests, lint, type checks, builds, and CI checks
- artifact installation/startup and production-like smoke tests
- security, dependency, contract, compatibility, or performance checks required by the project
- migration rehearsal, data-integrity checks, backup restore, and rollback rehearsal where data changes
- rollout plan, owners, observability, alerts, abort thresholds, and recovery runbook
- versioning, changelog, release notes, and documentation required by repository policy

For a material customer-facing feature, run `feature-qa`. Only the user can mark its manual scenarios `PASS`; green automation cannot substitute for acceptance.

Missing irrelevant gates may be marked `N/A` with a reason. Missing required evidence is not a pass.

## 4. Reconcile Risks

List every known issue with severity, affected users, mitigation, owner, rollback trigger, and explicit acceptance status.

A destructive or irreversible migration without rehearsed recovery, an unresolved security/data-integrity risk, red required CI, failed acceptance, unknown artifact provenance, or unverified rollback is blocking.

## Verdict

Use exactly one:

- `READY` — every required gate passes for the exact candidate and no unresolved material risk remains
- `READY WITH RISKS` — only non-blocking risks remain, each explicitly accepted with mitigation and rollback
- `BLOCKED` — any required gate, approval, provenance, recovery path, or material risk is unresolved

## Output

```text
Verdict
<READY | READY WITH RISKS | BLOCKED and rationale>

Candidate
<commit, version, artifact, target>

Change inventory
<material release risks>

Gate evidence
<required gate, command/artifact, outcome>

Accepted risks
<owner, mitigation, rollback trigger>

Blockers
<owner and evidence needed>

Release and rollback
<ordered plan, observability, abort criteria>
```
