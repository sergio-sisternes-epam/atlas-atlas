---
type: document
title: "Q6 — what does compile --type print?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin B: focused compile prints issues and the matching path list. JSON has critical/warnings and pages."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-list-type-alias.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/q-path-lens.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

`atlas compile --type protostar` is a focused gate. What is stdout?

**A — Gate output only.** Same shape as compile today: criticals, warnings, ok/fail line. Add a one-line scope note (`type=protostar pages=N`). Do not print every matching path. `--json` adds `"type"` and `"page_count"`; issues stay the payload.

**B — Gate plus path list.** Issues as today, and also print every matching path (the 0.7.5 dump). `--json` includes both `critical`/`warnings` and `pages`.

A keeps compile looking like compile. B keeps the repair-loop listing that created the opportunistic flag.

## Answer (operator 2026-08-27)

**B.** Same for any focus lens (`--type`, `--path`, or both once stacked).
