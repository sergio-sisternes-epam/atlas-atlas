---
type: protostar
title: "Query engine KPIs live in the Atlas skill"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "Leaf pointing at Atlas skill paths query and configure: grep until opt-in; atlas:ranked after fast path; tgrep not a latency play."
relates_to:
  - path: lessons/2026-09-09-opt-in-ranked-after-fast-path.md
    kind: derived_from
  - path: experiences/2026-09-09-smr-fast-path-product-bench.md
    kind: derived_from
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: related
  - path: experiences/2026-09-09-smr-kpi-bench.md
    kind: related
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
---

## Skill pointer

Keep this recommendation in the Atlas skill package, not only in this store:

- Path **query** — `references/paths/query.md` (discovery; engine choice before `atlas search`)
- Path **configure** — `references/paths/configure.md` (when to enable recall profiles)
- Router — `SKILL.md` search-engine line

Do not treat this leaf as implement authority for a new driver. It tracks skill copy that must stay aligned with lesson [opt-in ranked](../../../lessons/2026-09-09-opt-in-ranked-after-fast-path.md).

## Pending

Product ranked fast path re-bench is done. Keep skill copy aligned: grep until
opt-in; `atlas:ranked` for speed and follow-up tokens; do not claim tgrep
acceleration (see `p-tgrep-serve-and-subset-rank`).
