---
type: document
title: "Q7 — is --path the same kind of compile lens as --type?"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin A: --path filters the page walk to that store-relative prefix. Anything under the path is compiled. Store checks still run."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/q-type-stdout.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/q-scope-still-runs-store.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/q-stack-type-path.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Operator note (2026-08-27)

Compile should also support `--path`, to direct compilation at a subgraph under a path.

## Question

Is `--path` the same focusing model as `--type`?

**A — Same lens, different key.** Store-level checks always run (SCHEMA, staging, mesh, index). Only the page walk is limited to pages whose store-relative path is that prefix (folder or a single file). Exit remains 0/1/2 from that invocation. `--type` and `--path` may later stack; that is not this question.

**B — Different tool.** `--path` means something else (only that folder’s SCHEMA, skip store checks, treat the folder as its own atlas, etc.).

## Answer (operator 2026-08-27)

**A.** Filter by path. Anything in that path is compiled.
