---
type: document
title: "How the two-layer gate fixes the original protostar miss"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Trace from the 27-star quality inventory to what compile + schema path would change. Not implement."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/reusable-schema.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/warning-vs-critical.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Original symptom: `atlas compile` exit 0 on this store while 27 `type: protostar` pages missed work-hub `implements`, origin `derived_from`, and template sections. Search could not list them by type. Forming product work (git-mesh) was typed `document` with `kva: forming`.

What changes if the discussed gate exists:

1. Protostar is a properly defined schema (`templates.by_type.protostar` plus work-cluster rules in SCHEMA, not remember-path only).
2. Layer 2 walks pages of that type and emits warnings (pin A) for missing required section / missing `implements`.
3. `atlas search` remaining blind does not matter for the gate — compile lists the misses. A schema path / validate listing is how an agent *finds* them without grep folklore.
4. New Atlas roots get the same SCHEMA at birth, so the next skill store cannot repeat “type exists in the recommended list, contract lives only in this one store’s markdown template.”

What this does **not** fix by itself: landscape promote/terminate calls; answering git-mesh auth precedence; auto-rewriting 27 pages. Repair is a follow-on pass against the new warnings.

## Provenance

Operator: “How this solution will fix our initial problem?”
