---
type: work
title: Operator-chosen four-layer migration
created: 2026-10-04
work_id: 2026-10-04-four-layer-migration
status: done
kva: alive
stage: done
plan_path: autogenesis/plans/2026-10-04-four-layer-migration.md
origin: derived
sensitivity: internal
description: Canonical work node for the operator-chosen four-layer migration. Design is persisted. Implementation waits for explicit approval.
relates_to:
  - path: autogenesis/plans/2026-10-04-four-layer-migration.md
    kind: related
  - path: autogenesis/experiences/2026-10-04-four-layer-migration.md
    kind: records
---

## Scope

Design an operator-chosen migration of a whole Atlas store onto the four-layer contract shape. The migration is not on install, compile, or schema upgrade. A frame description that will not round-trip keeps its text and gets a named finding plus a written operator step.

## Status

**done.** PR https://github.com/sergio-sisternes-epam/atlas/pull/48 merged at 9802abf.  Approved by Sergio 2026-10-04 after the plan was persisted. Plan: `autogenesis/plans/2026-10-04-four-layer-migration.md`. Approval is not copied from the request card. The operator sentence applies only after this page exists.

## Outcomes

- Plan persisted at `autogenesis/plans/2026-10-04-four-layer-migration.md`.
- Change-class new-surface. New package cut named in the plan: 0.13.0-beta.7.
- No product code in this design step.
