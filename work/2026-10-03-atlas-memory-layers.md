---
type: work
title: "Atlas memory layers — page, gist, frame"
created: "2026-10-03"
work_id: "2026-10-03-atlas-memory-layers"
status: done
description: "Full Genesis design for memory as the core concept, the frame-gist-page walk, the strangler rung, and path memory-migrate. Stops for approval. No product implementation."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-10-03-atlas-memory-layers.md
    kind: related
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
  - path: experiences/2026-10-03-implement-atlas-memory-layers.md
    kind: related
---

## Scope

Design how Atlas moves from a document store toward a memory: page, gist, and frame in the same store, STM index.md left intact, document reported on an opt-in compile ladder, and a migration-assistant path for old schemes. Do not implement the skill in this unit until the plan is approved.

## Status

**done** — approved in chat t205u ("Approved. Proceed"). Atlas 0.13.0 is pull request https://github.com/sergio-sisternes-epam/atlas/pull/42 at `e16aa31edaa537215fcf2cc0510e19d08125858e`. Not merged. Not tagged. Subject compile exit 0 at rung info (468 info findings, no warnings, no critical). Experience: `experiences/2026-10-03-implement-atlas-memory-layers.md`. Scenario: `references/scenarios/memory-layers-adversarial-v1.yaml` in the skill repo.

## Outcomes

- Plan: `autogenesis/plans/2026-10-03-atlas-memory-layers.md`.
- Approval ref t205u. Pull request https://github.com/sergio-sisternes-epam/atlas/pull/42 (`e16aa31edaa537215fcf2cc0510e19d08125858e`). Tests and subject compile recorded on the experience.
