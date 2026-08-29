---
type: document
title: "Prior slices — type-contract work already recommended"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "The five slices proposed before the operator restated the gate as two layers."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/hub.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/two-layer-gate.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

These slices remain in scope. They sit *under* the two-layer gate; they are not a rival thesis.

1. **SCHEMA completeness** — add protostar (and any other recommended type we intend to enforce) to `templates.by_type`. Align advertised `core_checks` with the CLI.
2. **Page-level apply of `templates.by_type`** — required frontmatter and required sections for types that have a template block. Start as warnings.
3. **Work-cluster lint** — `work_id` implies `implements` → existing work hub. Protostar also implies `derived_from` origin.
4. **Repair pass** — fix this store against the new warnings before promoting rules to critical.
5. **Construct smokes** — missing required key; work_id without implements; Phase 2 criticals still fail.

Out of those slices: BM25, landscape promote/terminate calls, hard-requiring origin/sensitivity.

## Provenance

Agent recommendation in the same conversation, accepted as the base by the operator (“on top of your recommendations”).
