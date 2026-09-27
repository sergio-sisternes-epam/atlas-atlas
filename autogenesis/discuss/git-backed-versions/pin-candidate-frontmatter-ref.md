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
3. Does compile warn, ignore, or optionally fetch blobs for `ref`-qualified edges?
4. Keep the word `ref`, or rename relation field to avoid mount-card collision?

## Outcome

Forming pin candidate for pointer shape. Awaiting grain and naming confirmation.
