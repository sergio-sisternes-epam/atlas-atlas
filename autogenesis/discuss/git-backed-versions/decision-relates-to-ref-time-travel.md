---
type: decision
title: "Decision — optional relates_to.ref is shared space/time for Claims A and B"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: accepted
kva: alive
reality: current
description: "Shared capability: optional relates_to.ref (git rev) is time travel for both Claim A version hints and Claim B terminate history. Tip compile does not resolve ref yet. atlas#37 and #38."
tags: [decision, ref, time-travel, claim-a, claim-b]
origin: derived
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: records
  - path: autogenesis/discuss/git-backed-versions/decision-claim-b-tip-summary-git-history.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/decision-claim-a-living-version-hints.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/constellation-2026-09-27-git-backed-versions.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
---

## Decision

Optional **`ref` on each `relates_to` item** (beside `path` / `kind`) is the **shared space/time** capability for both Claim A and Claim B:

- **Absent `ref`** ⇒ tip behaviour unchanged (resolve `path` on HEAD; tip compile today).
- **Present `ref`** ⇒ resolve `path` at that git revision (time travel). Tip compile does **not** resolve those edges for now; history is deliberate recall.

Same word collision watch as the pin: mount/mesh store-tracking `ref` vs per-edge relation `ref`. Edge-level field preferred over page-level.

Claims differ by **recipe**, not by schema:

| | Claim B ([#37](https://github.com/sergio-sisternes-epam/atlas/issues/37)) | Claim A ([#38](https://github.com/sergio-sisternes-epam/atlas/issues/38)) |
|---|---|---|
| When | After KVA terminate / prune | On living evolving pages |
| Tip role | Thin terminate summary stand-in | Current living memory |
| `ref` use | Gateway from summary into failed-path history | Version hints to prior wording |

## Rationale

One contract for path@rev avoids divergent front-matter and duplicate compile/recall work. Tip stays the cheap “now” projection; `ref` walks are as-of/why.

## Consequences

- Schema docs and implement should land `relates_to[].ref` once, referenced by both issues.
- Optional expensive later compile of `ref` edges remains deferred for both.
- Supersede ≠ terminate: same `ref` shape, different recipes.
