---
type: document
title: "Atlas capabilities by git mode"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Required companion to git-default decision. What each mode may do."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-optional-git-cut.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Modes

| Mode | What “git” means |
|------|------------------|
| **Remote git** | Working copy + remotes. `atlas auth` + `mount` + push/PR. |
| **Local git** | Working copy, maybe no usable remote (Grok Cloud / air-gapped). Overlay still git. |
| **Headless** | No git repo / no git binary. Tree is just files. |

## Capabilities

| Capability | Remote git | Local git | Headless |
|------------|:----------:|:---------:|:--------:|
| `compile` / validate OKF | yes | yes | yes |
| `query` on a local tree | yes | yes | yes |
| Author pages in place | yes | yes | yes (no history) |
| `atlas mount` from pointer | yes | yes (clone without push) | no |
| `atlas auth` + translation | yes | partial (no remote needed) | no |
| Mesh row for a mounted id | yes | yes | no (or manual path-only) |
| Commit / branch | yes | yes | no |
| Push / PR | yes | no (until a remote exists) | no |
| `atlas://` across mounted ids | yes | yes | only if all trees already on disk and listed |

Headless is reader + edit-in-place on a folder you already have. It is not `mount`. It is not publish.
