---
type: document
title: "How host/path id joins credentials, checkout, and local files"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Working model, not a pin. Mesh is the join table between atlas-id, auth scope, mount, and in-store path."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/leaves/p-url-normalisation.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: related
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Three user questions on T1, after the no-alias pin:

1. Which credentials apply to check out this Atlas?
2. How does checkout work?
3. How does a local file map to a remote file?

Working model (forming):

Parse atlas-id `host/owner/repo` (scheme-free). That is enough to key APM-like auth: host class + org = owner. Reconstruct a clone URL only at mount time (HTTPS default; SSH if transport says so).

Mesh entry is the join row: `id`, local `root`, `access`, optional `subpath`, contribution. Local checkout lives under `.agents/atlas/<encoded-id>/`. In-store path is relative to that Atlas root (`SCHEMA.json` / `index.md`). Cross-root edges stay `atlas://<id>/<in-store-path>`.

Reverse map: file on disk → walk up to Atlas root → mesh row → id. Not guess from git remotes ad hoc.

Open: filesystem encoding of `host/owner/repo` (slashes), exact submodule vs worktree steps, whether `subpath` is in the id.
