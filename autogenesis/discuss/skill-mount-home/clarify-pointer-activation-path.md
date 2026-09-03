---
type: document
title: "Clarify — pointer is an activation-path markdown file"
created: "2026-09-03"
status: in-discussion
kva: alive
reality: current
description: "Operator: default markdown under references/atlas, harness activation path. Confirm mount, then search. May collide with file-not-tree if that path is a directory."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/discuss/skill-mount-home/pin-pointer-file.md
    kind: follows
  - path: autogenesis/discuss/skill-mount-home/p-pointer-artefact.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/hub.md
    kind: derived_from
---

## Content

Operator clarification, not yet a replacement pin:

The pointer is a default markdown file in `references/atlas`. It is an **activation path**. It instructs the agent to (1) confirm the target Atlas is mounted, (2) use that mount to search. The harness keeps its usual `references/` route. The store is not that path.

Two counters, not yet 1-by-1:

1. “In `references/atlas`” as a directory reopens a writeable tree on a global skill. The last pin was file, not tree, and `--root` must fail. The leak-safe reading is `references/atlas.md` (or a file whose path is not a directory).
2. The objective is write-home. Search-only instructions leave remember/compile free to write into the skill tree. The activation path has to name mount-if-missing **and** `--root` of the mount for query and persist.

### Outcome

KVA alive. Current branch until we pin which path shape and whether write is in the activation text.
