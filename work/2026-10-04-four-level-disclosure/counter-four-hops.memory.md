---
type: page
title: Counter: four hops versus two-level hierarchies
created: 2026-10-04
work_id: 2026-10-04-four-level-disclosure
kva: alive
reality: current
status: settled
origin: third-party
sensitivity: internal
relates_to:
  - path: work/2026-10-04-four-level-disclosure/hub.md
    kind: implements
  - path: work/2026-10-04-four-level-disclosure/theory.memory.md
    kind: counters
  - path: work/2026-10-04-four-level-disclosure/counters.memory.md
    kind: related
---

## What happened

Engaged counter, kept. Retrieval literature pulls two ways. Multi-hop walks can be required to reach evidence, and a two-level hierarchy can beat a flat store by letting a coarse layer select a small evidence set. HiGMem's event-turn hierarchy is one such two-level result: removing the event layer lowered F1 and recall, and a flat retrieval plus a later filter still returned a larger, less precise set. Sources: https://arxiv.org/html/2604.18349v2 and https://arxiv.org/pdf/2603.21564

Applied here: recall walks index, then schema, then gist, then memory, and stops when the level already answers. The stack is four levels deep, not a mandate to take four hops, and not a collapse back to only two levels.
