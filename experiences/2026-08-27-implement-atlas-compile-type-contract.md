---
type: experience
title: "Implement Atlas compile type-contract gate (0.7.5)"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: closed
origin: internal
sensitivity: internal
description: "Stage 1 compile Layer 1+2, atlas init, type listing and search type filter. Used compile warnings to repair this store to exit 0."
relates_to:
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
  - path: autogenesis/plans/2026-08-27-atlas-compile-type-contract.md
    kind: related
---

## Context

Approved plan: close the compile gap, then use compile as the repair list. This store was the first customer.

## What happened

Compile now checks SCHEMA against the skill contract, required frontmatter per `templates.by_type`, work-hub `implements` (not on `type: work` pages), protostar `derived_from`, and `kva: forming` on `type: document`. Headings are not checked. `atlas init` writes a first SCHEMA. `--list-type` and search `type:` filter on frontmatter.

First compile of this store produced 56 warnings. Feedback loop: add missing edges, set conversation documents from `kva: forming` to `alive`. Second compile: exit 0.

Work hubs are not required to `implements` themselves. Forming-type rule applies to documents only.

## Outcome

Atlas 0.7.5. This store compile-green. Stage 2 for other skills’ stores is their compile list, not this Run.

## Changed files

- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/validate.py`
- `scripts/atlas_cli/commands/init.py`
- `scripts/atlas_cli/commands/search.py`
- `scripts/atlas_cli/core/schema.py`
- `references/SCHEMA.contract.json`
- `references/atlas/SCHEMA.json`
- `references/templates/protostar.md`
- `references/templates/lesson.md`
- `references/templates/recipe.md`
- `references/atlas/templates/lesson.md`
- `references/atlas/templates/recipe.md`
- `SKILL.md`
- `references/scenarios/compile-type-contract-adversarial-v1.yaml`
- this store: protostar `implements` / landscape `derived_from` / forming documents → `kva: alive`
- `autogenesis/plans/2026-08-27-atlas-compile-type-contract.md`
- `work/2026-08-27-atlas-compile-type-contract.md`
- this experience
