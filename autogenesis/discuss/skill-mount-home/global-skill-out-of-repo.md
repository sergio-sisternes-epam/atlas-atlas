---
type: document
title: "Claim — global skill mounts put Atlas writes outside the repository"
created: "2026-09-03"
status: in-discussion
kva: alive
reality: alternative
description: "Operator concern: skill-internal references/atlas is session-controlled only when the skill lives in the repo. Proposed repair: repo-owned .atlas mount; skill path is a pointer and mount-if-missing."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: related
  - path: decisions/package-shapes.md
    kind: related
---

## Content

Two install shapes for the same skill:

1. Repository-level. The skill tree, including `references/atlas`, sits inside the session worktree. Writes are ordinary repo changes.
2. Global. The skill tree sits outside the repo (for example `~/.agents/skills/<name>`). Writes to `references/atlas` never appear in the session. They are also easy to leave uncommitted on the mount.

Operator proposal: stop treating the skill path as the write-home. Put the mount in the active repository as `.atlas` (stated as a file; the living convention is a directory `.atlas/<encoded-id>/`). The skill’s `references/atlas` only points at that mount, instructs the agent to mount if missing, then use it.

This branch is **alternative**. Current reality is still git-mesh: default mount `.atlas/<encoded-id>/` for corpora that are not skill-internal; skill process memory stays at `<skill>/references/atlas` when explicitly that skill’s own atlas-id.

### Probe (this session)

Atlas product worktree had `references/atlas` in `.gitmodules` and `atlas-mesh.json`, but the submodule was empty until init. The discuss and atlas skills were already answering from their global mounts. After init, repo submodule and skill mount share `538a5fe`, and the skill mount is dirty. That is the failure the claim names, observed rather than guessed.

### Outcome

KVA alive as an alternative branch. Not yet fit to replace the skill-internal exception. Next: take the hub batch 1-by-1.
