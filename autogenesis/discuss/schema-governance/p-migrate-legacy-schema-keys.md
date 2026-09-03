---
type: protostar
title: "Migrate legacy SCHEMA keys onto overlays"
created: 2026-09-03
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "Live stores already put kva and autogenesis_space on SCHEMA.json. Moving them to overlays is later work."
relates_to:
  - path: autogenesis/discuss/schema-governance/pin-extension-home.md
    kind: derived_from
---

## Pending

discuss-atlas and sibling stores already extend SCHEMA in-place. A later pass should lift those keys into overlays without a silent rewrite.

## Origin

Consult of discuss-atlas SCHEMA during the opening orbit.
