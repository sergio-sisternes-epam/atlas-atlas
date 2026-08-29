---
type: document
title: "Orbit — atlas-id normaliser"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Exact string function from pointer to scheme-free atlas-id. Nested mount path uses this id."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/gap-queue.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-url-normalisation.md
    kind: related
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/decision-mount-nested-path.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## Input

A pointer: MD URL, `atlas://…`, `git@host:org/repo.git`, or already scheme-free `host/org/repo`.

## Proposed function (not pinned)

1. If `atlas://`, drop that scheme only.
2. If `git@host:path`, rewrite to `host/path`.
3. If `https://` / `http://` / `ssh://` / `git://`, parse URL; drop scheme and userinfo.
4. Drop default ports (`:443`, `:80`, `:22`).
5. Drop trailing `/` and trailing `.git`.
6. **Lowercase host only.** Preserve org and repo case (GitHub is case-insensitive on owner/repo but other forges may not be; MVP: preserve path case).
7. Drop a leading `www.` on host.
8. Result: `host/org/repo` (exactly two slashes for GitHub-shaped paths). Extra path after repo is **not** part of the id (that is monorepo `subpath`, next gap).

Examples:

| Pointer | Id |
|---------|-----|
| `https://github.com/Acme/Wiki.git` | `github.com/Acme/Wiki` |
| `git@github.com:Acme/Wiki.git` | `github.com/Acme/Wiki` |
| `atlas://github.com/Acme/Wiki/decisions/x.md` | id `github.com/Acme/Wiki` + in-store path |
| `https://user:pat@github.com/Acme/Wiki` | `github.com/Acme/Wiki` (userinfo dropped) |

Same id → same `.atlas/github.com/Acme/Wiki/` folder.
