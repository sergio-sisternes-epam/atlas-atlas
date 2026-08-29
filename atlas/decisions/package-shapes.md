---
type: decision
title: "Two package shapes; this skill mounts the dedicated store at references/atlas"
created: 2026-08-30
status: settled
work_id: 2026-08-29-atlas-storage-mesh-mvp
description: "Embedded vs dedicated. Atlas skill uses dedicated atlas-atlas mounted as the references/atlas submodule; OKF root is nested atlas/."
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
2. **Dedicated.** Git unit is the Atlas. `subpath` is empty, or a nested OKF root such as `atlas/`.

This skill’s canonical store is dedicated (`github.com/sergio-sisternes-epam/atlas-atlas`) and is mounted as the `references/atlas` submodule. Compile/query root is `references/atlas/atlas` (`subpath: atlas`).

APM may copy files. Mesh membership still requires `atlas mount` of a git identity.

## Rationale

Process memory must be a git identity so mount, branch, and PR work. Nesting the dedicated repo under `references/atlas` keeps Cartograph and agents looking at the old skill-memory slot without flattening `atlas/` to git root.

## Alternatives considered

- Author pages in the skill tree at `references/atlas` — rejected; store lives in atlas-atlas.
- Default overlay only under `.atlas/host/org/repo` — rejected for this skill’s internal memory; `--target references/atlas` is the pin.
- A third APM-only OKF product without git — rejected.

## Consequences

Agents compile with `--root references/atlas/atlas`. Updates are git commits inside the submodule, then a parent gitlink bump. There is no `atlas sync`.
