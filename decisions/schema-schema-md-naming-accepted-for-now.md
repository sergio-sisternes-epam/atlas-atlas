---
type: decision
title: "schema.schema.md naming accepted for now"
created: 2026-10-05
status: accepted
origin: user
sensitivity: internal
description: "Accept default folder schema filename schema.schema.md for now; do not rename to index.schema.md."
relates_to:
  - path: autogenesis/work/2026-10-05-atlas-optimise-target-layers.md
    kind: related
---

## Decision

Sergio 2026-10-05 accepts default folder schema filename `schema.schema.md` for now but dislikes the doubled name; revisit later for a clearer handle. Keep migrate bootstrap as `schema.schema.md`; do not rename to `index.schema.md` (index.md stays OKF reserved).

## Rationale

Migrate bootstrap already uses `schema.schema.md`. Renaming to `index.schema.md` would collide with OKF's reserved `index.md` handle. Accept the doubled name temporarily; choose a clearer filename later without changing the migrate default yet.

## Alternatives considered

- Rename migrate bootstrap to `index.schema.md` — rejected (`index.md` stays OKF reserved).
- Change the default immediately to another handle — deferred; revisit later for a clearer name.

## Consequences

- Migrate bootstrap continues to write `schema.schema.md`.
- Agents should not invent a rename to `index.schema.md`.
- A clearer filename may be chosen later; that is a separate decision.
