---
type: experience
title: "Gap-close implement — what actually passed"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-gap-close
status: done
kva: alive
description: "Public mount smoke passed. Auth persist code works. Live gh login did not run here (no credentials)."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-gap-close.md
    kind: implements
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-gap-close.md
    kind: derived_from
  - path: autogenesis/experiences/2026-08-29-overclaim-mesh-mvp.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-live-auth-login.md
    kind: related
---

## Passed

- JSON Schema runtime (`jsonschema`) rejects a `token` field on mesh rows.
- `atlas query` is a real command, alias of `search`.
- `auth.json` write/list/remove in a temp `XDG_CONFIG_HOME` (no PAT stored).
- `atlas mount github.com/octocat/Hello-World` in an empty git dir: exit 0, row in `atlas-mesh.json`, tree at `.atlas/github.com/octocat/Hello-World`, ref `master`.
- Public clone no longer requires prior `atlas auth` (git can fetch public HTTPS).

## Failed / not run

- `atlas auth login --host github.com` in this session: no `gh` token and no TTY login. Exit 2. Persist-on-login was therefore not proven against GitHub, only against the store helpers.

## Changed files

- `scripts/atlas_cli/core/authstore.py` `meshfile.py` `commands/authcmd.py` `commands/mount.py` `cli.py`
---
