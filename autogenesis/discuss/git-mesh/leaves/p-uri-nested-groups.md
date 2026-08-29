---
type: protostar
title: "URI id width beyond two path segments"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: open
kva: forming
reality: current
growth: true
star_kind: refine
description: "MVP two-segment peel leaves GitLab nested groups and other namespace widths behind."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-uri-id-extract-mvp.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/uri-id-extract.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Growth path

Add host-width tables and/or longest-prefix match against known atlas-ids so `gitlab.example/a/b/c/proj/page.md` does not treat `b` as the repo. Also self-hosted path depths, `www` already stripped by normalise, and any host where org is not one segment.

## Open question

When the store is not yet in the mesh, how does resolve know the id width without a profile for that host?
---
