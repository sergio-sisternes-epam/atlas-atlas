---
type: lesson
title: "Forgetting is usually failed expression, not guaranteed deletion"
created: 2026-09-03
status: stable
work_id: 2026-09-03-human-memory-model
description: "Interference and remodeling hide traces that can still be re-expressed. Aging often blends bindings rather than blanking the file."
origin: third-party
sensitivity: public
sources:
  - uri: https://www.scientificamerican.com/article/forgotten-memories-may-remain-intact-in-the-brain/
    note: "Engram still present after interference forgetting; stimulation re-expresses"
  - uri: https://www.nature.com/articles/s41380-023-02137-5
    note: "Synaptic remodeling and the plasticity–stability dilemma"
  - uri: https://studyfinds.com/aging-brains-blend-memories-together-instead-of-just-forgetting-them-study-finds/
    note: "Aging category-level misbinding rather than clean deletion"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Content

Natural forgetting has several stacked mechanisms. Retroactive interference can hide an engram that optogenetic stimulation still re-expresses; activity in those cells can be required for the forgetting to happen, which frames forgetting as competition and decision, not only passive fade.

Ongoing synaptic remodeling (plasticity–stability dilemma) moves connectivity off the original pattern, so some loss of faithful replay is the price of new learning. Blocking NMDA-dependent change can reduce forgetting of recent hippocampal memories in animal work.

Aging data often show gist-level blending — category misbinding — rather than an empty slot.

## Implication for Atlas

`forget` / demote should default to “stop expressing in query” (`kva` exit, status, exclude from current view) while leaving the page on disk. Hard delete is a separate, rarer act. Query must prefer current slots or old facts keep winning the contest.
