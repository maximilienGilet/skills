---
name: impact-check
description: Use before approving or implementing a risky change, when asked for impact analysis or blast radius, or when shared code, contracts, schemas, packages, configuration, or deployment behavior may affect unknown consumers.
---

# Impact Check

## Overview

Map what a proposed or current change can break before judging it safe. This is read-only unless the user separately asks for implementation.

Do not equate a text search, local tests, or a clean build with complete impact coverage.

## Workflow

### 1. Define the changed contract

State exactly what can change for consumers:

- types, inputs, outputs, errors, side effects, defaults, ordering, or timing
- persisted data, schemas, migrations, generated artifacts, or wire formats
- configuration, permissions, runtime dependencies, rollout, or rollback behavior

Use the request, current diff, or changed symbol as the boundary. If that boundary is unclear, mark the result `INCONCLUSIVE` rather than guessing.

### 2. Trace outward

Inspect the definition and then traverse:

1. direct callers, references, imports, tests, and fixtures
2. aliases, wrappers, re-exports, dependency injection, registries, and generated code
3. downstream packages, services, builds, scripts, jobs, dashboards, and deployment paths
4. dynamic or external consumers that the repository cannot prove

Prefer semantic references and dependency metadata over grep alone. Read representative callers to identify implicit dependencies on behavior, not only names.

### 3. Build the evidence ledger

Label every material claim:

- **Verified:** confirmed by inspected code or a fresh command
- **Inferred:** supported by repository patterns but not directly proven
- **Unknown:** outside visibility or not yet checked

Include concrete paths, symbols, and command outcomes. Never silently convert an unknown into “no impact.”

### 4. Rank risks

Classify each affected area as `HIGH`, `MEDIUM`, or `LOW` using consequence, reach, reversibility, and available detection. Security, payments, data loss, public contracts, irreversible migrations, and unknown external consumers default to `HIGH` until reduced by evidence.

For incompatible contracts or persistent data, assess staged rollout and rollback. Prefer expand-contract when old and new consumers can overlap.

### 5. Define the validation boundary

Name the smallest checks that prove each identified consumer remains valid: targeted tests, downstream typechecks/builds, contract tests, migration rehearsal, production-like data checks, observability, and rollback rehearsal.

Do not run destructive, production, or costly checks without explicit approval.

## Verdict

Use exactly one:

- `SAFE` — all material consumers are verified and checks pass
- `SAFE WITH CONDITIONS` — bounded risks remain with explicit gates
- `NOT SAFE` — a confirmed breakage or unresolved high risk exists
- `INCONCLUSIVE` — visibility or evidence is insufficient

## Output

```text
Verdict
<status and one-sentence rationale>

Changed contract
<what consumers can observe>

Impact map
<direct, transitive, operational, external>

Risk register
<severity, evidence label, affected area, reason>

Required validation
<commands, rollout gates, rollback checks>

Unknowns
<what this repository cannot prove>
```
