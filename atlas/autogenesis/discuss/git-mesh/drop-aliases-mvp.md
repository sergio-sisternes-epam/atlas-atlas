---
type: decision
title: "MVP: no aliases — atlas-id must locate the server"
created: 2026-08-26
work_id: 2026-08-26-atlas-modular-graph-protocol
status: settled
kva: alive
reality: current
description: "Drop cute aliases. Scheme-free host/path is the only id. Migration of repo/org is deferred."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/option-c-derived-short.md
    kind: related
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: counters
  - path: autogenesis/discuss/git-mesh/leaves/p-alias-collision.md
    kind: related
  - path: autogenesis/discuss/git-mesh/exit-aliases-dropped.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Decision

MVP Atlas identity has no short aliases (`skill-memory`, and the like).

The atlas-id is a scheme-free host/path that points at the serving git host, for example `github.com/org/repo`. Protocol stays out of the id.

## Rationale

An alias hides where the knowledge lives. A host/path id is resolvable: you can see the server, the org, and the repo. That is the point of moving off local nicknames.

## Alternatives considered

- Optional aliases unique per compiled mesh — rejected for MVP. Collision rules do not fix the “where is this?” problem.
- Full URL including scheme — already rejected on protocol-is-not-identity.

## Consequences

- `p-alias-collision` is terminated (exit: `exit-aliases-dropped.md`).
- Repo or organisation migration (rename, transfer, host move) is a known tension and is **out of MVP**. Parked as a forming protostar.
- `atlas://` in MVP uses the host/path id, not a nickname.
