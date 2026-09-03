---
type: work
title: "Atlas schema governance — overlays, schema path, claimed prefixes"
created: 2026-09-03
work_id: 2026-09-03-atlas-schema-governance
status: done
description: "Shipped Atlas 0.8.5 schema path, overlay merge, schema new/install/uninstall, and write-receipt compile gates."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: related
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: related
  - path: autogenesis/discuss/schema-governance/current-reality.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: follows
  - path: experiences/2026-09-03-implement-atlas-schema-governance.md
    kind: related
---

## Scope

Add a schema activation path and CLI so skills and projects extend SCHEMA via overlay files, not free edits or root dumps. Compile merges overlays and fails on core-key clashes and undeclared install writes.

## Status

done — 2026-09-03. Atlas 0.8.5.

## Outcomes

- Path `schema` and CLI `atlas schema new|install|uninstall`
- Compile merges `schema.d/`; critical on core clash, core-type mutate, overlay-key clash, undeclared receipt paths
- Smokes: `scripts/test_schema_governance.py` all passed
- Experience: `experiences/2026-09-03-implement-atlas-schema-governance.md`

## Related

Discussion fabric: `autogenesis/discuss/schema-governance/`. Prior work: compile-type-contract (pin F, two-layer compile).
