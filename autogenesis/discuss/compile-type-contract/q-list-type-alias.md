---
type: document
title: "Q5 — does --list-type remain as an alias?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin A: hard cut. --list-type is removed when --type lands. No alias."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-flag-name.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/q-type-stdout.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

Canonical flag is `compile --type <name>` (and the same on `validate`).

**A — Hard cut.** Remove `--list-type` in the same change that adds `--type`. 0.7.5 scripts break; the opportunistic name is gone.

**B — Alias, same behaviour.** `--list-type` keeps working as `--type`. Help text marks it hidden or deprecated. Remove later only if something forces it.

Same machine meaning either way. A is cleaner. B is kinder to anything already calling 0.7.5.

## Answer (operator 2026-08-27)

**A — Hard cut.**
