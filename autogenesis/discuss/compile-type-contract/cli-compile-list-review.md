---
type: document
title: "Review — 0.7.5 compile and list surface is opportunistic"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: in-discussion
kva: alive
reality: current
description: "Shipped compile --list-type is a discovery flag hung on the health gate. It short-circuits validate. Search type: is a second, ranked, limited inventory. Not general graph tools."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-cli-not-use-case.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/find-by-type.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/approach.md
    kind: follows
  - path: experiences/2026-08-27-implement-atlas-compile-type-contract.md
    kind: backed_by
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Claim

Atlas 0.7.5 solved a real discovery miss (search ranked *mentions* of a type) by bolting inventory onto `compile`. That was biased to this store’s repair loop and left the CLI pointing the wrong way.

## What shipped (facts)

Commands: `init`, `compile` (= `validate`), `search`, `migrate`, `promote`, `view`.

There is **no** `list` verb.

`compile` and `validate` both take `--list-type`. In `commands/validate.py`, if that flag is set the function prints matching pages and **`return 0`**. The health payload, warning list, and exit 1/2 mapping never run.

`search "type:<name>"` filters frontmatter type, then **scores leftover tokens against body**. A type-only query reuses the type name as a scoring token. Default `--limit 5` on some calls, 10 otherwise — inventory is truncated and ranked, not listed.

`--list-type` output is path + title only. No `kva`, `work_id`, `growth`, relation kinds.

## Why this is opportunistic

Pin U said: compile lists accidents; search also filters type. That was a *repair-session* need: “show me the 27 protostars compile should have named.” The cheapest hook was a flag on the command already in hand.

The parked star `p-cli-not-use-case` already warned: do not add `--kva` / `--work-id` to compile because we wanted a backlog. 0.7.5 took the first step of that slide.

Compile’s job in the settled approach is a **two-layer gate**. Listing is a **graph read**. Mixing them means:

1. Agents cannot trust `compile --list-type` as a gate (always 0).
2. Agents cannot use compile as “print the warning list and also filter type” — listing replaces the gate.
3. A second inventory exists on search with different semantics (rank, limit, body score).
4. The next habit (`--kva forming`, `--work-id …`) has an obvious home on compile, which is the wrong home.

## What a coherent split looks like (not a plan)

| Verb | Job |
|------|-----|
| `compile` / `validate` | Gate only. Exit 0/1/2. JSON issues. No inventory flags. |
| `list` (or `query` graph primitive) | Deterministic page inventory. Filter any frontmatter field; optional relation kind. Unbounded or explicit `--limit`. Exit 0 if the list ran. |
| `search` | Discovery. Ranked. `type:` as a *constraint* is fine; it is not `list`. |

This store’s “what should I work on?” stays an agent recipe over `list` + edges, not more compile flags.

## Stale graph note

`current-reality.md` still describes pre-0.7.5 compile (no page-contract, 27 green protostars). Product reality moved; that page did not. Review of CLI shape should not treat it as locked shipped behaviour.

## Provenance

Operator ask 2026-08-27: review atlas CLI especially compile and list; 0.7.5 felt biased and opportunistic. Probe: `cli.py` 0.7.5, `validate.py` `_list_type` + early `return 0`, `search.py` `_split_type_filter`.
