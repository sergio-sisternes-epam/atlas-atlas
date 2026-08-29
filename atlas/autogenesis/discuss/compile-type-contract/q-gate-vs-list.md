---
type: document
title: "Q1 — compile stays a gate; list is a separate verb?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Operator rejected a separate list verb. compile --list-type is meant to focus the gate on a type as the graph grows. search is the GPS navigator (grep + nav rules), not inventory."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-list-verb.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/q-list-type-scopes-gate.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

Does the operator accept: compile = gate with no inventory flags; inventory = its own verb; search = ranked discovery?

## Answer (operator 2026-08-27)

**No** to a separate list verb as the missing piece.

- `--list-type` is a **focus flag for compile**: when the graph grows, validate a type slice rather than the whole store.
- **Search** is the agent navigator. Deterministic GPS to files for grounding. Default engine is grep, plus the nav rules (read hits, expand links, never staging).

## Distinction this answer creates

The 0.7.5 plan text said `--list-type` prints matching paths and exits 0 if the listing ran. Shipped code does that and skips the gate.

The operator’s meaning is scoped **validation**, not an inventory dump. That is the next question. Not settled here.
