---
type: document
title: "Q3 — scoped compile still runs store-level checks?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin A: --list-type filters the page walk only. SCHEMA, staging, mesh, index still run on the whole store."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-list-type-scopes-gate.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/q-flag-name.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Question

`compile --list-type protostar` is a focused gate. What still always runs?

**A — Filter pages only.** Store-level checks always run: SCHEMA present and valid, staging empty, mesh, recommended-type-without-contract, root/folder index rules. Only the *page* walk (frontmatter, links, page-contract) is limited to `type: protostar`. A broken SCHEMA cannot hide behind a type focus.

**B — Filter the whole compile.** If you asked for protostars, only protostar pages are considered. SCHEMA/staging/index are out of this invocation.

A keeps compile as one gate with a lens. B makes `--list-type` a different, weaker program.

## Answer (operator 2026-08-27)

**A.**
