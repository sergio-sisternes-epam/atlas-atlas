---
type: work
work_id: 2026-10-04-atlas-recall-rename
title: "Work: 2026-10-04-atlas-recall-rename"
status: designed
subject: atlas
plan_path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
closes: []
scenario_ref: autogenesis/plans/recall-rename-adversarial-v1.yaml
evaluation_evidence: null
external_ref: "chat t226u"
created: 2026-10-04
updated: 2026-10-04
origin: derived
sensitivity: internal
description: "Design only. Rename path query and the search step to recall. Hard cut in the 0.13 beta. approval_ref t226u does not by itself start implement."
relates_to:
  - path: autogenesis/plans/2026-10-04-atlas-recall-rename.md
    kind: related
  - path: decisions/2026-10-04-recall-renames-query-path-and-search.md
    kind: related
  - path: work/2026-10-03-atlas-memory-layers.md
    kind: related
---

# Work: 2026-10-04-atlas-recall-rename

Autogenesis authoring-work record for the recall rename. Not a runtime asset. This node does not implement the skill.

## Links

- Plan: `autogenesis/plans/2026-10-04-atlas-recall-rename.md`
- Implement experience: (pending; not started)
- Scenario draft: `autogenesis/plans/recall-rename-adversarial-v1.yaml`
- Evaluation evidence: (none; design only)
- External ref: chat t226u (2026-10-04)
- Related: `decisions/2026-10-04-recall-renames-query-path-and-search.md`, `work/2026-10-03-atlas-memory-layers.md`

## Status

**designed.** approval_ref t226u is recorded on the plan. Sergio approved on 2026-10-04 before the plan was shown. This operation does not implement. The parent starts implement only if the pinned plan matches: path `query` becomes `recall`; search ceases to be a separate command; the walk is unchanged; hard cut in this beta.

## Status history

- designed: 2026-10-04. approval_ref t226u recorded. Implement not started.
