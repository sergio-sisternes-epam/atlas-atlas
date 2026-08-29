---
type: document
title: "Doubt — default .atlas vs --target-skill vs Atlas outside skills"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: ".atlas is default install target only. --target-skill writes into a skill tree. Multi-atlas-per-skill is the tension."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/leaves/p-agents-location.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
---

## Content

User doubt 2026-08-29:

- `.atlas/` is probably only the **default** when no `--target` is set.
- `--target-skill` could install into that skill’s historical default, `references/atlas/`.
- That collides with “more than one Atlas for one skill” (a skill knowledge mesh).
- Open question: does it still make sense to have `.atlas/` *and* ship Atlas trees outside skills?

Working distinction (not pinned):

| Role | Where | How many |
|------|--------|----------|
| Skill process memory | `<skill>/references/atlas/` | at most one authored store per skill |
| Installed corpora | `.atlas/<kebab>/` or `--target <path>` | many |
| Published Atlas package | own git/APM repo | one grain per package (mono/multi still open) |

`--target-skill` as a special case that *replaces* a skill’s process-memory root is different from “install another corpus the skill can mesh.” Mixing them in one folder is the tension.
