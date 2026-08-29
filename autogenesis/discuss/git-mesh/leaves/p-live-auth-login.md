---
type: protostar
title: "Prove atlas auth login against a real gh/PAT environment"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-gap-close
status: open
kva: forming
reality: current
growth: true
star_kind: action
description: "This sandbox has no GitHub credentials. Login persist is unproven live."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: autogenesis/experiences/2026-08-29-gap-close-honest.md
    kind: derived_from
  - path: work/2026-08-29-atlas-storage-mesh-gap-close.md
    kind: implements
---

## Growth path

On a machine with `gh` logged in or `GITHUB_TOKEN`, run `atlas auth login --host github.com` and confirm `auth.json` records backend without a token field.

## Open question

Should missing credentials on a public mount stay a soft fallback forever? Current code tries git anyway.
---
