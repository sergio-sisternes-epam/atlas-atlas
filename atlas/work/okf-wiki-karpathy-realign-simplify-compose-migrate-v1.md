---
type: work
title: "Atlas reboot of okf-wiki"
created: 2026-08-23
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
status: done
description: "Design and implement Atlas as the operational successor to okf-wiki — structure, compile, search, migrate/promote, mesh, relations, opening-test store."
relates_to:
  - path: experiences/2026-08-23-okf-wiki-design-challenge-karpathy-realign.md
    kind: related
  - path: experiences/2026-08-23-atlas-design-plan.md
    kind: related
  - path: experiences/2026-08-23-atlas-name-pin.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase1.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase3.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase4.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase5.md
    kind: related
  - path: experiences/2026-08-23-implement-atlas-phase6.md
    kind: related
  - path: experiences/2026-08-23-construct-adversarial-green.md
    kind: related
  - path: experiences/2026-08-23-cartograph-atlas-port.md
    kind: related
  - path: decisions/cartograph-fork-in-atlas.md
    kind: related
  - path: decisions/atlas-name.md
    kind: related
  - path: decisions/type-vocabulary.md
    kind: related
---

## Scope

Reboot the okf-wiki operational layer as **Atlas**: OKF v0.2-aligned knowledge substrate with schema-driven free layout, staging, lean CLI (validate/compile/search/migrate/promote), mesh consolidate, frontmatter-authoritative relations, and skill process memory under `references/atlas/`.

## Status

Implementing — CLI and opening-test Atlas are green. Deferred: full BM25 index, live okf-wiki store migration.

## Outcomes

- Atlas skill + Click CLI
- Opening-test store at `references/atlas/` with experiences, decisions, and this work hub
- Relation vocabulary (`relates_to` / `kind`) and recommended types including `work`
- Construct adversarial report green (2 deferred out of scope)
- Cartograph forked into `addons/cartograph/` (Build-only sky; skill is the only Atlas viewer source)

## Related

See `relates_to` frontmatter (authoritative).
