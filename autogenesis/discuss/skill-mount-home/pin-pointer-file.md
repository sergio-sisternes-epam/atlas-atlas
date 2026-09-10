---
type: document
title: "Pin — pointer is a file, not a tree; --root on it must fail"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "Skill pointer names the atlas-id in a file. A directory at references/atlas is forbidden because a global install would still be writeable."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/p-pointer-artefact.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-not-store.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/current-reality.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: related
---

## Content

Operator pinned: the skill pointer is **a file, not a tree**. `--root references/atlas` must fail. The file names the atlas-id. Mount-if-missing then targets `.atlas/<encoded-id>/` in the active git repository.

Rejected here:

- A directory stub at `references/atlas` (still writeable when the skill is global).
- Repo `atlas-mesh.json` as the only pointer (that drops the skill path).

Working default, not a separate pin: keep the historical path as a **file** named `references/atlas` so old Enter cards still find an artefact, and compile/search refuse it as a root. Exact filename can move later if the CLI cannot take a file at that path.

### Outcome

KVA alive. p-pointer-artefact.md is answered. Current reality should absorb this pin.
