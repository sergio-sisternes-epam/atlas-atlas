---
type: document
title: "Challenge — KVA fields are not enough to navigate a growing graph"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "think-challenge on lifecycle signals: needs expansion, in progress, early idea, dead end. Grounded in search. Not implement."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/approach.md
    kind: counters
  - path: autogenesis/discuss/compile-type-contract/two-stage-fix.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Claim under review: `kva` + `type` + `growth` + `status` are the signals an agent uses to find what needs expansion, what is being expanded, what is early, and what is a dead end.

### Counters

1. Declared status rot. People stop updating lifecycle tags; notes pile up as blank/forming forever.
2. Classification tax. Extra fields that overlap (`kva` vs `status` vs `growth` vs `type: protostar`) get applied inconsistently or abandoned.
3. Knowledge rot is currency and conflict, not only a terminated flag. Alive pages go stale without the label changing.
4. Deadness has two faces: target gone (broken path) vs target still there but meaning changed. Compile today sees only the first.
5. Wikipedia-scale graphs infer growth/decay/stability from link add vs remove, not from a status field on the article.

### Implication for Atlas

Keep a short declared vocabulary (KVA). Add inferred signals compile or query can compute: last work_id activity, missing required edges, current_branch, broken vs superseded links. Do not grow another status enum.

Grounding: Garfield knowledge rot; note-tag abandonment; Wikipedia link add/remove classes; linked-data structural vs semantic broken links; LLM-wiki claim states (stale, contradicted, current).

## Provenance

Operator asked think-challenge on KVA navigation signals. Search-backed. Not a pin.
