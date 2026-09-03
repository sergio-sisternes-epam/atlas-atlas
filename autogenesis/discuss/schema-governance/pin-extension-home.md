---
type: document
title: "Pin — overlay files merged at compile"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Core SCHEMA.json stays closed. Skill and project extras live in overlay files. Compile merges. Clash with a core key fails."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: autogenesis/discuss/schema-governance/pin-contribute.md
    kind: follows
---

## Content

Where extra SCHEMA lives, given local extend plus host install.

**Pin:** overlay contribution files, merged at compile. Core SCHEMA.json stays closed.

Example used in the orbit: a skill ships `contributions/<id>/SCHEMA.overlay.json` plus templates. Host install writes `schema.d/<id>.json`. Compile merges core + `schema.d/*` and fails if an overlay overwrites a core key or claims a reserved root name. Uninstall is delete the overlay file.

Set aside: namespaced keys inside the one SCHEMA.json; closed core with no extra keys; free extra keys with no namespace.

Overlay filename and package layout remain forming.

## Provenance

Operator 2026-09-03, after an overlay example.
