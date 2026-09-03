---
type: protostar
title: "Init applies skill overlays at store birth"
created: 2026-09-03
status: open
kva: forming
growth: true
star_kind: action
origin: derived
sensitivity: internal
description: "atlas init writes core SCHEMA. How a skill-owned store gets its overlay on first init is unpinned."
relates_to:
  - path: autogenesis/discuss/schema-governance/pin-path-cli.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/init-surface.md
    kind: related
---

## Pending

A discuss-atlas birth should not hand-write `kva` into SCHEMA.json. Init plus schema path should apply the skill overlay. Exact call sequence is unpinned.

## Origin

Path-vs-CLI pin, against pin F.
