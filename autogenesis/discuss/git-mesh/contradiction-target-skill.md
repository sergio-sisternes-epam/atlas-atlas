---
type: document
title: "Contradiction 5 — --target-skill vs path-as-signal"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "May atlas mount write into a skill’s references/atlas? Path means internal memory."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: related
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-target-skill.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-skill-knowledge-mesh.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The fight

Side A: `references/atlas` is a **signal** — this skill’s internal memory. One authored root per skill. Other corpora join via mesh + `.atlas/`. `--target-skill` that writes a third-party tree into that folder destroys the signal.

Side B: `--target-skill foo` is convenient sugar: mount into `foo/references/atlas` so the skill “has” the knowledge.

Both cannot be the default mount path.

## Proposed resolution (not pinned)

- Default mount target: **`.atlas/<kebab>/`**.
- `--target <path>` is a generic path override. No special `--target-skill`.
- A skill’s `references/atlas` is **authored** (or `atlas mount` of *that skill’s own* atlas-id into that path, explicitly).
- Extra Atlases a skill uses are mesh members, not extra folders under `references/`.
- Other skills may still *write pages* into a skill Atlas they have mounted (Autogenesis pattern). That is writers, not “install N trees into one folder.”
