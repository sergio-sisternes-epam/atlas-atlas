---
type: decision
title: "Default mount path is nested .atlas/host/org/repo/"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Encoding of atlas-id on disk is nested directories. Reversible 1:1 with scheme-free id."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/mount-path-encoding.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-kebab-encoding.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

Default `atlas mount` target is **`.atlas/<host>/<org>/<repo>/`** (nested directories). The path is the scheme-free atlas-id. Reversible 1:1. HTTPS and scheme-free pointers to the same id share one folder.

`--target <path>` still overrides. Host case follows the id normaliser when that leaf is pinned (until then: lowercase host, preserve org/repo as in the id).

Flatten `--` and kebab encodings are rejected for MVP.

## Alternatives considered

- `.atlas/github.com--org--repo/` — rejected; less readable, extra alphabet.
- `.atlas/github-com-org-repo/` — rejected; lossy.
---
