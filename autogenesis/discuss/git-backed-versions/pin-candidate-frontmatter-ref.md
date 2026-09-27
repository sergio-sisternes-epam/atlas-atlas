---
type: experience
title: "Pin candidate — front-matter `ref` for off-tip memory links"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "User proposal for pointer shape. Use the word ref in Atlas/OKF front-matter when a link targets past memories that are not on the active branch tip."
tags: [ref, frontmatter, okf, pointer, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-ref-edges-not-compiled.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
---

## Context

Sergio (2026-09-27): use the word `ref` in Atlas / OKF front-matter when linking to past memories that do not belong to the active branch.

## What happened

### Proposal (forming)

Today `relates_to` entries are tip-relative: `{path, kind}` and compile resolves `path` on HEAD. Off-tip links need an explicit signal that the target is historical.

Candidate grain: add optional `ref` beside `path` (and `kind`) on a relation, meaning “resolve this path in that Git revision, not on the active tip.”

Illustrative shape (not yet schema):

```yaml
relates_to:
  - path: autogenesis/discuss/example/terminated-trial.md
    kind: derived_from
    ref: abcdef1   # commit (or other git rev) where that path still exists
```

Absent `ref` ⇒ current behaviour (tip). Present `ref` ⇒ history-dimension link; compile must not require the path on HEAD; recall may pay more to materialise it.

### Name collision to watch

Atlas already uses `ref` on mount cards and mesh stores for the *branch* to track (`ref: main`). Git uses “ref” for named pointers. This proposal reuses the word for a *per-edge revision* of a page path. Same word, different grain — schema docs must separate store-tracking `ref` from relation `ref`, or pick a clearer relation key later (`at`, `rev`, `git_ref`) if collision hurts.

### Fit to pointer-shape batch

Closest to **URI / ref form** and **summary-plus-fields**, not same-path stub. The terminate summary (or any living page) keeps tip; trial pages may vanish from HEAD; edges carry `ref` to reach them.

### Still open on this node

1. Is `ref` on each `relates_to` item (preferred reading), or a page-level field?
2. Allowed values: full commit SHA only, or also tags / branch names (branches move — usually wrong for scars)?
3. Compile for `ref` edges — pinned: not compiled for now (see pin-ref-edges-not-compiled.md).
4. Keep the word `ref`, or rename relation field to avoid mount-card collision?


### Worked example in current `relates_to` list shape

Today SCHEMA says authoritative links are `relates_to: [{path, kind}]`. Tip edges stay that shape. Off-tip edges add optional `ref` on the **same list item**.

```yaml
relates_to:
  # Tip (unchanged)
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: related

  # Off-tip: trial page removed from HEAD; still addressable in history
  - path: autogenesis/discuss/git-backed-versions/old-trial-counter.md
    kind: derived_from
    ref: 8ab638c1f0e2a9b4c5d6e7f8091a2b3c4d5e6f70
```

Reading: missing `ref` ⇒ resolve `path` on the active tip (compile today). Present `ref` ⇒ resolve `path` at that Git revision; do not require the file on HEAD.

Not page-level `ref:` next to `title` — that would collide harder with mount/mesh `ref` and would not scale when one summary links several historical paths at different commits.

## Outcome

Edge-level `ref` confirmed by user. Compile: `ref` edges are not resolved for now (pin-ref-edges-not-compiled.md). Naming collision with mount `ref` still noted, not blocking.
