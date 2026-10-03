---
type: work
work_id: 2026-10-04-atlas-recall-rename
title: "Work: 2026-10-04-atlas-recall-rename"
status: done
subject: atlas
plan_path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
closes: [2026-10-04-atlas-recall-rename]
scenario_ref: references/scenarios/recall-rename-adversarial-v1.yaml
evaluation_evidence: "product scripts/run_tests.py exit 0; test_memory_layers.py exit 0; Click registry hard cut verified"
external_ref: "chat t226u"
created: 2026-10-04
updated: 2026-10-04
origin: derived
sensitivity: internal
description: "Implemented. Path query and CLI search renamed to recall / atlas recall run. Hard cut in the 0.13 beta. approval_ref t226u."
relates_to:
  - path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
    kind: related
  - path: experiences/2026-10-04-implement-atlas-recall-rename.md
    kind: related
  - path: decisions/2026-10-04-recall-renames-query-path-and-search.md
    kind: related
  - path: work/2026-10-03-atlas-memory-layers.md
    kind: related
---

# Work: 2026-10-04-atlas-recall-rename

Autogenesis authoring-work record for the recall rename. Not a runtime asset.

## Links

- Plan: `autogenesis/plans/2026-10-04-atlas-recall-rename.md`
- Implement experience: `experiences/2026-10-04-implement-atlas-recall-rename.md`
- Scenario: product `references/scenarios/recall-rename-adversarial-v1.yaml` (draft also under `autogenesis/plans/recall-rename-adversarial-v1.yaml`)
- Evaluation evidence: product `scripts/run_tests.py` exit 0; `test_memory_layers.py` exit 0; Click hard cut verified
- Product implement SHA: `08cc045f8f767f47e5dbf08aa22b98fbcdd76151` on https://github.com/sergio-sisternes-epam/atlas/pull/42
- External ref: chat t226u (2026-10-04)
- Related: `decisions/2026-10-04-recall-renames-query-path-and-search.md`, `work/2026-10-03-atlas-memory-layers.md`

## Status

**done.** Implement landed on PR 42. Not merged. Not tagged.

## Status history

- designed: 2026-10-04. approval_ref t226u recorded. Implement not started.
- implementing: 2026-10-04. Parent bound disposition approved.
- done: 2026-10-04. Experience `experiences/2026-10-04-implement-atlas-recall-rename.md`. Product SHA 08cc045.
