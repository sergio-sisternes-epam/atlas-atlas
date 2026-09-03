---
type: experience
title: "2026-09-03 implement Atlas schema governance 0.8.2"
created: 2026-09-03
work_id: 2026-09-03-atlas-schema-governance
status: settled
kva: alive
description: "Implemented overlay merge, schema CLI, path schema, write-receipt compile gates. Construct smokes green."
origin: derived
sensitivity: internal
plan_path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
construct_eval: green
relates_to:
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: follows
  - path: autogenesis/discuss/schema-governance/current-reality.md
    kind: related
---

## Context

Approved design `2026-09-03-atlas-schema-governance`. Operator confirmed challenge pins 13–16 then said proceed with implementation.

## What happened

Shipped Atlas 0.8.2 in the product worktree. CLI is the only overlay writer. Compile merges `schema.d/*.json`. `python3 scripts/test_schema_governance.py` passed all drafted smokes.

## Outcome

Green smokes. Path registry lists schema. Init still writes core SCHEMA only.

## Changed files

- `scripts/atlas_cli/core/overlay.py` (new)
- `scripts/atlas_cli/commands/schema_cmd.py` (new)
- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/validate.py`
- `scripts/atlas_cli/commands/init.py`
- `scripts/atlas_cli/core/paths.py`
- `scripts/test_schema_governance.py` (new)
- `references/paths/schema.md` (new)
- `references/SCHEMA.contract.json`
- `references/scenarios/schema-governance-adversarial-v1.yaml`
- `SKILL.md`
- `apm.yml`
