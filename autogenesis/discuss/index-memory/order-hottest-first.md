---
type: document
title: "1-by-1 — hottest at top, drop from the bottom"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: settled
kva: alive
reality: current
description: "STM order means frequency. Top is hottest. Forget later drops the bottom. Encoding without counts is the next pin."
tags: [index-md, order, stm]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: autogenesis/discuss/index-memory/compile-incomplete.md
    kind: follows
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
  - path: autogenesis/discuss/index-memory/protostar-forget-path.md
    kind: related
---

## Context

Hub batch item on order. The opening talk named both “frequent at the top” and “top eventually drops”. Those need two different lists. The human chose one list: hottest at the top.

## Decision

Order in each folder `index.md` means how hot the memory is. Hottest is at the top. Forget, when opened, drops from the bottom. The “top-drop” claim is not current reality.

## Gap

We still have no access-count telemetry. A frequency *meaning* without a *signal* cannot be implemented as a counter. The next pin is the signal: recency proxy, promote-on-query, or wait for forget.

## Outcome

P6 is alive as hottest-first / bottom-drop. Encoding is the live 1-by-1.
