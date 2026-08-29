---
type: document
title: "Q2 — does --list-type scope the gate or replace it?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin A: --list-type scopes the compile gate to that type. Shipped B (list and exit 0) is a miss against intent."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-gate-vs-list.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-list-swallows-gate.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/q-scope-still-runs-store.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

When you run `atlas compile --list-type protostar`, which of these is the intended machine behaviour?

**A — Scope the gate.** Still run SCHEMA + staging + page-contract, but only emit issues for pages whose `type` matches. Exit 0/1/2 from that slice. Listing matching paths may appear as extra output, but it does not replace the gate.

**B — Inventory dump (what 0.7.5 shipped).** Print matching paths (and titles). Do not report warnings/criticals. Always exit 0 if the list ran.

The approved plan wrote B. Your last turn described A.

## Answer (operator 2026-08-27)

**A.**
