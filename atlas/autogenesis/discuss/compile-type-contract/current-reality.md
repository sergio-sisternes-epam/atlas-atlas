---
type: document
title: "Current reality — what compile actually gates"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Locked facts for this discussion. Not a product pin."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/hub.md
    kind: derived_from
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
  - path: experiences/2026-08-23-implement-atlas-phase2.md
    kind: backed_by
  - path: decisions/type-vocabulary-document-and-sensitivity.md
    kind: related
---

## Content

Locked for this discussion (not product-implemented):

1. `atlas compile` is an alias of `validate`. Exit 0 means no critical issues.
2. Live checks: SCHEMA file present and root-shaped; staging empty; frontmatter exists; `type` is a non-empty string; body not thinner than `min_body_chars`; Markdown links and `relates_to[].path` resolve on disk; optional mesh merge.
3. `templates.by_type` is read only to enforce the *schema file* simplicity budget (max required keys/sections declared). Pages are not checked against those templates.
4. Phase 2 explicitly deferred section-level template enforcement.
5. Origin and sensitivity stay recommended and must not become compile-required without a new decision that supersedes `type-vocabulary-document-and-sensitivity`.
6. OKF v0.2: unknown `type` values and unknown frontmatter keys must be tolerated. Compile must not close the type enum.
7. Live store `SCHEMA.json` `templates.by_type` = experience, decision, work, document. `types.recommended` also lists lesson, recipe, protostar. Those three have no compiler-visible contract.
8. 27 `type: protostar` pages in this store compile green. Contract misses are remember-path / template misses, not compile-red.
9. `relates_to` checks existence of `path`, not required `kind`s, not work-hub presence.

## Provenance

Read of `scripts/atlas_cli/commands/validate.py`, `core/schema.py`, Phase 2 experience, document-type decision, live SCHEMA.json, protostar quality inventory 2026-08-27.
