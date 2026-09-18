---
type: document
title: "1-by-1 — compile allows incomplete STM indexes"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: settled
kva: alive
reality: current
description: "Keep index.md present. Do not require complete child listings. Fail on dangling STM links."
tags: [index-md, compile, stm]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: autogenesis/discuss/index-memory/layer-2-incomplete.md
    kind: follows
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
---

## Context

Follows the layer-2 pin. Incomplete working sets are illegal under today’s named `index_md_listing` completeness contract.

## Decision

Compile keeps `index_md_present`: a folder with concept pages still has `index.md`, including at store root.

Compile drops completeness: a missing child line is legal LTM, not a failure.

Compile still fails if an STM index links a path that does not exist.

`index_md_listing` in SCHEMA must be redefined or removed in the implement slice so it does not mean “all children named”.

## Outcome

P9 is alive. Next 1-by-1 is listing order, now that the list may be a subset.
