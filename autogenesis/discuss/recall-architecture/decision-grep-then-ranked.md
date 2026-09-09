---
type: decision
title: "Grep stays the basic default; atlas:ranked is the opt-in default"
created: 2026-09-09
status: settled
kva: alive
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "SCHEMA 1.0 and recall.enabled=false keep grep. The next configuration after opt-in is atlas:ranked, not scan or tgrep."
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: lessons/2026-09-09-smr-fast-path-published-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
---

## Decision

1. **Basic:** grep. Do not enable recall by default. `atlas search` without a profile on a store that has not opted in stays the grep engine.
2. **Next configuration:** `atlas recall activate` defaults to `atlas:ranked`. An enabled store with no preset resolves to `atlas:ranked`, not `atlas:scan`.
3. **Latest / advanced:** `atlas:tgrep` remains a named profile. Owners must pass `--profile atlas:tgrep`. Limited benefits until the tgrep protostar lands.
