---
type: work
title: "Atlas compile as schema + page-contract gate"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: done
description: "Implemented Atlas 0.7.5. Compile type-contract gate, init, list-type, search type filter. This store repaired to compile exit 0."
origin: user
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/discuss/compile-type-contract/hub.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/approach.md
    kind: related
  - path: autogenesis/plans/2026-08-27-atlas-compile-type-contract.md
    kind: related
  - path: experiences/2026-08-27-implement-atlas-compile-type-contract.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: related
  - path: work/2026-08-26-residuals-vs-protostar.md
    kind: follows
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: related
  - path: decisions/type-vocabulary-document-and-sensitivity.md
    kind: related
---

## Scope

Shape (not implement) a compile change so Atlas stops treating file-graph health as type-contract health.

In scope for discussion:

1. Validate that `SCHEMA.json` definitions are internally valid.
2. Validate that pages comply with any type contract that SCHEMA properly defines.
3. Prior slices: SCHEMA completeness for protostar, warning-then-critical rollout, work-cluster lint, repair pass, construct smokes.

Out of scope: BM25, landscape content calls, hard-requiring origin/sensitivity, discussion → implement.

## Status

**done** — 2026-08-27. Atlas 0.7.5.

## Outcomes

- Plan implemented
- Experience: `experiences/2026-08-27-implement-atlas-compile-type-contract.md`
- This store compile exit 0 after repair against the new warning list
- Construct suite not run as a packaged fixture; CLI smokes run by hand (`init`, `--list-type`, `type:` search)
