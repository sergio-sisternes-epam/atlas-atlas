---
type: document
title: "Sketch — protostar templates.by_type contract"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Illustration of a properly defined protostar schema. Not written into live SCHEMA.json. Not implement."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/unconstrained-types.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-unconstrained-types.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Illustration only. Live `SCHEMA.json` is unchanged.

A protostar contract in `templates.by_type` would look like the experience block, with this payload:

Required frontmatter stays at three keys (`type`, `title`, `created`) so the simplicity budget is not spent. Work-cluster edges are a separate compile rule object, because they are conditional (`if work_id`).

Required sections follow the existing markdown template: `Pending`, `Origin`. Discuss pages today use `Growth path` / `Open question` instead — that mismatch is why Layer 2 would warn.

Work-cluster rule (only enforceable after it lives in SCHEMA): if `work_id` is set, `relates_to` must include `kind: implements` to an existing work hub; protostar also needs `kind: derived_from`.

Against `autogenesis/discuss/git-mesh/leaves/p-auth-precedence.md`, warnings would be: no `implements` to the work hub; required section `Pending` missing. `derived_from` and required FM already pass. Compile stays exit 0 / 1 under pin A, not exit 2.

## Provenance

Operator asked to see the new contract. Orbit 2, still unpinned C/D/E.
