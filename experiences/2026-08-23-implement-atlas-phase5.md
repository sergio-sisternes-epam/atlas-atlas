---
type: experience
title: "2026-08-23 implement Phase 5: mesh consolidate in compile"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Phase 5 — partial mesh fragments merged by id inside atlas compile; conflict hard-fail; mesh.json written."
tags: "[memory, implement, atlas, mesh, work_id]"
origin: internal
sensitivity: internal
implements: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
plan_path: /home/workdir/artifacts/autogenesis-plans/2026-08-23-atlas-reboot-okf-wiki-v1.md
construct_eval: deferred
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: experiences/2026-08-23-atlas-design-plan.md
    kind: implements
  - path: experiences/2026-08-23-implement-atlas-phase4.md
    kind: follows
---
# 2026-08-23 implement Phase 5: mesh consolidate

## Context

Composition pin required mesh consolidation as a clear step inside atlas compile/validate.

## What was implemented

### Changed files

- `atlas/scripts/atlas_cli/core/mesh.py` — discover fragments, validate entries, merge by id, write mesh.json
- `atlas/scripts/atlas_cli/commands/validate.py` — mesh step before staging checks
- Fixture: `fixtures/mini-atlas/mesh/fragments/*.json`
- `atlas/SKILL.md` — v0.5.0-phase5

### Behaviour

- Fragments: `mesh/fragments/*.json`, `*.mesh.fragment.json`, `mesh.fragment.json`, …
- Required entry fields: `id`, `root`, `access` (`read` | `read/write`)
- Optional: `contribution.type`, `contribution.repository`
- Same `id` with differing `root` or `access` → **mesh_conflict** critical (exit 2)
- Success → writes `mesh.json` at Atlas root

### Smokes

| Case | Result |
|------|--------|
| Two compatible fragments | exit 0, mesh.json with 2 atlases |
| Conflicting root/access | exit 2, mesh_conflict |
| No fragments | exit 0, mesh step skipped |

## Deferred

- BM25 engine, construct adversarial suite, live okf-wiki migration

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **implements:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **follows:** [2026-08-23-implement-atlas-phase4](2026-08-23-implement-atlas-phase4.md)
