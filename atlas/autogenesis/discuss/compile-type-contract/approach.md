---
type: document
title: "Approach captured — compile gap then deterministic repair"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Handover node. Resume here. Settled approach plus parked decisions. Not a design packet. Not implement."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/two-stage-fix.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/warning-vs-critical.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/reusable-schema.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/hub.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Resume node for work `2026-08-27-atlas-compile-type-contract`. Discussion paused 2026-08-27 after the operator asked to capture the approach and resume decisions later.

### Problem

`atlas compile` is a file-graph health gate. Forming pages can be contract-wrong and the store still exits 0. The 27 protostars in this Atlas were the proof. Remember-path rules were folklore.

### Approach (settled)

Two stages.

**Stage 1 — fix the root (compile gap).**  
Compile becomes two layers: (1) SCHEMA definitions are valid; (2) pages comply with any type contract that SCHEMA properly defines. Atlas needs a `schema` path (and likely an init writer) so every new store is born with a valid SCHEMA. The atlas skill stays reusable: same CLI, same path, same contract file. No silent rewrite of sibling stores.

**Stage 2 — compile lists; we repair.**  
After Stage 1, compile prints actionable page paths. Humans/agents fix those pages. No search archaeology. Stage 2 is not inside the Stage 1 product change except as acceptance: the gate must list paths.

### Pins already taken

- Layer-2 misses start as **warnings** (`exit 1`). Phase 2 criticals stay critical. Promotion after repair. (`warning-vs-critical.md` — A)
- Origin/sensitivity stay recommended (existing 2026-08-24 decision). Unknown types stay OKF-legal.
- Work-cluster rules (`work_id` → `implements`, protostar → `derived_from`) are enforceable only after they live in SCHEMA.

### Parked — resume decisions here

- C / D / E — constrain all recommended types, mark extras unconstrained, or protostar-only first (`unconstrained-types.md`)
- Init surface — CLI `atlas init`, path-only, or path calls CLI (`leaves/p-init-surface.md`)
- SCHEMA.contract.json vs live SCHEMA.json as Layer-1 authority (`leaves/p-contract-vs-live-schema.md`)
- Section names on protostar — template `Pending` vs discuss `Growth path` (`protostar-contract-sketch.md`)
- Forming `document` pages that should be protostars (`leaves/p-forming-documents.md`)
- Search-by-type vs compile listing (`leaves/p-search-by-type.md`)

### Next legal step when resuming

Stay on `path: discuss` to finish parked calls, then `mode: run`, `path: design` on this `work_id`. Discussion cannot implement.

## Provenance

Operator: “Capture the approach and then we will resume the decision.”
