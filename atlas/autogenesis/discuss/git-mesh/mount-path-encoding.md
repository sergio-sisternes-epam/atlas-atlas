---
type: document
title: "Orbit — how mount encodes atlas-id as a directory"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Next gap after auth. Default target .atlas/<encoded-id>/. Slashes need a reversible encoding."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-kebab-encoding.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The act

`atlas mount` default target is `.atlas/<encoded-id>/`. Id is `github.com/org/repo` (slashes). Encoding must be reversible so mesh id ↔ folder is 1:1. Same id via https pointer or scheme-free pointer shares one folder (id is scheme-free).

## Candidates

| Encoding | Example | |
|----------|---------|--|
| Nested dirs | `.atlas/github.com/org/repo/` | readable; more mkdir |
| `--` flatten | `.atlas/github.com--org--repo/` | one directory name |
| Kebab all | `.atlas/github-com-org-repo/` | lossy if org/repo contain `--` or case |

Proposed lean (not pinned): **nested `host/org/repo` under `.atlas/`**. Reversible, matches the id, no extra alphabet. `--target` still wins when set.
