---
type: experience
title: "Implemented atlas-optimise vNext (evidence-gated fill; 0.13.0-beta.11; PR #53)"
created: 2026-10-06
work_id: 2026-10-06-atlas-optimise-vnext
status: done
origin: derived
sensitivity: internal
stage: implement
description: "Package implement for atlas-optimise vNext after design tip eb556ce and Hand/Sergio unlock. Shipped on github.com/sergio-sisternes-epam/atlas PR #53 as 0.13.0-beta.11 (head 717b26a). Tests green; no fleet apply; sleep still unimplemented."
plan_path: autogenesis/plans/2026-10-06-atlas-optimise-vnext.md
implements: autogenesis/plans/2026-10-06-atlas-optimise-vnext.md
relates_to:
  - path: autogenesis/plans/2026-10-06-atlas-optimise-vnext.md
    kind: implements
  - path: autogenesis/work/2026-10-06-atlas-optimise-vnext.md
    kind: related
  - path: autogenesis/experiences/2026-10-06-atlas-optimise-vnext-design.md
    kind: follows
---

## Context

work_id `2026-10-06-atlas-optimise-vnext`. Design tip on atlas-atlas: `eb556ce775576915dcd5090164ec3dfd9ae189a6` (PR #25; King's Guard design PASS). Hand/Sergio unlocked package implement only. Subject skill: atlas. Baseline before this cut: `0.13.0-beta.10` tidy optimise (no invent; `missing_gist` uncleared).

## What happened

Autogenesis **implement** recorded the atlas package ship of evidence-gated **fill** beside existing **tidy** repairs:

- Modes: `path` (default, fill on), `full` (`--target .` only, serial only), `custom` (`--custom-tree` prefixes), `incremental` (git commit history, committer clock, default `--since-hours 24`; dirty/uncommitted parents excluded from fill).
- `--tidy-only` skips fill; `--auto-verbatim` required before verbatim fill is `auto`; confirm remains default.
- Plan/apply keep stale hash+HEAD guard over evidence sources; security scan blocks secret-class text and `sensitivity: restricted`; default cost ceiling 200 pages examined; durable receipt (fetch OK, tip, counts, residuals, scan, cost).
- Helper stays standalone; `atlas.py` has no optimise command; install/init/compile/memory-migrate do not call it. Store write stamp stays `0.13.0-beta.7`.
- Sleep/consolidate not implemented. No fleet apply in this cut.

Package PR: https://github.com/sergio-sisternes-epam/atlas/pull/53 — version `0.13.0-beta.11`, PR head `717b26a24920684280970b558fe8720614d5bbbd`, merge commit `7b61c194dc6f2285ab28642052c9e49bdcb1e0d3`, tag `v0.13.0-beta.11` (merged 2026-10-06).

## Changed files

Product files from atlas PR #53:

- `scripts/atlas_optimise.py`
- `scripts/test_atlas_optimise.py`
- `references/paths/atlas-optimise.md`
- `references/scenarios/atlas-optimise-vnext-adversarial-v1.yaml`
- `CHANGELOG.md`
- `apm.yml`
- `SKILL.md`
- `scripts/atlas_cli/__init__.py`
- `references/help/` (`VERSION`, `index.md`, `getting-started.md`)

## Outcome

Tests green on the implement PR: `python3 scripts/run_tests.py` — 19 repository test entrypoints passed, including `scripts/test_atlas_optimise.py` (23 tests) and `scripts/release_readiness.py` (`package_version: 0.13.0-beta.11`). No live-store fleet apply. Sleep/consolidate remains unimplemented.

## Follow-ups

- King's Guard re-audit of these Autogenesis/memory pages (public-repo hygiene) before atlas-atlas remote push.
- Pilot-then-fleet remains an operator/process gate; this cut does not claim fleet readiness.
- Future sleep/consolidate dreamer stays a separate work_id.
