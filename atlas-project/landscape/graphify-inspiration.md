---
type: protostar
title: "Landscape — Graphify ideas Atlas might grow"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: open
kva: forming
growth: true
star_kind: action
label: symbiont
description: "Expansion areas inspired by Graphify. Not a commitment to graph.json as SoR. Owns forming spikes until a work branch starts."
origin: derived
sensitivity: internal
relates_to:
  - path: atlas-project/landscape/graphify.md
    kind: derived_from
  - path: atlas-project/landscape/graph-json-challenge.md
    kind: related
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Growth path

Steal the overlay protocol, not the product. Each row may become its own work hub; until then this page owns them.

| Idea | Atlas shape | Do not copy |
|---|---|---|
| EXTRACTED vs INFERRED vs AMBIGUOUS | Tag derived edges; frontmatter `relates_to` is EXTRACTED only | LLM `semantically_similar_to` in the committed graph |
| SHA256 skip-unchanged cache | Compile / Cartograph keyed by page hash | Cache as SoR |
| `built_from` commit | Projection header vs `HEAD` | Trust a stale overlay |
| Grow-only incremental merge | Union changed pages into a compile cache; refuse shrink without `--force` | Silent overwrite |
| Repo-tagged `merge-graphs` | Mesh `atlas://` ids; join on path+hash | Prefix soup that hides the page |
| JSONL nodes/links sorted by id | Optional `.atlas/` artifact if we persist a cache | Pretty-printed 40k-line `graph.json` as merge surface |
| Custom git merge driver | Seatbelt only if we *commit* that cache | Driver religion when compile can rebuild from pages |
| Leiden communities | Optional Cartograph view | Community id as identity |

## Open question

Which single spike first: EXTRACTED/INFERRED on compile output, or `built_from` freshness on Cartograph?

The Cartograph context link now points to the current standalone package.
Its earlier in-Atlas location is retained in the
[historical exit record](../../decisions/cartograph-fork-in-atlas-exit.md).
This navigation update does not approve or implement any of the ideas above.
