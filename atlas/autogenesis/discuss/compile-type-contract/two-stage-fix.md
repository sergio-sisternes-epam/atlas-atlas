---
type: document
title: "Pin — two-stage fix: close the compile gap, then repair what it lists"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Operator restatement of the work. Stage 1 is the gate. Stage 2 is deterministic repair against compile output."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/fixes-initial-problem.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/warning-vs-critical.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

**Stage 1 — fix the root problem (the compile gap).**  
Make compile a two-layer gate: SCHEMA definitions valid; pages checked against properly defined type contracts. Schema path / init so every new Atlas is born with that gate. Product work is the skill + CLI + SCHEMA, not editing 27 pages by hand.

**Stage 2 — compile surfaces problems deterministically; we fix them.**  
After Stage 1 ships, `atlas compile --root` lists Layer-2 misses (warnings first, pin A). Repair is a separate pass against that list (implements edges, sections, type hygiene). No archaeology. No search-as-inventory.

Stage 2 is not in the Stage 1 design packet except as acceptance: the gate must print actionable paths. Promotion of named warnings to critical happens after Stage 2 on this store, not before.

## Provenance

Operator: “This is a two stage fix: we fix the root problem. The compile gap. Compile will surface problems deterministically and we fix them.”
