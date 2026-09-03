---
type: document
title: "Pin — schema path plus CLI as only writer"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Schema path tells the agent when. CLI init and schema install or schema new are the only writers."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: autogenesis/discuss/schema-governance/pin-root-layout.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/init-surface.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/leaves/p-schema-path.md
    kind: related
---

## Content

Who may write SCHEMA.json and schema.d overlays. Pin F already says `atlas init` writes the first SCHEMA. Do not reopen F.

**Pin:** schema path tells the agent when. CLI (`init`, `schema install`, and later `schema new`) is the only writer.

Set aside: path-only file copy with no CLI; CLI with no schema path; agent hand-edit of SCHEMA.json on skill-owned stores.

This answers the forming lean on reusable-schema / p-schema-path: yes, path_id `schema`. The path module itself is still not implement.

## Provenance

Operator 2026-09-03, fifth orbit.
