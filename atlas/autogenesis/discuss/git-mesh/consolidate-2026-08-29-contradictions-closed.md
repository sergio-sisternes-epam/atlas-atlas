---
type: document
title: "Consolidate 2026-08-29 — contradictions closed"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
consolidation: true
description: "Second snapshot. Pins #2 #3 #5 #6. Feeds from storage-mesh consolidate."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-storage-mesh.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-mvp-mesh.md
    kind: feeds
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/decision-pointer-vs-auth.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-verb-mount.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-target-path.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/decision-git-default-headless.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-capabilities-by-mode.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/scope-storage-not-query.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/pointer-vs-auth.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/option-b-short-primary.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: restates
  - path: autogenesis/discuss/git-mesh/contradiction-protocol-guess.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/contradiction-install-vs-checkout.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/contradiction-target-skill.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/contradiction-git-optional.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/verb-materialise-name.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-url-normalisation.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-monorepo-id.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-uri-fragment.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-unresolved-id-policy.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-kebab-encoding.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-checkout-parent-git.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-helper-surface.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-precedence.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-protocol-choice.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-apm-git-trace.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-mono-vs-multi.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-package-shape.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-mesh-pull.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-repo-org-migration.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-optional-git-cut.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-install-vs-checkout.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-target-skill.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-agents-location.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-skill-knowledge-mesh.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-alias-collision.md
    kind: absorbs
---

## Picture

```text
pointer (MD / atlas:// / host/org/repo)
        │
        ▼
atlas auth  →  translation  →  git remote for this process
        │
        ▼
atlas mount <pointer>  [--target path]
        │
        ▼
.git working copy on disk     default .atlas/<id>/
                              skill memory stays references/atlas

Atlas = OKF + graph     Git = DFS overlay
APM = separate product
```

Modes: **remote git** (full) · **local git** (Grok Cloud ok) · **headless** (reader + edit, no mount/publish).

## Confirms

No aliases. Scheme-free id. Pointer ≠ credential. `atlas mount`. Default `.atlas/`. `--target` path only. Skill `references/atlas` = internal memory. Git default overlay; local git counts; headless documented. APM uncoupled. Storage-not-query scope.

## Refutes

Full-URL identity. Nickname identity. Worktree-as-write MVP. `atlas checkout` / `atlas install` as product verbs. `--target-skill`. Git-optional as a peer writer architecture.

## Absorbs

Contradiction pages 2, 3, 5, 6 and the install/checkout naming leaf. Optional-git cut. Target-skill leaf. Agents-location (answered: `.atlas/` + skill path). Skill-knowledge-mesh (mesh, not extra folders). Alias-collision.

## Expands

Own-repo + mount (not install). Git-aware → default overlay + capability matrix.

## Defers

Repo/org migration.

## Indexes (still open)

Normaliser, monorepo subpath, `atlas://` vs `#`, missing id, kebab/fs encoding, parent git for submodule, mount lifecycle, `atlas auth` grain/precedence/protocol, agent verb list polish, APM-copy then mount, mono vs multi package, atlas package shape, mesh pull/update.
