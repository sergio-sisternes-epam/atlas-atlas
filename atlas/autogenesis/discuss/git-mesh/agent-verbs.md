---
type: document
title: "Orbit — agent-facing Atlas verbs"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Inventory of verbs pinned across this constellation. Git covers update and publish."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/decision-package-shape-mvp.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-atlas-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Proposed inventory (not pinned as a set until you accept)

Atlas:

- `init` — create a local Atlas (SCHEMA, index) in a folder
- `auth login|list|logout` — alias for a git host
- `mount <pointer>` — first materialise; submodule if parent is git
- `resolve <pointer>` — id → mount root; page URI → file
- `query` — search a mounted (or local) tree; skip unmounted ids
- `compile` — validate the store; warn on unknown `atlas://`

Git, in the directory `resolve <id>` returned:

- fetch / pull / checkout / commit / push / PR

Explicitly not Atlas verbs in MVP: `install`, `checkout`, `sync`, `--target-skill`.

Headless: `compile` and `query` (and edit-in-place) only.
---
