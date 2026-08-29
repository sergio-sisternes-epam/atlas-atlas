---
type: document
title: "Branching is how Atlas knowledge grows"
created: 2026-08-27
description: "Git branches carry temporary truths. Merge is the institutional act. Fixed infrastructure fights agent-speed knowledge evolution."
origin: user
sensitivity: internal
status: alive
kva: alive
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/vision.md
    kind: derived_from
  - path: atlas-project/sdlc-first.md
    kind: related
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: related
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: related
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: related
---

## Content

Institutional pools assume one current truth, one indexer, one budget owner. Agentic SDLC assumes many concurrent truths, most of them temporary.

| Work shape | Knowledge shape |
|---|---|
| Feature branch | Knowledge branch: draft requirements, decisions, protostars |
| Modernisation spike | Forked as-is / to-be Atlas; merge only when the spike is real |
| Test failure | Experience on the finding branch; lesson promoted when compile-green |
| Incident | Ops experience on a hotfix branch; recipe PRed to the shared ops Atlas |
| Team B consumes Team A | Submodule mount of A at a SHA; PR into A if B finds a contract gap |

Submodule-at-a-pinned-branch matters more than a remote graph map. Team B must work against last week’s understanding while Team A’s main has moved. A central graph that only shows HEAD cannot do that without reinventing git.

Contribution MVP (already forming in git-mesh): `atlas checkout` materialises a submodule; write is edit + commit + pull request; compile on the contributor clone and again in CI.

## Provenance

User framing 2026-08-27 joined to work `2026-08-26-atlas-modular-graph-protocol`.
