---
type: plan
title: "Plan — grep search + query path + B17 card"
created: 2026-08-27
work_id: 2026-08-27-atlas-search-nav-signals
status: done
description: "Merged onto 0.7.7 query-harness. Path query plus card. CLI search carries traffic. Version 0.7.8."
origin: derived
sensitivity: internal
change_class: new-surface
kva: alive
stage: implement
plan_path: autogenesis/plans/2026-08-27-atlas-search-nav-signals.md
relates_to:
  - path: work/2026-08-27-atlas-search-nav-signals.md
    kind: implements
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: follows
  - path: work/atlas-agentic-integration-v1.md
    kind: follows
  - path: experiences/2026-08-27-implement-atlas-search-nav-signals.md
    kind: related
---

## Intent

Keep the 0.7.7 glossary rewrite-once harness. Add the missing engine and card: search hits carry traffic; formal lookup requires B17 `path: query`.

## Change-class

`new-surface`

## Merge notes

Their 0.7.7 took the skill version for path prose and spines and parked hit-cards. This work ships the hit-card CLI and does not drop their rewrite step. Product version becomes **0.7.8** so 0.7.7 stays their identity.

## Pinned decisions

- Do not merge query and search names.
- B17 card required for formal lookup.
- Closed filters: `type:` `kva:` `status:` `work_id:` `path:`
- Default-exclude exit states.
- Keep glossary Search aliases rewrite (at most once).
- Shared guidance names `relates_to`.

Approved (“Agreed. Continue”; “Re-apply”; “merge changes”).
