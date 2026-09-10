---
type: document
title: "Pin — repo mount is .atlas/<encoded-id>/; skill path only names the id"
created: "2026-09-03"
status: settled
kva: alive
reality: current
description: "Rejects a single .atlas file-or-folder per repo. Keeps the living many-store layout. Skill references/atlas is not the checkout."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-no-git-refuse.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-not-store.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
---

## Content

Operator pinned: the active repository keeps **`.atlas/<encoded-id>/`**. One repo may mount many stores. The skill’s `references/atlas` is only a pointer to that id, plus mount-if-missing.

Rejected here:

- One `.atlas` folder or file per repo as the sole submodule, shared by every skill.
- A repo-root `.atlas` pointer file that names ids while mounts live beside it.

This is the same directory layout git-mesh already chose for default mount. What changes is the skill-internal exception: that id is no longer checked out under the skill tree.

### Outcome

KVA alive. Batch on the hub is engaged. Pointer artefact form is still open.
