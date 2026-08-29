---
type: experience
title: "Implement search nav signals + query card (0.7.8 merge)"
created: 2026-08-27
work_id: 2026-08-27-atlas-search-nav-signals
status: closed
origin: internal
sensitivity: internal
implements: 2026-08-27-atlas-search-nav-signals
closes: 2026-08-27-atlas-search-nav-signals
plan_path: autogenesis/plans/2026-08-27-atlas-search-nav-signals.md
construct_eval: deferred
description: "Merged onto query-harness 0.7.7. CLI hit traffic, field filters, B17 card. Glossary rewrite kept."
relates_to:
  - path: work/2026-08-27-atlas-search-nav-signals.md
    kind: implements
  - path: autogenesis/plans/2026-08-27-atlas-search-nav-signals.md
    kind: related
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: follows
  - path: experiences/2026-08-27-implement-query-harness-hubs.md
    kind: follows
---

## Context

Operator asked to re-apply and merge with concurrent 0.7.7 query-harness-hubs (glossary rewrite, spines). That slice did not change `search.py`.

## What happened

Shipped the parked hit-card behaviour as grep-mode payload. Kept their rewrite-once step. Bumped product to 0.7.8 so 0.7.7 remains their version.

## construct_eval

`deferred: deterministic fixture smokes green; construct full loop not run.`

## Changed files

- `scripts/atlas_cli/commands/search.py`
- `scripts/atlas_cli/cli.py`
- `references/paths/query.md` (merged, rewrite step kept)
- `SKILL.md`
- `apm.yml`
- `references/atlas/glossary.md` (one alias row)
- `references/scenarios/search-nav-signals-adversarial-v1.yaml`
- `fixtures/search-nav-atlas/`
- plan / work / this experience

## Outcome

Atlas 0.7.8. Formal lookup = path query + atlas search. 0.7.7 harness intact.
