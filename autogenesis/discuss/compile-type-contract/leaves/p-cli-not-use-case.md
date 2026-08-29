---
type: protostar
title: "Atlas CLI must stay general graph tools, not this store’s workflow"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: open
kva: forming
growth: true
star_kind: tension
origin: user
sensitivity: internal
description: "list-type plus kva/work filters would bake our protostar focus habit into the product. Next session: design generic graph queries, not more compile flags for this use case."
relates_to:
  - path: autogenesis/discuss/compile-type-contract/atlas-orders-the-graph.md
    kind: derived_from
  - path: experiences/2026-08-27-implement-atlas-compile-type-contract.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Pending

Do not add `--kva`, `--work-id`, or other focus flags to compile because we wanted a protostar backlog. Atlas CLI should expose general graph operations (list by any frontmatter field, filter by any relation kind, walk a work cluster). This store’s “what should I work on?” is an agent recipe on top of those primitives, not a special command.

## Origin

After 0.7.5, `--list-type protostar` fixed discovery. Focusing still needed `kva` + `growth` + `work_id` grouping by hand. The temptation was another compile flag for that exact habit. Operator: the CLI is sliding toward our use case; park it and widen later.
