---
type: work
title: "Atlas marketplace rename and catalog republish"
created: "2026-09-10"
work_id: "2026-09-10-atlas-marketplace-rename"
status: done
description: "GitHub repo apm-marketplace renamed to atlas-marketplace; catalog identity name is atlas; dependents republished and pinned."
origin: derived
sensitivity: internal
relates_to:
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: records
  - path: decisions/atlas-marketplace-identity.md
    kind: related
  - path: lessons/2026-09-10-register-marketplace-as-atlas.md
    kind: related
  - path: lessons/2026-09-10-apm-lockfile-marketplace-git-coords.md
    kind: related
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
  - path: experiences/2026-09-10-release-atlas-0.11.0.md
    kind: follows
  - path: work/2026-09-10-atlas-store-modes.md
    kind: follows
---

## Scope

Record the completed GitHub marketplace rename from
`sergio-sisternes-epam/apm-marketplace` to
`sergio-sisternes-epam/atlas-marketplace`, the catalog identity `name: atlas`,
consumer registration and install forms, the dependent republish order, current
peeled catalog pins, and APM 0.30.0 lockfile / frozen-audit behaviour.

## Status

Opened and closed 2026-09-10. Rename and republish already happened; this hub
clusters durable memory.

## Outcomes

- Decision: `sergio-sisternes-epam/atlas-marketplace` is the Atlas catalog; identity `name` is `atlas`.
- Lesson: register with `--name atlas`; install `pkg@atlas`; do not re-add `apm-marketplace`.
- Lesson: APM 0.30.0 lockfiles store git coordinates; frozen audit expects `_marketplace/atlas/<pkg>`.
- Recipe: republish atlas 0.11.2, then discuss 0.3.10, then autogenesis 0.4.3.
