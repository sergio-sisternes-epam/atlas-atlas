---
type: document
title: "Discussion root — Atlas compile schema and page contracts"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "discussion_root. Subject and objective locked. Does not move."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
  - path: autogenesis/discuss/compile-type-contract/current-reality.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/warning-vs-critical.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/unconstrained-types.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/reusable-schema.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/two-stage-fix.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/approach.md
    kind: follows
---

## Content

Subject: Atlas compile as a schema-aware gate.

Objective: decide whether `atlas compile` must (1) validate that SCHEMA definitions are valid and (2) validate that pages comply with any schemas that are properly defined — on top of the type-contract slices already recommended.

This page is `discussion_root`. It does not move.

## What happened

A query of the Atlas store showed 27 protostars all compile-green while missing work-hub `implements` edges, origin `derived_from` edges, and template sections. Compile was then traced: it is a file-graph health gate. Phase 2 deferred section-level template enforcement. Protostar was named in `types.recommended` but not wired into `templates.by_type`. Remember-path prose carries the real contract.

The operator asked Autogenesis to formalise that discussion, and added two questions: should compile validate schema definitions, and should pages be compliant with any schemas properly defined.

## Batch on the hub

Engaged this turn:

1. Diagnosis — compile is graph-health, not type-contract — `current-reality.md`
2. Prior recommended slices — `prior-slices.md`
3. Two-layer gate (operator questions) — `two-layer-gate.md`
4. Warning vs critical (1-by-1) — `warning-vs-critical.md` — **settled: A**
5. Unconstrained types (1-by-1) — `unconstrained-types.md` — C/D/E still open
6. Reusable schema + schema path — `reusable-schema.md`
7. Two-stage fix — `two-stage-fix.md` — settled
8. Approach captured (pause) — `approach.md` (**current_branch**, settled)

Unengaged / parked as protostars under `leaves/`:

- SCHEMA.contract vs live SCHEMA as authority
- Search cannot list by type
- Forming documents wearing the wrong type
- Repair-before-red on this store

## Provenance

Distilled from the 2026-08-27 conversation. Not a transcript.
