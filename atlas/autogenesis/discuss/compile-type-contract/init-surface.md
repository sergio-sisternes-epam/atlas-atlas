---
type: document
title: "Orbit — how a new Atlas gets its first SCHEMA"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin F: atlas init writes the first SCHEMA."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-init-surface.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/unconstrained-types.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/reusable-schema.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

New Atlas folders today have no helper that writes SCHEMA.json. Compile only fails if the file is missing. That is a lock, not a factory.

**F — command only.** A program `atlas init` writes the first SCHEMA and default templates.

**G — instructions only.** A written path tells the agent which files to create. No new command.

**H — both.** The path tells the agent when. The command is the only thing allowed to write the first SCHEMA (so every harness does the same thing).

**Pin (operator 2026-08-27): F.**  
`atlas init` writes the first SCHEMA. No requirement that a schema path be the only writer.

## Provenance

Next parked item after pin C.
