---
type: experience
title: "Discussion root — Atlas storage mesh over git"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "discussion_root. Subject and objective locked. Does not move."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/current-reality.md
    kind: related
  - path: autogenesis/discuss/git-mesh/retrofit-from-conversation.md
    kind: records
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-storage-mesh.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-contradictions-closed.md
    kind: related
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: related
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: related
---

## Context

Subject: Atlas storage-mesh composition over git repositories.

Objective: shape a modular knowledge-graph protocol where git is the distributed file-system and overlay, Atlas is the graph connectivity layer, and query stays a separate concern.

This page is `discussion_root`. It does not move.

## What happened

A live conversation explored the three-layer stack (git / APM / atlas), the existing mesh + `atlas://` surface, then the user's storage thesis (id = repo URL, submodule read, worktree write). The thread then agreed to take tensions one at a time and keep a discussion graph. That graph was not maintained until this retrospective `from-conversation` pass.

## Batch still on the hub

Engaged (pages exist):

1. Three-layer stack — `stack-three-layers.md`
2. Current mesh / `atlas://` reality — `current-mesh-reality.md`
3. Scope lock: storage not query — `scope-storage-not-query.md`
4. Git-aware Atlas — `git-aware-atlas.md`
5. Identity = git repo URL — `identity-id-is-repo-url.md`
6. Mount model submodule / worktree — `mount-submodule-worktree.md`
7. Tension 1 URL-as-id — `tension-url-as-id.md`
8. Options A/B/C under that tension
9. Protocol is not identity — `protocol-is-not-identity.md`
10. Branch atlas-auth — `atlas-auth.md` (current_branch)

Unengaged / parked as forming leaves under `leaves/`:

- URL normalisation, alias collision, monorepo id form
- Submodule vs worktree lifecycle
- `.agents/atlas/` location
- Optional-git feature cut
- Atlas package shape, mesh pull verb
- URI fragment, unresolved-id policy
- Auth precedence, protocol choice, helper surface

## Outcome

Graph retrofit completed. Current orbit is the atlas-auth branch, opened after protocol-is-not-identity.
