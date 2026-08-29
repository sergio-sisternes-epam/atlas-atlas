---
type: plan
title: "Plan — compile focus lenses (--type, --path)"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-focus-lenses
status: done
description: "Replace compile --list-type dump with a real focused gate: --type and --path filter the page walk; store checks always run; print issues plus matching paths; hard-cut --list-type."
origin: derived
sensitivity: internal
change_class: new-surface
kva: forming
stage: design
plan_path: autogenesis/plans/2026-08-27-atlas-compile-focus-lenses.md
relates_to:
  - path: work/2026-08-27-atlas-compile-focus-lenses.md
    kind: implements
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: follows
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/q-enough-to-design.md
    kind: derived_from
---

## Intent

Make `atlas compile` / `validate` a single health gate that can be aimed at a slice of the store. 0.7.5 `--list-type` printed paths and exited 0. That was a listing hung on the gate. Replace it with lenses.

## Change-class

`new-surface`

## Pinned decisions

From discussion Q1–Q9 plus challenge:

1. No separate `list` verb. Search stays the GPS (`grep` + nav rules). `type:` on search is unchanged in this work.
2. `--type` focuses the **page walk** only. SCHEMA, staging, mesh, index rules still run on the whole store.
3. Canonical flag is `--type`. `--list-type` is a **hard cut** (no alias).
4. Focused stdout is **gate output plus the matching path list**. JSON includes `critical`, `warnings`, and `pages`.
5. `--path` is the same lens on a store-relative prefix (folder or one file). Anything under that prefix is in the page walk.
6. `--type` and `--path` together are **AND**. Empty intersection is still a successful focused compile of zero pages if store-level checks are clean.
7. `--path` after resolve must stay **inside `--root`**. `..` or absolute escape → critical exit 2. Prefix that does not exist inside the store → critical exit 2.
8. This slice: at most one `--type` and one `--path`. Repeatable flags and globs are protostars, not scope.

## Scope (implement after approval)

- `cli.py`: on `compile` and `validate`, add `--type` and `--path`; remove `--list-type`.
- `validate.run`: accept `type_name` and `path_prefix`. Always run store-level checks. Filter `iter_concept_md` page walk by type and/or resolved prefix.
- After the walk: print issues as today, then the matching page list (path + title). Scope line: `type=… path=… pages=N`.
- `--json`: add `type`, `path`, `page_count`, `pages: [{path, title, type}]`. Do not skip issues.
- Exit codes unchanged: 2 critical, 1 warnings only, 0 clean. Listing never forces 0.
- SKILL.md CLI surface + help epilog.
- Version bump on implement (0.7.6).
- Construct / CLI smokes listed below.
- This store’s SKILL one-liners only. No silent rewrite of sibling stores.

## Non-goals

- A `list` command.
- Keeping `--list-type`.
- Changing search engines or adding `--path` to search.
- Globs, repeated flags, `--kva`, `--work-id`.
- Promoting warnings to critical.
- Repairing other skills’ Atlases.
- agent-spec Gherkin in this design turn (deferred below).

## Challenge

Internal think-challenge. Grounded counters:

| Counter | Source | Severity | Pin |
|---------|--------|----------|-----|
| `--path ../…` or absolute path walks files outside the store. Agent-invoked CLIs have shipped this class of bug. | Google Workspace CLI PR 447; OWASP Path Traversal | high | Accept: resolve + must be under `--root` or critical. |
| Empty slice should not look like failure. `find` exits 0 when nothing matches if traversal succeeded. | find(1) POSIX / Linux man | medium | Accept: empty AND is exit 0 unless store issues exist. |
| Printing every matching path plus issues re-creates the opportunistic “list” habit. | This discussion Q6 | medium | Reject change: operator chose B. Listing is extra stdout on a real gate. |
| Store-level index warnings outside `--path` will surprise a subgraph compile. | Q3 pin | low | Accept surprise: one gate, lens on pages only. |

## Genesis Artifacts

### Mermaid

```mermaid
sequenceDiagram
  participant CLI
  participant Schema as SCHEMA + staging
  participant Pages as page walk
  CLI->>Schema: Layer 1 always
  alt path escapes root or missing
    CLI-->>CLI: critical exit 2
  else
    CLI->>Pages: filter type AND path prefix
    CLI-->>CLI: issues + pages list; exit 0/1/2
  end
```

### Interface sketch

```text
atlas compile|validate --root <atlas> [--json] [--type <name>] [--path <store-relative>]
```

`--path autogenesis/discuss/` includes that folder and descendants.  
`--path work/foo.md` is that file only.

### Cost note

Same page walk as compile today, with two string filters. Resolve `--path` once. Cheap.

### Acceptance

- `compile --type protostar` runs SCHEMA/staging checks; reports page issues only for protostars; prints those paths; exit from issues not from listing.
- `compile --path autogenesis/discuss/` page-walks only that prefix.
- Both flags: intersection.
- Zero matching pages + clean store → exit 0, `pages=0`.
- `--list-type` is unknown option (Click error, not silent ignore).
- `--path ../` or `--path /etc` → critical, no walk outside root.
- `--path does-not-exist/` → critical.
- Unfocused `compile` behaviour and exit codes unchanged.

### Stop for approval

Do not implement until the operator approves this plan.

## Catalogue Review

`catalogue_review: in-scope` (compile is a gate).

- genesis matches: none named (no new panel / fan-out).
- Autogenesis extension: B17 activation card already on atlas; no change to card schema required for a CLI flag.
- composition: INLINE in existing `commands/validate.py` + thin `cli.py` wiring (agent-cli pattern already in place).
- inherited anti-pattern: do not hang inventory on the gate and skip the gate (0.7.5). This plan removes that.
- admission: flag change stays in the existing CLI package; no new skill.

## Behavioural contract (agent-spec)

`deferred: specify on implement after approval. Pins are CLI flags, filters, exit codes, and JSON keys; Gherkin would only restate those. Forbidden: list-type dump that returns 0; path escape.`

## Evaluation plan

Deterministic (primary):

- Click help has `--type` and `--path`, not `--list-type`.
- Fixture: dirty page outside `--path` does not appear in page issues; dirty page inside does.
- Fixture: `--type` ignores other types’ page-contract misses.
- Fixture: `--path ../` exit 2.
- Fixture: missing prefix exit 2.
- Fixture: empty AND + clean store exit 0.
- Fixture: warnings inside slice exit 1 and JSON has both `warnings` and `pages`.

Agent evaluations: optional; not required for these flags.

## Adversarial scenario draft

File on implement: `atlas/references/scenarios/compile-focus-lenses-adversarial-v1.yaml`

- smoke `list-type-gone` — source: Q5 hard cut
- smoke `list-type-must-not-exit-0` — source: 0.7.5 defect / p-list-swallows-gate
- smoke `path-escape-critical` — source: OWASP / GW CLI PR 447
- smoke `empty-and-ok` — source: find(1) exit 0
- smoke `and-intersection` — source: Q8

## C1–C5

- C1: path-escape counter is non-trivial.
- C2: high-severity path-escape pinned into scope.
- C3: pins listed above.
- C4: search GPS, no list verb, store checks always on.
- C5: no implementation in this path.
