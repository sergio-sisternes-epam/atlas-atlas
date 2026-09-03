---
type: document
title: "Orbit — monorepo subpath vs atlas-id"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Id stays host/org/repo. Optional mesh subpath for Atlas root inside that repo. Second root in one repo deferred."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-monorepo-id.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-mono-vs-multi.md
    kind: related
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Constraints already pinned

Normaliser id is exactly `host/org/repo`. Mount dir is `.atlas/host/org/repo/` (whole git clone / submodule).

A skill Atlas today lives at `references/atlas` **inside** a larger repo. That is the common monorepo-shaped case: one git unit, Atlas not at repo root.

## Proposed lean (not pinned)

1. **Id does not include subpath.** Two Atlases would not get two ids from one repo in MVP.
2. Mesh row gains optional **`subpath`**. Empty / omitted = Atlas root is the repo root (`SCHEMA.json` / `index.md` there). Typical skill: `subpath: references/atlas`.
3. Compile/query/resolve use `mount_root + subpath` as the Atlas root. In-store paths are relative to that root, not the git root.
4. **MVP: at most one Atlas root per git repo.** A second root in the same clone is deferred (package-shape / multi-atlas gap). Avoids `atlas://github.com/sergio-sisternes-epam/atlas-atlas/page` pointing at two trees.
5. `#` in pointers is **not** used for subpath (next gap is `atlas://` vs Markdown `#`).

`atlas mount github.com/org/skill-repo` still clones the repo; mesh says where the OKF root sits inside it.
