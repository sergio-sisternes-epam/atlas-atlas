---
type: protostar
title: "compile --list-type returns 0 and skips the gate"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: open
kva: forming
growth: true
star_kind: probe
origin: derived
sensitivity: internal
description: "validate.run short-circuits on list_type: print hits, return 0. Warnings and criticals are discarded. Listing is not compile."
relates_to:
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Pending

Treat `--list-type` on compile as a defect, not a feature to grow. Either remove it after a real `list` verb exists, or if it stays as a compatibility shim, it must not change exit-code meaning of compile (still run the gate; listing is extra stdout). Current code cannot be both a gate and an inventory.

## Origin

Review of shipped 0.7.5 `commands/validate.py` after the operator challenged opportunistic CLI evolution.
