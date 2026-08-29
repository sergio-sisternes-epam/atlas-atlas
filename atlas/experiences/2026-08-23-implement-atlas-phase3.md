---
type: experience
title: "2026-08-23 implement Phase 3: atlas search (grep pilot + bm25 flag)"
created: 2026-08-23
status: raw
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "Phase 3 — atlas search with SCHEMA query.search_engine grep|bm25; pilot default grep; agentic guidance; bm25 falls back with WARNING."
tags: "[memory, implement, atlas, search, work_id]"
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
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: follows
---
# 2026-08-23 implement Phase 3: atlas search

## Context

User directed Phase 3 with a pilot change: grep search is approved under configuration; BM25 later. When mode is grep, CLI must instruct standard agentic search patterns.

## What was implemented

### Changed files

- `atlas/scripts/atlas_cli/commands/search.py` — ranked grep search + bm25 stub/fallback + agentic guidance
- `atlas/scripts/atlas_cli/cli.py` — `search` subcommand (`--engine`, `--limit`, `--json`)
- `atlas/fixtures/mini-atlas/SCHEMA.json` — `query.search_engine: grep`
- `atlas/references/SCHEMA.contract.json` — pilot default grep
- `atlas/SKILL.md` — v0.3.0-phase3, search contract updated

### Behaviour

| Config | CLI behaviour |
|--------|----------------|
| `search_engine: grep` (default) | Ranked full-text over concept pages; prints agentic guidance |
| `search_engine: bm25` or `--engine bm25` | If no index/engine → WARNING + grep fallback + guidance |
| Agent unbounded tree grep | Still forbidden; use `atlas search` |

### Smokes

- `atlas search "Atlas naming"` → ranked hits including decisions/naming.md
- `--engine bm25` without index → WARNING + grep fallback
- `--json` includes `agentic_guidance` when engine_used is grep

## Deferred

- Real BM25 index build / query
- migrate, promote, mesh consolidate
- construct adversarial run

## Related

- **implements:** [okf-wiki-karpathy-realign-simplify-compose-migrate-v1](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **implements:** [2026-08-23-atlas-design-plan](2026-08-23-atlas-design-plan.md)
- **follows:** [2026-08-23-implement-atlas-phase2](2026-08-23-implement-atlas-phase2.md)
