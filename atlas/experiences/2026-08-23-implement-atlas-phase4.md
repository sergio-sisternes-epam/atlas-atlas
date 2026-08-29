---
type: experience
title: "2026-08-23 implement Phase 4: atlas migrate + promote"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Phase 4 — migrate copies into staging only; promote scaffolds from template and clears staging; compile fails on thin scaffolds until agent writes claims."
tags: "[memory, implement, atlas, migrate, promote, work_id]"
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
  - path: experiences/2026-08-23-implement-atlas-phase3.md
    kind: follows
---
# 2026-08-23 implement Phase 4: migrate + promote

## Context

Migration pin required an explicit path for external/old content into staging, and a optional promote helper that only scaffolds.

## What was implemented

### Changed files

- `atlas/scripts/atlas_cli/commands/migrate.py`
- `atlas/scripts/atlas_cli/commands/promote.py`
- `atlas/scripts/atlas_cli/cli.py` — wired `migrate` and `promote`
- `atlas/scripts/atlas_cli/core/frontmatter.py` — strip HTML comments in not-just-links heuristic
- `atlas/SKILL.md` — v0.4.0-phase4
- Fixture gained `decisions/mesh-access.md` as a completed example from the smoke path

### Behaviour

```text
atlas migrate <source> [--into staging/]
  → copy into staging + provenance sidecar
  → atlas compile FAILS (staging non-empty)

atlas promote <staging-file> --to <target> [--type decision]
  → template skeleton, index stub, remove staging file
  → prints agent checklist
  → atlas compile FAILS while body is thin (not_just_links)

agent writes claims + links
  → atlas compile GREEN
```

### Smokes

| Step | Result |
|------|--------|
| migrate rough file | staging has file; compile exit 2 |
| promote to decisions/… | scaffold + checklist; staging cleared |
| thin scaffold | compile exit 2 `not_just_links` |
| agent-completed page | compile exit 0 |

## Deferred

- BM25 engine, mesh consolidate, construct eval, live okf-wiki store migration


## Exit criterion: Click migration (same session)

- `atlas_cli/cli.py` rewired from argparse to **Click** (microsoft/apm-aligned).
- `commands/` and `core/` unchanged (`run()` contract preserved).
- Regression: validate, search, migrate, promote help + fixture compile green.

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **implements:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **follows:** [2026-08-23-implement-atlas-phase3](2026-08-23-implement-atlas-phase3.md)
