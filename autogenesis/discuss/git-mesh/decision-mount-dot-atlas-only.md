---
type: decision
title: "Mount is .atlas/<encoded-id>/; skill path is activation-path only"
created: "2026-09-03"
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Successor to decision-target-path. No store under the skill tree. references/atlas.md mounts and read/writes the repo .atlas mount."
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/current-reality.md
    kind: derived_from
  - path: autogenesis/discuss/skill-mount-home/pin-activation-covers-write.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-atlas-md.md
    kind: related
---

## Decision

1. Default `atlas mount` target is **`.atlas/<encoded-id>/`** in the active git repository.
2. The only override is **`--target <path>`**. There is no `--target-skill`.
3. Do **not** mount at `<skill>/references/atlas`. That path is not a store. The skill ships **`references/atlas.md`**: confirm the target Atlas is mounted (mount-if-missing), then query and persist with `--root` on that mount.
4. Every corpus the skill uses, including that skill’s own atlas-id, is a mesh member under `.atlas/` (or another `--target`), not a tree under `references/`.
5. Other skills may write **pages** into a skill Atlas they have mounted in the active repo. That does not license stacking N roots in one folder.

No git repository: refuse to persist. No fallback into the skill tree.

## Rationale

A globally installed skill made `<skill>/references/atlas` an untracked write-home. The August path-as-signal lean does not survive that install shape. Git remains the overlay. The harness still enters through `references/`, via a markdown activation path rather than a nested store.

## Alternatives considered

- Keep skill-internal memory at `references/atlas` — rejected; global skills leak writes.
- Directory stub at `references/atlas/` — rejected; still writeable.
- Search-only activation path — rejected; persist must use the mount too.

## Consequences

`decision-target-path.md` is superseded. git-mesh current reality follows this page. Not implement.
