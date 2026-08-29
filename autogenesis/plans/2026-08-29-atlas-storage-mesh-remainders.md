---
type: plan
title: "Design — mesh remainders after gap-close"
created: "2026-08-29"
work_id: "2026-08-29-atlas-storage-mesh-remainders"
status: implemented
change_class: hardening
subject: atlas
kva: alive
description: "auth.json consumed by mount, jsonschema declared, headless guard, card hygiene, superseded historical pages. Live gh login stays a protostar."
plan_path: autogenesis/plans/2026-08-29-atlas-storage-mesh-remainders.md
catalogue_review: n/a
catalogue_review_rationale: "No new topology; wiring leftovers and store hygiene."
behavioural_contract: deferred: agent-spec after approval if mount-auth wiring is treated as new behaviour
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-remainders.md
    kind: implements
  - path: work/2026-08-29-atlas-storage-mesh-gap-close.md
    kind: follows
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: follows
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-live-auth-login.md
    kind: related
  - path: autogenesis/experiences/2026-08-29-gap-close-honest.md
    kind: derived_from
---

## Intent + scope

Close graph and wiring leftovers that the last honest review named. Do not pretend live GitHub login is done.

**In**

1. `mount` / translation **read** user `auth.json` (ssh vs https, host then org).
2. Declare `jsonschema` as a runtime dependency of the Atlas skill (`apm.yml` or equivalent). Fail compile/mesh validate with a clear message if the package is missing.
3. Headless guard: `mount` and `auth login` refuse when git is absent, pointing at the capability matrix.
4. Hygiene: rewrite stale task cards; mark superseded early discuss pages (`current-reality` already fixed; tensions/checkout drafts still read as current).
5. Open explicit work tasks for those items (this epic). Keep `p-live-auth-login` as protostar, not a fake task-done.

**Out**

Live `gh auth login` in this sandbox. Nested-group URIs. APM-copy-then-mount. Org/repo migration. agent-spec Gherkin in this design path (deferred one line).

## Non-goals

New verbs. Changing atlas-id rules.

## Acceptance

- With `auth.json` saying ssh for a host, `mount` uses `git@`.
- Missing `jsonschema` prints a named error, not a stack dump only.
- `mount` without `git` on PATH exits non-zero with a headless message.
- Cards for reopened/partial work match status.
- Historical discuss pages that the pins replaced are `status: superseded` or `kva` equivalent and linked `supersedes`.

## Pins used

`decision-atlas-auth`, `decision-mount-auth-flow`, `decision-git-default-headless`, `decision-pointer-vs-auth`.

## Counters

- Calling remainders “docs only” — rejected.
- Implementing live login here without credentials — rejected; protostar stays.

## Catalogue Review

n/a — hygiene + existing CLI wiring.

## Stop

Stops for approval. No further CLI until you accept this plan.
---
