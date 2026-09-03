---
type: decision
title: "Unmounted external Atlas references are non-blocking compile warnings"
created: "2026-09-03"
status: settled
work_id: "2026-09-03-skill-mount-home"
kva: alive
description: "Compile reports atlas_uri_unmounted but exits 0 when no actionable warning or critical issue exists."
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-03-skill-mount-home.md
    kind: implements
  - path: decisions/mount-dot-atlas-submodule.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-uri-vs-hash.md
    kind: related
---

## Decision

An `atlas://` URI whose Atlas ID is absent from the active repository's
`atlas-mesh.json` remains visible as `atlas_uri_unmounted`, but it is a
non-blocking warning.

Compile exits 0 when these are the only issues. It still prints every unknown
ID and the page where it was found.

## Rationale

External Atlas dependencies may be unavailable transiently or intentionally
not mounted in the current repository. That availability condition must not
make an otherwise valid local store fail compilation or force authors to
remove valid cross-Atlas references.

## Boundary

This exception applies only to `atlas_uri_unmounted`. Actionable local warnings
such as missing indexes or page-contract defects still exit 1. Critical schema,
staging, path, and link failures still exit 2.

