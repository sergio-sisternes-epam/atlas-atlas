---
type: document
title: "Lean — skill Atlas is internal memory; mesh is distributed memory"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: superseded
reality: archive
description: "references/atlas signals skill-internal memory. Other skills may write it. APM materialise must not destroy git provenance."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/dot-atlas-and-target.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/atlas-as-own-repo.md
    kind: related
  - path: autogenesis/discuss/git-mesh/leaves/p-skill-knowledge-mesh.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
  - path: autogenesis/discuss/git-mesh/consolidate-view.md
    kind: related
  - path: autogenesis/discuss/skill-mount-home/exit-skill-internal-store.md
    kind: kva_supersede
---

## Content

User lean 2026-08-29:

- An Atlas under `references/atlas` is **skill-internal information**. The path is a signal, keep it.
- That store is the skill’s **internal memory**. Other skills may write into it (today: Autogenesis writing into another skill’s Atlas). That is allowed.
- Autogenesis “overall memory” is not one mega-store. It is the **mesh of Atlases** plus the pages inside them — distributed memory. That is probably fine.
- The pain is the **APM cycle**: a proper install must not treat `references/atlas` as editable source the way we do in a working tree, yet editing it in place is working.
- APM also **breaks trace** to the original repo: it transforms skill content into harness folders and drops the git identity of those files.
- Candidate repair: materialise the skill Atlas as a **git submodule inside the APM-materialised skill folder**, so the remote and PR path survive the transform.

`.atlas/` remains the default target for Atlases that are *not* a skill’s internal memory.
