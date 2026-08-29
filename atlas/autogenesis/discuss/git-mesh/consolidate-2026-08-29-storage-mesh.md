---
type: document
title: "Consolidate 2026-08-29 — storage mesh over git"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
consolidation: true
description: "Formal discuss consolidate. Partial dated stance. Feeds from informal consolidate-view.md."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/hub.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: derived_from
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-2026-08-29-contradictions-closed.md
    kind: feeds
  - path: autogenesis/discuss/git-mesh/scope-storage-not-query.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/drop-aliases-mvp.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-apm-uncoupled.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/exit-aliases-dropped.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/protocol-is-not-identity.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/skill-atlas-internal-memory.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/option-c-derived-short.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/stack-three-layers.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: confirms
  - path: autogenesis/discuss/git-mesh/checkout-resolve-design.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/id-to-checkout-join.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/git-aware-atlas.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/current-reality.md
    kind: restates
  - path: autogenesis/discuss/git-mesh/current-mesh-reality.md
    kind: restates
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/identity-id-is-repo-url.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/option-a-url-primary-aliases.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/option-b-short-primary.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/mount-submodule-worktree.md
    kind: refutes
  - path: autogenesis/discuss/git-mesh/atlas-auth.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/apm-auth-precedent.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/apm-env-outranks-gh.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/tension-url-as-id.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/tension-checkout-lifecycle.md
    kind: expands
  - path: autogenesis/discuss/git-mesh/leaves/p-alias-collision.md
    kind: absorbs
  - path: autogenesis/discuss/git-mesh/leaves/p-url-normalisation.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-monorepo-id.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-repo-org-migration.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-uri-fragment.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-unresolved-id-policy.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-install-vs-checkout.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-target-skill.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-skill-knowledge-mesh.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-kebab-encoding.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-id-fs-encoding.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-checkout-parent-git.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-submodule-lifecycle.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-agents-location.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-apm-git-trace.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-mono-vs-multi.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-package-shape.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-mesh-pull.md
    kind: indexes
  - path: autogenesis/discuss/git-mesh/leaves/p-optional-git-cut.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-precedence.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-protocol-choice.md
    kind: defers
  - path: autogenesis/discuss/git-mesh/leaves/p-auth-helper-surface.md
    kind: defers
---

## Picture (this snapshot)

```text
atlas-id = host/org/repo     no scheme, no nickname

skill internal memory              working set                 published package
<skill>/references/atlas           .atlas/<kebab>/             own git repo
signal: process memory             default --target            APM may copy files

writes = git commit / PR
agents run Atlas CLI (init, install, query, …) + git
APM and Atlas are separate products
mesh + atlas:// = distributed memory
```

## Confirms

- Storage mesh only; query implementation out of scope except as a named verb.
- No cute aliases. Id names the server (`github.com/org/repo`).
- Protocol is not identity.
- Atlas ⟂ APM. No product hooks. Agents know Atlas + git.
- `references/atlas` = that skill’s internal memory. Other skills may write it. Autogenesis memory = the mesh.
- `.atlas/` = default install target for non-skill corpora.
- Atlas may live as its own repo/package. `atlas install` materialises; submodule if already in a git repo.
- Git is the overlay. No second overlay tree.

## Refutes

- Full clone URL (with scheme) as atlas-id.
- Short nicknames as primary identity (option B) or optional alias table (option A).
- Worktree-as-write-mount as the MVP contribution path.
- Teaching APM to preserve Atlas remotes.

Those pages **remain** in the graph. This snapshot rejects them as current reality.

## Expands

- Informal `consolidate-view.md` → this formal stance view.
- Checkout/resolve → `atlas install` + lean skill + mesh registration.
- “Git-aware” → git *is* the overlay.
- T2 lifecycle → parent git / dirty tree / verb surface still open, but write=PR is the lean.

## Defers

- Auth helper vs “user always passes URL”; env-then-gh vs gh-first.
- Repo/org migration.
- What works with no git.
- Exact T1 leftover (normaliser details) except the scheme-free shape already confirmed.

## Indexes (gaps)

Identity: normalisation, monorepo `subpath`, `atlas://` vs `#`, missing id.  
Install: install vs checkout, agent verbs, kebab path, parent `.gitmodules`, `--target-skill`, skill mesh folders, package grain, mesh pull, APM-copy then Atlas restore.  
Auth cluster parked.

`p-alias-collision` is **absorbed** into `drop-aliases-mvp` (terminated leaf).

## Contradictions still live (idea↔idea)

This view **confirms** one side and **refutes** the other without deleting either:

1. scheme-free id vs full-URL id  
2. never-guess protocol vs auth helper reconstructs protocol  
3. `install` vs `checkout` as the materialise verb  
4. APM-as-files vs APM-as-Atlas-API (API side refuted; files side confirmed)  
5. `--target-skill` into process memory vs path-as-signal  
6. git optional vs git is the overlay  
