---
type: document
title: "Orbit 1 — Layer-2 misses: warning then critical, or critical now?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin: new Layer-2 misses start as warnings (exit 1). Phase 2 criticals stay critical. Promotion after repair is part of the pin."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-warning-then-critical.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Current reality vs alternative: this orbit is current. Other batch items stay parked.

**Option A — warnings first.**  
New Layer-2 misses (missing required key, missing required section, `work_id` without `implements`) emit `exit 1`. Existing Phase 2 criticals stay critical: no SCHEMA, non-empty staging, missing type, thin body, broken path. After a repair pass on this store, named rules promote to critical.

**Option B — critical from day one.**  
Same new rules are `exit 2` immediately. This Atlas goes red until the 27 protostars and any other miss are repaired or waived page-by-page.

**Pin (operator 2026-08-27): A.**

A that never promotes is a dead gate. Which named rules promote, and after what repair evidence, is design-time — not reopened as “critical from day one.”

Not in this orbit: which types get a `by_type` block; SCHEMA.contract vs live SCHEMA; search-by-type.

## Provenance

Operator: “One question at a time.” Then “A.”
