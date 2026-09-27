---
type: work
title: "Work — git-backed version links and live-tree pruning"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: closed
description: "Closed 2026-09-27. Checkpoint + Claim A/B decisions on atlas-atlas; implement via atlas issues #37 (Claim B) and #38 (Claim A); shared relates_to.ref time-travel."
relates_to:
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/thesis-git-is-durability-live-tree-may-prune.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
---

## Scope

Durable discussion on whether Atlas should treat Git history as first-class relatedness for page lineage and for KVA exit cleanup.

Primary fabric: this store (`github.com/sergio-sisternes-epam/atlas-atlas`). discuss-atlas is not the home for this orbit.

## Status

**Closed** (checkpointed) 2026-09-27. Discussion concluded; implementation tracked on the Atlas product repo.

## Outcomes

- Constellation checkpoint: `autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md` (merged via atlas-atlas PR #19).
- Claim B decision (tip terminate summary + prune failed path + `ref` history): durable memory + https://github.com/sergio-sisternes-epam/atlas/issues/37
- Claim A decision (living-page version hints via `ref`): durable memory + https://github.com/sergio-sisternes-epam/atlas/issues/38
- Shared capability: optional `relates_to.ref` as space/time travel; tip compile does not resolve `ref` for now.
- Delete/terminate = tip and default-search exclusion; git retains the trail.
