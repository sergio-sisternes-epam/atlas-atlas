---
type: document
title: "Discussion hub — skill Atlas write-home when the skill is global"
created: "2026-09-03"
status: in-discussion
kva: alive
reality: current
description: "discussion_root. Candidate subject and objective locked here until the operator adjusts them."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: related
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: related
  - path: decisions/package-shapes.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/pin-objective.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-both-write-homes.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-not-store.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-no-git-refuse.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/pin-dot-atlas-encoded-id.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/current-reality.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-file.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/p-enter-card-shape.md
    kind: follows
---

## Content

Subject: where a skill’s Atlas is mounted, and therefore written, when that skill is installed globally versus inside the active repository.

Objective: keep Atlas writes under the active repository’s control, so a globally installed skill cannot become an untracked write-home. Pinned on pin-objective.md.

This page is `discussion_root`. It does not move.

This is a new orbit. It does not silently replace git-mesh. The settled pin remains: default `atlas mount` target is `.atlas/<encoded-id>/`, and `<skill>/references/atlas` is that skill’s internal memory. The operator’s concern reopens whether that internal-memory exception still holds once skills are routinely global.

### What happened

Operator invoked discuss from an Atlas product session. Query of discuss-atlas found `next-step/mount-not-clone.md` (Enter must mount, not a sibling clone) and `wire/q2-graph-home.md` (write-home is the subject Atlas). Query of atlas-atlas found the git-mesh target-path decision and the skill-internal-memory lean.

A cheap probe in this session: workspace `references/atlas` was an uninitialised submodule; the global skill mount at `~/.agents/skills/atlas/references/atlas` was the live tree. After init, both checkouts share SHA `538a5fe`, yet the skill mount has extra uncommitted pages the repo submodule does not. Writes to skill-internal memory already fall outside session control.

### Batch on the hub (not yet 1-by-1)

1. Confirm subject and objective — engaged: pin-objective.md
2. Which write-home we are moving — engaged: pin-both-write-homes.md (both)
3. Counter — git-mesh skill-internal exception — engaged via pin-both-write-homes.md (reopen).
4. Counter — path-as-signal — engaged: pin-pointer-not-store.md (signal dies; pointer plus mount-if-missing).
5. No active git repository — engaged: pin-no-git-refuse.md (refuse to persist).
6. `.atlas` shape — engaged: pin-dot-atlas-encoded-id.md (`.atlas/<encoded-id>/`; skill path names the id).

### Outcome

KVA alive. Init and migrate stamp the exact five-field Atlas mount activation
card in the consuming skill's main SKILL.md. The card points to Atlas's mount
module, identifies the store by `atlas_id`, and requires no consuming-skill
path-registry row. Current branch is p-enter-card-shape.md.
