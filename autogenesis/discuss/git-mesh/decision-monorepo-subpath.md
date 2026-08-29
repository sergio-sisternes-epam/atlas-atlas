---
type: decision
title: "One Atlas root per git repo; optional mesh subpath"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Id stays host/org/repo. Mesh subpath names the OKF root inside the clone. Second root in one repo is deferred."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/monorepo-subpath.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/leaves/p-monorepo-id.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-mono-vs-multi.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Decision

1. Atlas-id remains `host/org/repo` from the normaliser. Subpath is not part of the id.
2. Mesh row may carry optional **`subpath`**. Empty means the OKF root is the repository root. A skill store typically uses `references/atlas`.
3. Compile, query, and resolve treat `mount_root + subpath` as the Atlas root. In-store page paths are relative to that root.
4. MVP allows **at most one Atlas root per git repository**. A second root in the same clone is deferred.
5. Markdown `#` is not used to encode subpath.

## Alternatives considered

- Put subpath in the id — rejected; breaks the two-segment normaliser.
- Several roots per clone in MVP — rejected; `atlas://host/org/repo/page` would be ambiguous.
- `#fragment` as subpath — rejected here; that is the next gap (`atlas://` vs Markdown `#`).
---
