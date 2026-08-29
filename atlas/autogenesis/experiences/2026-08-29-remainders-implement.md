---
type: experience
title: "Remainders implement — wiring and hygiene"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-remainders
status: done
kva: alive
description: "mount reads auth.json; jsonschema declared; headless git guard; some discuss pages superseded."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-remainders.md
    kind: implements
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-remainders.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-live-auth-login.md
    kind: related
---

## Passed

- `lookup(host, org)` on `auth.json`; mount sets ssh from recorded backend.
- `apm.yml` python dep `jsonschema>=4.0` and `scripts/requirements.txt`.
- Missing jsonschema is a named error string.
- `has_git()`; mount and `auth login` refuse without git.
- Seven early discuss drafts marked `superseded`.

## Not in this slice

Live `atlas auth login` against GitHub. Task `t-auth-backends` remains reopened / card blocked.

## Changed files

- `scripts/atlas_cli/core/authstore.py` `gitops.py` `meshfile.py`
- `scripts/atlas_cli/commands/mount.py` `authcmd.py`
- `apm.yml` `scripts/requirements.txt`
---
