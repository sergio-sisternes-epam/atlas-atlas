---
type: lesson
title: "Retrieval can open a gated update window; in-place rewrite is not settled"
created: 2026-09-03
status: contested
work_id: 2026-09-03-human-memory-model
description: "Reconsolidation can strengthen, weaken, or update a trace. Apparent updates may be a new trace that outcompetes the old one."
origin: third-party
sensitivity: public
sources:
  - uri: https://www.sciencedirect.com/science/article/abs/pii/S0149763425001988
    note: "Reconsolidation temporal and molecular windows"
  - uri: https://ueaeprints.uea.ac.uk/100688/3/Rugg_Renoult_2025_NBR.pdf
    note: "Rugg and Renoult 2025 — update vs coexisting new trace unclear"
  - uri: https://www.cell.com/neuron/fulltext/S0896-6273(15)00761-8
    note: "Dudai consolidation and transformation review"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: lessons/prediction-error-update-or-differentiate.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Content

After some retrievals, a consolidated memory can become labile again and must restabilize (reconsolidation). In that window the trace can be strengthened, weakened, updated, or disrupted. The window is gated by age of the memory, prediction error, and how the reminder is run. It does not open on every recall.

Extinction is often a second memory with opposite meaning that inhibits the first, not a shred of the original file.

Rugg and Renoult (2025) argue human and animal evidence is compatible with coexistence: the original trace remains, a new trace is encoded, and retrieval picks a winner. It is not established that “memory updating” always rewrites the content of the old engram.

## Implication for Atlas

Allow a gated edit of a *current-theory* slot after an explicit reminder plus new information. Keep the prior expression as a page with `supersedes` / `contradicts` rather than assuming the bytes were rewritten in place. Mark this lesson contested until a probe distinguishes update from competition.
