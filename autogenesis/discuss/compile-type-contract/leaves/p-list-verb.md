---
type: protostar
title: "Inventory is a list verb, not a compile flag or a search query"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: open
kva: forming
growth: true
star_kind: tension
origin: user
sensitivity: internal
description: "General graph list: filter any frontmatter field and optional relation kind. Not type-only. Not ranked. Not limited to 10. Not hung on validate."
relates_to:
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/find-by-type.md
    kind: related
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Pending

Design a generic `atlas list` (name TBD) that prints pages matching field filters. `type=` is one filter, not the product. Do not add `--kva` to compile. Search `type:` stays a discovery constraint.

## Origin

Operator: 0.7.5 compile/list direction makes no sense. Same thesis as p-cli-not-use-case, now with shipped evidence.
