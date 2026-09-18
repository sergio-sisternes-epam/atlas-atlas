---
type: document
title: "Requirements — index.md semantic memory organisation"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: settled
kva: alive
reality: current
description: "Sorted requirements for index-first recall. Forget is out of this set."
tags: [requirements, index-md, query]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
  - path: autogenesis/discuss/index-memory/protostar-forget-path.md
    kind: related
---

## Context

Sorted from the 2026-09-18 hub conversation. Must-items are the core algorithm this orbit. Later-items belong to forget and are not design pins here.

## Must — this orbit

1. **STM metaphor.** Every folder `index.md` is short-term memory: the nearest memories, scanned first. Root index maps folders. Child indexes map the pages in that folder.
2. **Write into STM.** When a new memory is stored, it is added to the owning folder `index.md` so it is discoverable without a full-store walk.
3. **Query layer 1.** Skill query instructions treat the STM listing as the first focal point.
4. **Query layer 2.** Deeper recall is `atlas search` for concept pages *not* listed in folder `index.md` files. Indexes are incomplete working sets. Compile listing completeness must change.
5. **Instructions carry it.** Atlas query (and any skill that says query-first, including discuss) must name this two-layer habit. Search is not the default first move.
6. **Autogenesis plan.** The core algorithm is captured as a design that can be implemented later.
7. **Issue lineage.** A GitHub issue should link that plan once the pins are stable enough to implement.

## Later — parked

8. **Forget.** Drop entries from STM without deleting the underlying page.
9. **Access counts.** Frequency of read would inform forget. Tracking that is currently limited.
10. **Order as heat.** Hottest at the top. Forget later drops from the bottom. Top-drop is not current reality.
11. **Heat signal.** Remember inserts at the top. Query is read-only. Heat in this slice is recency of write. True access counts stay with forget.

## Probe

Current Atlas compile requires folder `index.md` where concept pages exist (`index_md_present`). Listing checks are completeness of children, not recency. If STM *is* every folder `index.md`, then “drop from index” becomes a compile miss. That is evidence against collapsing OKF inventory and working memory into one list.

## Outcome

Must-items 1–7 feed the Autogenesis plan. Items 8–11 stay on the forget protostar and on the hub batch.
