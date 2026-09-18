---
type: document
title: "1-by-1 — remember inserts at top, query is read-only"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: settled
kva: alive
reality: current
description: "Heat for this implement slice is recency of write. New STM lines go to the top. Query does not rewrite indexes."
tags: [index-md, remember, query]
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/index-memory/hub.md
    kind: derived_from
  - path: autogenesis/discuss/index-memory/order-hottest-first.md
    kind: follows
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: related
  - path: autogenesis/discuss/index-memory/protostar-forget-path.md
    kind: related
---

## Context

Follows hottest-first. There is no access-count telemetry. Query-promoting lines would mutate the store on every recall.

## Decision

Path remember, after compile green, inserts the new page at the **top** of the owning folder `index.md`. Query reads indexes and does not rewrite them.

Heat in this slice is recency of write, used as a stand-in for hottest-first. Promote-on-query and true counts stay on the forget protostar.

## Outcome

P7 is alive. Core algorithm pins are complete enough to approve the plan and file a GitHub issue.
