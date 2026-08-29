---
type: document
title: "Doubt — install and checkout both misname the verb"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: superseded
kva: alive
reality: current
description: "Contradiction 3 is now a naming problem. The act is attach pointer + materialise git tree + mesh row."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/contradiction-install-vs-checkout.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-install-vs-checkout.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-atlas-agent-verbs.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## The act

1. Take a pointer (MD URL, `atlas://`, host/path).
2. Translate via `atlas auth`.
3. Materialise a git working copy (submodule if inside a repo).
4. Register the tree on the mesh.

Not “install a package into a runtime.” Not “git checkout a branch.”

## Candidate verbs (forming)

| Verb | Fits | Lies |
|------|------|------|
| `add` | mesh membership | weak on “tree now on disk” |
| `attach` | pointer + local tree | slightly mechanical |
| `clone` | honest git | ignores mesh registration; fights submodule-in-parent |
| `mount` | local path appears | overlay metaphor we just dropped |
| `connect` | mesh | weak on disk |
| `sync` | later updates | wrong for first materialise |
| `use` | skill tone | vague |
| `install` | APM rhyme | package-manager baggage |
| `checkout` | familiar git | branch operation, not this |

User: neither install nor checkout feels accurate. Name still open. No pin on #3 until a verb is chosen.
