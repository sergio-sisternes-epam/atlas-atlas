---
type: experience
title: "2026-08-30 first write into atlas-atlas via the references/atlas submodule"
created: 2026-08-30
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: raw
description: "Moved skill references/mesh operator notes into the dedicated store. First knowledge commit through the submodule."
origin: internal
sensitivity: internal
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: decisions/package-shapes.md
    kind: records
  - path: recipes/git-update-mounted-store.md
    kind: records
  - path: recipes/capabilities-by-git-mode.md
    kind: records
---

## Context

After GitHub import, atlas-atlas was mounted at `references/atlas` as a submodule. Skill package still had `references/mesh/` operator notes (package shapes, git modes, git update) that read as knowledge, not path modules.

## What happened

Those notes were rewritten as OKF pages under this store (`decisions/package-shapes.md`, `recipes/`). Compile ran against `references/atlas/atlas`. The write is a commit **inside** the submodule (atlas-atlas), then a parent gitlink bump. There is no `atlas sync`.

## Outcome

Skill `references/mesh/` removed. Store gained `recipes/` plus the package-shapes decision. Submodule workflow: edit under `references/atlas`, compile `--root references/atlas/atlas`, `git commit` in the submodule, `git add references/atlas` in the skill repo.
