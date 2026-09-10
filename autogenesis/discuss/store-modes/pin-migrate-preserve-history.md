---
type: document
title: "Pin — strategy migrate preserves store git history"
created: "2026-09-10"
status: settled
kva: alive
reality: current
description: "dedicated ↔ shared pushes the existing store commits onto the destination remote or atlas branch. No page-import rewrite."
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/store-modes/migrate-path-orbit.md
work_id: "2026-09-10-atlas-store-modes"
relates_to:
  - path: autogenesis/discuss/store-modes/migrate-path-orbit.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-migrate-one-path.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
---

## Content

Operator pin, 2026-09-10: strategy migrate **preserves git history**.

The existing store commits are pushed onto the destination. Dedicated → shared: those commits land on consumer branch `atlas`. Shared → dedicated: those commits land on the dedicated remote (operator still supplies an existing remote; Atlas does not create the host repository).

Do not init a blank destination and copy pages. Fail closed if the destination already has unrelated history that cannot fast-forward that push.

After the push: rewrite the parent gitlink, write mesh `strategy` and `id`, compile green on the new root. No dual-write.

## Provenance

Operator choice on migrate-path orbit, item 2.
