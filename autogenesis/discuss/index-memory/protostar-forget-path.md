---
type: protostar
title: "Protostar — forget path for index.md STM"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: open
kva: forming
reality: current
growth: true
star_kind: refine
description: "Parked: how STM entries leave the working set without access-count telemetry."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/discuss/index-memory/requirements.md
    kind: related
---

## Growth path

Design forget only after the STM artefact and two-layer query are pinned. Do not invent access telemetry in the core algorithm. Recency, explicit pin/unpin, compile-driven caps, or a second eviction list are candidates when this star is opened.

## Open question

Without reliable access counts, what signal is allowed to drop a page from STM while leaving the file in the store?

## Origin

Hub conversation 2026-09-18. The user asked to discuss forget later and to keep this orbit on organisation plus query.
