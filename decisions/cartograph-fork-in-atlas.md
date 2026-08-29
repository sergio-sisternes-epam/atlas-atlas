---
type: decision
title: "Cartograph lives only in the Atlas skill"
created: 2026-08-23
status: accepted
work_id: okf-wiki-karpathy-realign-simplify-compose-migrate-v1
description: "The star-map viewer is an Atlas-owned fork of okf-wiki graph-viewer. Hosts import it; they must not keep a second Atlas source tree."
relates_to:
  - path: work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md
    kind: implements
  - path: experiences/2026-08-23-cartograph-atlas-port.md
    kind: records
  - path: decisions/atlas-name.md
    kind: related
---

## Decision

Cartograph source lives only under `atlas/addons/cartograph/`. It is a fork of `okf-wiki/addons/graph-viewer`, not a shared package. Grok Build hosts **import** `@atlas/cartograph`; they do not duplicate Atlas or viewer code.

## Rationale

A host copy drifts from the skill. Atlas owns `SCHEMA.json`, free layout, `relates_to`, and `atlas://`. okf-wiki's viewer remains the legacy wiki sky.

## Alternatives considered

Keeping the viewer only in okf-wiki and adapting at the host. Rejected: Atlas stores would keep looking like wikis.

Copying Cartograph into each Build app. Rejected: two sources of truth.

## Consequences

Strip with `addons/cartograph/STRIP.md`. `atlas view` is Build-only. Compile, search, migrate, and promote do not depend on the add-on.

## Related

- **implements:** [Atlas reboot of okf-wiki](../work/okf-wiki-karpathy-realign-simplify-compose-migrate-v1.md)
- **records:** [Cartograph ported into Atlas](../experiences/2026-08-23-cartograph-atlas-port.md)
- **related:** [Successor name is Atlas](atlas-name.md)
