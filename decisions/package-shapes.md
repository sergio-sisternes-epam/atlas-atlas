---
type: decision
title: "Two package shapes; this skill mounts the dedicated store at references/atlas"
created: 2026-08-30
status: settled
work_id: 2026-08-29-atlas-storage-mesh-mvp
description: "Embedded vs dedicated. Atlas skill uses dedicated atlas-atlas mounted at references/atlas; OKF root is git root."
origin: derived
sensitivity: internal
kva: alive
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: follows
  - path: work/mesh-mvp/f-package-shapes.md
    kind: related
  - path: recipes/git-update-mounted-store.md
    kind: related
---

## Decision

MVP allows exactly two shapes:

1. **Embedded.** Git unit is the skill or project repo. Mesh `subpath` is the OKF folder (often `references/atlas`).
2. **Dedicated.** Git unit is the Atlas. `subpath` is empty (OKF root = git root).

This skill’s canonical store is dedicated (`github.com/sergio-sisternes-epam/atlas-atlas`) and is mounted at `references/atlas`. Compile/query root is `references/atlas` (`subpath` empty).

APM may copy files. Mesh membership still requires `atlas mount` of a git identity.

## Rationale

Process memory must be a git identity so mount, branch, and PR work. Mounting at `references/atlas` with OKF at git root means resolve path = compile path.

## Alternatives considered

- Author pages in the skill tree at `references/atlas` — rejected; store lives in atlas-atlas.
- Default overlay only under `.atlas/host/org/repo` — rejected for this skill’s internal memory; `--target references/atlas` is the pin.
- A third APM-only OKF product without git — rejected.

## Consequences

Agents compile with `--root references/atlas`. Updates are git commits inside the mount, then a parent gitlink bump if the mount is a submodule. There is no `atlas sync`.
