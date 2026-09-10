---
type: decision
title: "Atlas catalog is atlas-marketplace with name atlas"
created: 2026-09-10
status: accepted
work_id: 2026-09-10-atlas-marketplace-rename
description: "sergio-sisternes-epam/atlas-marketplace is THE marketplace for Atlas. Catalog identity name is atlas."
origin: derived
sensitivity: internal
kva: alive
relates_to:
  - path: work/2026-09-10-atlas-marketplace-rename.md
    kind: implements
  - path: experiences/2026-09-10-atlas-marketplace-rename.md
    kind: records
  - path: lessons/2026-09-10-register-marketplace-as-atlas.md
    kind: related
  - path: recipes/republish-atlas-marketplace-deps.md
    kind: related
  - path: experiences/2026-09-10-release-atlas-0.11.0.md
    kind: follows
---

## Decision

`sergio-sisternes-epam/atlas-marketplace` is **the marketplace for all things
Atlas**. GitHub renamed it from `sergio-sisternes-epam/apm-marketplace`.
Catalog identity `name` is `atlas` (marketplace identity PR 14).

## Rationale

The repo slug `atlas-marketplace` names the host. The catalog consumers address
is the short identity `atlas`, so install specs stay `pkg@atlas` rather than
tracking the GitHub org or the long repo name.

## Alternatives considered

- Keep catalog name `sergio-sisternes-epam` (old local registration) — rejected;
  that name was unregistered.
- Use catalog name `atlas-marketplace` (APM `add` default from repo name) —
  rejected; identity is `atlas`.
- Install as `pkg@sergio-sisternes-epam` or `pkg@atlas-marketplace` — rejected.

## Consequences

Consumers must pass `--name atlas` on `apm marketplace add`. Do not re-add
`sergio-sisternes-epam/apm-marketplace` or reuse local name
`sergio-sisternes-epam`. Current install form is `pkg@atlas`. Pin catalog
`ref` to peeled commits, not tag objects; never move tags.
