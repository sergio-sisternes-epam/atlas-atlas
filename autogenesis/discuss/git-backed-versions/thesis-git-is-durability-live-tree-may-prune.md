---
type: experience
title: "Thesis — Git is durability; the live tree may prune"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: alternative
description: "Forming thesis. Once the store is a Git repo, pages need not be treated as immutable on HEAD. Atlas can relate to past versions by git ref, and can remove terminated notes from the live graph while pinning a pointer to the commit before deletion."
tags: [thesis, git, kva, prune, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/claim-a-version-hints-on-living-pages.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/hub.md
    kind: follows
---

## Context

User claim (2026-09-27): once Git is engaged, it makes no sense that memories become immutable, because Git already tracks changes. Atlas could support relationships to past versions of the same file and leave small points or hints to those versions. The same git-ref relationship can support deleting KVA-terminated notes to reduce live-graph complexity, keeping a pointer to the KVA entrypoint pinned to the specific git commit before deletion.

## What happened

### Claim package (still forming)

**A — Version hints on living pages.** An alive (or forming) page may declare a relationship to one or more prior git versions of itself (or of a named path), carrying a small human hint about what changed. Durability of the old bytes is Git’s job. The live page carries navigation, not a full archive copy.

**B — Prune terminated from HEAD (refined).** Keep the KVA *terminate summary* on the active branch. Remove the full trial body from tip. Point from the summary to the old path (and commit) so detailed experiences stay traversable at higher recall cost. Live complexity falls without losing history.

### Tension with current discuss defaults

Discuss process elsewhere: do not delete exit stubs; do not flip terminated back to forming on the same page; reactivation is a new forming page with `derived_from` the stub. That protects scar readability inside the working tree. This thesis relocates the scar into Git plus a thinner pointer, so the scar remains, but not necessarily the full terminated body on HEAD.

### Early counters (batch, not yet probed)

1. **URI breakage** — `atlas://` and `relates_to` paths that pointed at the deleted file break unless stubs keep the path or URIs grow a `@rev` form.
2. **Scar without body** — a SHA-only pointer may be too thin for humans who never open `git show`.
3. **Compile contract** — compile and search must define what a “git-ref relation” is, and whether deleted-but-pointed pages count as present.
4. **Who may prune** — auto-prune vs steward/path-driven prune after terminate.

## Outcome

Forming. Claim B refined: summary stays on HEAD; full trial may leave the active branch behind a git/path pointer (see claim-b-summary-on-head-trial-in-git.md). Still needs pointer shape and whether A ships with B.
