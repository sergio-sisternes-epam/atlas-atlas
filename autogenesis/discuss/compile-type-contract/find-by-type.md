---
type: document
title: "Orbit — how we list pages of one type"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin U: compile lists accidents; search filters by type. Compile listing ships first."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-search-by-type.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/forming-documents.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Search today ranks pages that *mention* a type, not pages that *are* that type. That is how we missed the 27 protostars.

**S — compile lists them.** Stage 2 uses the warning list and, if useful, a simple `atlas compile --list-type protostar`. Search can wait.

**T — search must understand type now.** Add a type filter to search in the same Stage 1 as the compile gap.

**U — both.** Compile lists accidents. Search also filters by frontmatter type (indexing, in scope for Atlas).

**Pin (operator 2026-08-27): U.** Compile listing ships first. Search-by-type follows. Not blocked on BM25.

## Provenance

Last parked item from the original quality inventory.
