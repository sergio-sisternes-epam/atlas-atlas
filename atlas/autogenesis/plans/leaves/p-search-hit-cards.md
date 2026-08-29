---
type: protostar
title: "Search hit cards: print work_id, kva, match field"
created: 2026-08-27
work_id: 2026-08-27-atlas-query-harness-hubs
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "New-surface later: search stdout/JSON includes type, work_id, kva, title-vs-body match. Not this hardening slice."
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md
    kind: derived_from
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: implements
---

## Pending

Change `search.py` only in a later new-surface design with mini-genesis.

## Origin

Harness finding: agents opened too many files because hits lacked structure.
