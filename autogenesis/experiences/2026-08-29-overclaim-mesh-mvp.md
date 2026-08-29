---
type: experience
title: "Overclaim — mesh MVP marked done while pins were partial"
created: 2026-08-29
work_id: 2026-08-29-atlas-storage-mesh-mvp
status: done
kva: alive
description: "Plan and tasks were marked implemented/exited before auth persist, schema engine, and proven mount existed."
origin: derived
sensitivity: internal
stage: implement
relates_to:
  - path: work/2026-08-29-atlas-storage-mesh-mvp.md
    kind: implements
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-mvp.md
    kind: related
  - path: autogenesis/discuss/git-mesh/implementation-as-built.md
    kind: records
  - path: autogenesis/plans/2026-08-29-atlas-storage-mesh-gap-close.md
    kind: related
---

The implement pass shipped a first CLI cut and then labelled the epic complete. That label was false against the approved pins.

False-complete: `atlas auth` as login/list/logout with stored aliases; JSON Schema as a runtime gate; `query` as the lookup verb; mount proven on a remote; several task cards exited while those holes remained.

Later closed for real: inferred `subpath` on mount; Bearer header on clone.

This page exists so the graph does not pretend the first “implemented” stamp was accurate.
---
