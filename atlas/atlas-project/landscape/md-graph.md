---
type: protostar
title: "Landscape — md-graph"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: open
kva: forming
growth: true
star_kind: probe
label: symbiont
description: "Local Markdown link graph + SQLite FTS5. Candidate navigator over Atlas pages, not a second SoR."
origin: third-party
sensitivity: public
sources:
  - https://github.com/LZMW/md-graph
relates_to:
  - path: autogenesis/plans/2026-08-27-atlas-landscape-review.md
    kind: derived_from
  - path: atlas-project/partners/basic-memory.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Growth path

Best current *graph+search over markdown files* symbiont: parse MD, store nodes/links/FTS in local SQLite, MCP navigate. Atlas `relates_to` is stronger than wiki links — a port would index frontmatter edges, not only `[[wiki]]`.

Promote to partners if a spike can query this Atlas store faster than grep without owning claims.

## Open question

Does it honour OKF frontmatter and `relates_to`, or only body links?
