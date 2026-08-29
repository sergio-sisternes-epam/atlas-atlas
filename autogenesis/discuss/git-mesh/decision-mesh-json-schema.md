---
type: decision
title: "Mesh config is JSON with a schema"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Project-root atlas-mesh.json. All Atlas config files are JSON validated against a schema."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mesh-on-disk.md
    kind: derived_from
  - path: work/mesh-mvp/t-mesh-file.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

Atlas configuration files are **JSON**, checked against a published schema. The project mesh file is **`atlas-mesh.json`** at the repository root (or the directory where `mount` ran if there is no parent git).

YAML is not a config format for Atlas. `mount` writes valid JSON only. `compile` / `mount` fail if the file does not match the schema.

## Alternatives considered

- `atlas-mesh.yml` — rejected; user wants JSON plus schema for all config.
---
