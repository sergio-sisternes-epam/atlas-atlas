---
type: document
title: "Thesis — two-layer compile: valid schema, then pages against it"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Operator questions restated as the living thesis. Not a design pin. Not implement authority."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/hub.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/current-reality.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/prior-slices.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Current reality vs alternative: this branch is the current lean.

**Layer 1 — schema definitions are valid.**  
`SCHEMA.json` must be a well-formed Atlas schema before any page is judged against it. That is more than “file exists and parses as JSON.” A valid definition means:

- Required root fields present (`schema_version`, `atlas_id`, `structure`, `compile`).
- `templates.by_type` entries are objects with `frontmatter` / `sections` lists that stay inside the simplicity budget.
- Advertised `compile.core_checks` name checks the CLI actually runs, or the extra names are removed.
- `types.recommended` and `templates.by_type` do not silently disagree: a recommended type is either *constrained* (has a by_type block) or *explicitly unconstrained*.
- Relation `recommended_kinds` is a declared list; unknown kinds on pages are a page-layer issue, not a schema-invalid issue.

`SCHEMA.contract.json` is a candidate meta-schema for Layer 1. Whether the contract file or the live SCHEMA is the authority is still a forming leaf.

**Layer 2 — pages comply with schemas that are properly defined.**  
“Properly defined” is the safety valve, not a weasel. A page is judged only against a contract that Layer 1 accepted for that `type`:

- If `templates.by_type[type]` exists → required keys and required sections apply.
- If the type is absent from `by_type` → OKF freedom: frontmatter + non-empty `type` only. Unknown types stay legal.
- Recommended keys (`origin`, `sensitivity`) stay recommended unless a new decision supersedes the 2026-08-24 pin.
- Extra work-cluster rules (`work_id` → `implements`, protostar → `derived_from`) belong here only after they are written into SCHEMA (a proper definition), not as remember-path folklore.

Lean on the operator questions: **yes and yes.** Compile today does a weak Layer 1 and no Layer 2. That is why 27 protostars are green and still contract-wrong.

This page does not pick warning vs critical, does not rewrite SCHEMA, and does not author Gherkin. Those stay forming children.

## Provenance

Operator turn 2026-08-27: “should we ensure atlas compile validates that (1) schema definitions are valid (2) pages are compliant with any schemas properly defined.”
