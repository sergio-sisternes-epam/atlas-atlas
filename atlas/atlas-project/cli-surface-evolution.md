---
type: document
title: "CLI surface evolution"
created: 2026-08-27
status: alive
kva: alive
work_id: 2026-08-27-atlas-query-harness-hubs
description: "Spine: how the Atlas CLI verbs and flags grew, and what drove each change. Detail stays on the implement experiences."
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: implements
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
  - path: experiences/2026-08-23-construct-adversarial-green.md
    kind: related
  - path: decisions/migrate-cli-lessons-from-autogenesis.md
    kind: related
  - path: experiences/2026-08-27-implement-atlas-compile-type-contract.md
    kind: related
  - path: experiences/2026-08-27-implement-atlas-compile-focus-lenses.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: related
  - path: experiences/2026-08-27-search-self-atlas-cli-evolution-probe.md
    kind: derived_from
---

## Content

Spine only. Read the linked pages for claims.

| When | Surface | Drove it |
|------|---------|----------|
| Phase 1 | Skill + SCHEMA contract; CLI named | Reboot plan after Karpathy / okf-wiki challenge |
| Phase 2 | `validate` / `compile` | First agent-callable gate; staging-empty hard fail |
| Phase 3 | `search` (`grep` pilot, `bm25` flag) | User-directed lexical pilot; BM25 later |
| Phase 4 | `migrate` / `promote` | Old content → staging; promote is scaffold-only |
| Phase 5 | mesh inside `compile` | Composition pin; no extra verb |
| Phase 6 | same verbs, adversarial smokes | Prove the surface |
| Live migrate | lessons, not flags | Directory form, empty staging, agent owns claims |
| 0.7.5 | `init`; `search type:`; `compile --list-type` | Search missed 27 protostars |
| 0.7.6 | drop `--list-type`; `compile --type` / `--path` | List flag short-circuited the gate |

Living split: compile = gate, search = ranked discovery, inventory is not a compile flag.

## Provenance

Assembled from the 2026-08-27 CLI-evolution query probe.
