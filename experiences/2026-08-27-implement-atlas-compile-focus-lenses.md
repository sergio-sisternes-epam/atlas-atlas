---
type: experience
title: "Implement compile focus lenses (0.7.6)"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-focus-lenses
status: closed
origin: internal
sensitivity: internal
implements: 2026-08-27-atlas-compile-focus-lenses
closes: 2026-08-27-atlas-compile-focus-lenses
plan_path: autogenesis/plans/2026-08-27-atlas-compile-focus-lenses.md
construct_eval: deferred
description: "Removed --list-type. compile/validate --type and --path filter the page walk; store checks stay global; issues plus page list; path escape/missing are critical."
relates_to:
  - path: work/2026-08-27-atlas-compile-focus-lenses.md
    kind: implements
  - path: autogenesis/plans/2026-08-27-atlas-compile-focus-lenses.md
    kind: related
---

## Context

Approved plan `2026-08-27-atlas-compile-focus-lenses`. 0.7.5 `--list-type` listed pages and returned 0.

## What happened

`validate.run` no longer short-circuits. `--type` and `--path` (AND) filter which concept pages emit issues and appear in `pages`. SCHEMA/staging/mesh/index still run. `--path` resolve must stay under `--root` and must exist.

## construct_eval

`deferred: construct create failed on this scenario YAML (packages list shape). Deterministic CLI smokes matching the five approved ids ran green by hand.`

## Changed files

- `scripts/atlas_cli/cli.py`
- `scripts/atlas_cli/commands/validate.py`
- `SKILL.md`
- `apm.yml`
- `references/scenarios/compile-focus-lenses-adversarial-v1.yaml`
- `references/atlas/autogenesis/plans/2026-08-27-atlas-compile-focus-lenses.md`
- `references/atlas/work/2026-08-27-atlas-compile-focus-lenses.md`
- `references/atlas/log.md`
- this experience
