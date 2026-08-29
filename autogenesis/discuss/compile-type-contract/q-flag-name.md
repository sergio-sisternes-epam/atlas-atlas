---
type: document
title: "Q4 — keep --list-type or rename the focus flag?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin A: canonical flag is --type. Not --only-type. --list-type is the old name; alias vs cut is Q5."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-scope-still-runs-store.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/q-list-type-alias.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

The flag is called `--list-type`. Pins now say it does not list; it focuses the page walk of compile.

**A — Rename.** Something that means focus, e.g. `--type` or `--only-type`. `--list-type` becomes a short-lived alias or dies.

**B — Keep `--list-type`.** Name stays; behaviour changes to the scoped gate. Agents relearn the flag in place.

A drops the opportunistic word. B is less churn.

## Answer (operator 2026-08-27)

**A — `--type`.**

