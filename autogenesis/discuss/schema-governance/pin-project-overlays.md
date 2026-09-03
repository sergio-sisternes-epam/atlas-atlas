---
type: document
title: "Pin — project overlays before a skill exists"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Agents may schema new a bespoke overlay on a project Atlas. Same compile gates. Not a SCHEMA.json back door."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: autogenesis/discuss/schema-governance/pin-path-cli.md
    kind: follows
  - path: autogenesis/discuss/schema-governance/pin-contribute.md
    kind: related
---

## Content

A project may be building a new idea that is not yet a skill. Agents need freedom to create an overlay and compile it.

**Pin:** agents may create a bespoke overlay on a project Atlas before any skill exists. Freedom is `atlas schema new <id>` (schema path) plus compile, not a hand-edit of SCHEMA.json. Same merge and claimed-prefix gates as a skill overlay. When the idea later becomes a skill, the overlay moves into that skill’s `contributions/<id>/`. No sandbox that skips compile.

Set aside: project stores exempt from overlay rules; staging overlays that compile ignores.

## Provenance

Operator 2026-09-03, plan-rejection feedback then pin.
