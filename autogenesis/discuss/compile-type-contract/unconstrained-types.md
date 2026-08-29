---
type: document
title: "Orbit 2 — types with no templates.by_type block"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin C: every recommended type gets a templates.by_type contract so the graph stays consistent."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-unconstrained-types.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/warning-vs-critical.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Current reality vs alternative: this orbit is current.

Live `types.recommended`: experience, decision, lesson, recipe, work, document, protostar.  
Live `templates.by_type`: experience, decision, work, document only.

Also used in this store and not in `by_type`: `plan`, plus discuss pages typed `document` that carry KVA fields the document template does not require.

**Option C — constrain every recommended type.**  
Add `by_type` blocks for lesson, recipe, protostar (and plan if we add plan to recommended). Layer 2 then warns on those pages. Unknown types outside the list stay OKF-legal with no extra contract.

**Option D — mark the extras unconstrained.**  
SCHEMA says lesson / recipe / protostar / plan are recommended names with no required keys beyond OKF (`type` + title/created if we still want a floor). Layer 2 does not invent a contract.

**Option E — constrain protostar only; leave lesson/recipe/plan unconstrained for now.**  
The failure we just saw is protostar-shaped. Do not grow the gate to types we have not written templates for.

**Pin (operator 2026-08-27): C.**  
Reason given: schema should be consistent to ensure quality graphs. Lesson, recipe, and protostar get `by_type` blocks in the same Stage 1 as the compile gap. Plan stays out until it is added to `types.recommended`.

Not in this orbit: SCHEMA.contract vs live SCHEMA; search-by-type; forming documents that should have been protostars.

## Provenance

Next batch item after pin A on warning-vs-critical.
