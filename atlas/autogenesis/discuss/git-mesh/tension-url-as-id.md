---
type: document
title: "Tension 1 — URL-as-id ergonomics"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "Tension 1 under the identity thesis. Options A/B/C plus protocol-is-not-identity. current_branch moved to atlas-auth."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/option-b-short-primary.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/option-c-derived-short.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

Making the primary atlas-id a full git URL gives uniqueness and provenance, but produces noisy references such as `atlas://https://github.com/org/my-atlas/path/to/page.md`.

Scheme-free host/path is the current lean. Aliases dropped for MVP (`drop-aliases-mvp.md`).

Open questions still on this branch:

- Exact host/path normalisation
- Monorepo scoping (`id#subpath` vs a `subpath` field)

Parked: repo/org migration (`leaves/p-repo-org-migration.md`). Auth is a separate branch.
