---
type: document
title: "Implications — git-mesh after dropping the skill-internal store"
created: "2026-09-03"
status: in-discussion
kva: alive
reality: current
description: "What git-mesh was, what clause 3 did, and what changes if mounts only live under the active repo’s .atlas/."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-mount-dot-atlas-only.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/exit-skill-internal-store.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/p-package-shapes-mount.md
    kind: related
---

## Content

Git-mesh is the Atlas storage conversation: git is the overlay, identity is `host/org/repo`, default mount is `.atlas/<encoded-id>/` (submodule if the parent is git), and `atlas-mesh.json` lists what this project has mounted. Query stayed a separate concern.

The exception, clause 3, was: a skill’s **own** process memory could still be checked out at `<skill>/references/atlas`. Other corpora already belonged under `.atlas/`. That exception is what we superseded.

### What now follows

- Write-home for atlas-atlas, discuss-atlas, and any subject Atlas is the **active git repo**, at `.atlas/<encoded-id>/`.
- A globally installed skill must not receive those writes. Its only Atlas artefact is `references/atlas.md` (mount-if-missing, then query and persist with `--root` on the mount).
- `atlas-mesh.json` in the project should name those `.atlas/...` paths, not `references/atlas`.
- No git repository: refuse to persist. Headless query of an already-present mount is unpinned.
- `--target` remains the escape hatch. `--target-skill` stays absent.

### Not yet moved

- `decisions/package-shapes.md` still says this skill mounts atlas-atlas at `references/atlas`.
- Discuss and Atlas Enter cards still say `--target references/atlas`.
- This session’s own persist used the **old** workspace submodule at `references/atlas`, because that is what `.gitmodules` already had. The new pin is not implemented.

## Outcome

KVA alive. Picture only. Not implement.
