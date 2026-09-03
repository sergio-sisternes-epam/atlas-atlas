---
type: lesson
title: "Permanence of a page is not evidence it is current or true"
created: 2026-09-03
status: stable
work_id: 2026-09-03-human-memory-model
description: "An append-only store preserves errors as faithfully as facts. Current belief is a retrieval policy."
origin: derived
sensitivity: public
sources:
  - uri: https://arxiv.org/html/2507.08844v1
    note: "Immutability does not guarantee trust; garbage-in, garbage-eternally"
  - uri: https://levelup.gitconnected.com/ai-agent-doesnt-have-a-memory-problem-it-has-a-write-policy-problem-2c7c937a1ced
    note: "Agent memory is a write-policy problem; supersede rather than accumulate"
  - uri: https://jasondoyle.ie/whitepapers/when-memory-becomes-production-state/
    note: "Stale contradictory memory; consolidation can erase history or pick the wrong winner"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: lessons/forgetting-is-expression-failure.md
    kind: related
  - path: lessons/reconsolidation-gated-update.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Content

Cryptographic or filesystem permanence keeps lies, slander, and honest errors as well as useful facts. Trust and current belief are not properties of an append-only log.

Agent-memory practice matches the brain’s retrieval contest: if new information accumulates instead of superseding a slot, corrected preferences return. Consolidation that “resolves” contradictions can also drop history or elect the wrong winner. Concurrent writers without atomic append lose updates.

## Implication for Atlas

Integrity of history and correctness of answers are different jobs. log.md and episode pages may be append-only. Query answers from the current view. A signed old page is not licensed as live guidance.
