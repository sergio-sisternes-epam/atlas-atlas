---
type: document
title: "Contradiction 6 — git optional vs git is the overlay"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Can Atlas work without git? Mount/write assume git. Reader-only degrade is the leftover."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-optional-git-cut.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The fight

Side A (early): git is optional; Atlas still works on a local folder; most mesh features are limited.

Side B (later): git **is** the overlay. `atlas mount` materialises a git tree. Writes leave through commit/PR. No second overlay.

Both cannot describe the same product mode.

## Proposed resolution (not pinned)

Git is **required** for mount, auth-translation to a remote, and publish.

Without git, Atlas may still **read** an already-present local OKF tree (`compile`, `query` on `--target` / `references/atlas`). That is a degraded reader, not a peer mesh member.

No “optional git writer.” No fake overlay when git is missing.
