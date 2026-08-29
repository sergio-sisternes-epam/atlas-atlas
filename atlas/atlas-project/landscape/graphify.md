---
type: protostar
title: "Landscape — Graphify"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: open
kva: forming
growth: true
star_kind: probe
label: symbiont
description: "Local code+doc graph with graph.json overlay. Adapter for corpora we will not lift into Atlas. Not Atlas SoR."
origin: third-party
sensitivity: public
sources:
  - https://github.com/Graphify-Labs/graphify
  - https://github.com/Graphify-Labs/graphify/blob/v8/docs/how-it-works.md
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-landscape-review.md
    kind: derived_from
  - path: atlas-project/landscape/graph-json-challenge.md
    kind: related
  - path: atlas-project/landscape/md-graph.md
    kind: related
  - path: atlas-project/vision.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Content

Graphify builds `graphify-out/graph.json` (NetworkX node-link), `GRAPH_REPORT.md`, optional wiki, SHA256 cache. Code via tree-sitter (EXTRACTED). Docs/PDF via LLM (INFERRED). Git merge driver union-merges two `graph.json` files. `merge-graphs` tags nodes by repo.

**Takes:** navigation over a folder that stays code/PDF/notes.

**Must not take:** Atlas claim SoR. Pages plus `relates_to` remain the graph.

## Growth path

Keep as landscape-owned adapter/symbiont. Promote to `partners/` only if we mount a code repo beside Atlas and need their AST graph. Inspiration for *our* compile cache lives on `graphify-inspiration.md`.

## Open question

Do we ever vendor Graphify as a CLI next to `atlas compile`, or only steal overlay ideas?
