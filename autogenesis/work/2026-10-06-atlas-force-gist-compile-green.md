---
type: work
title: "Work: 2026-10-06-atlas-force-gist-compile-green"
created: 2026-10-06
updated: 2026-10-06
work_id: 2026-10-06-atlas-force-gist-compile-green
status: designed
subject: atlas
kva: alive
stage: designed
origin: user
sensitivity: internal
description: "Authoring hub for force-gist / compile-green follow-on after atlas 0.13.0-beta.11. Amended: useful gists only (no stubs); Cut 1b LOCKED CLOSED (enrich-before-migrate / block; exclude-from-index REJECTED); shared cluster gist N→1; MultiCluster; Cut 2 LOCKED (cluster membership = same folder only — not cross-folder relates_to). Design only; stop for Hand/Sergio approval. No package implement."
plan_path: autogenesis/plans/2026-10-06-atlas-force-gist-compile-green.md
relates_to:
  - path: autogenesis/plans/2026-10-06-atlas-force-gist-compile-green.md
    kind: implements
  - path: autogenesis/experiences/2026-10-06-atlas-force-gist-compile-green-design.md
    kind: related
---

# Work: 2026-10-06-atlas-force-gist-compile-green

Autogenesis authoring-work record for atlas force-gist / compile-green. Not a runtime asset of the atlas package.

## Links

- Plan: `autogenesis/plans/2026-10-06-atlas-force-gist-compile-green.md`
- Design experience: `autogenesis/experiences/2026-10-06-atlas-force-gist-compile-green-design.md`
- Baseline: atlas `0.13.0-beta.11` (PR #53)
- Prior work: `2026-10-06-atlas-optimise-vnext` (residual missing_gist allowed — overridden for opted-in stores; subject-clustering reused for shared gist)

## Status history

- designed: 2026-10-06 — Autogenesis design (new-surface mini-genesis) on branch `autogenesis/2026-10-06-atlas-force-gist-compile-green`; **STOP FOR APPROVAL**; no package implement
- amended: 2026-10-06 — Folded Sergio amend pin (no gist stubs — every gist useful / evidence-grade); retracted titled-stub / shell-gist clearance; recorded Cut 1b OPEN (later superseded). Still **STOP FOR APPROVAL**; no package implement.
- amended: 2026-10-06 — Folded Sergio pins as **LOCKED**: Cut 1b **CLOSED** — (a) enrich-before-migrate / block migrate until useful gist **LOCKED**; (b) exclude-from-index **REJECTED**; every indexed memory covered; **NEW** chained/related → one shared cluster gist (N→1) aligned with existing optimise subject-clustering; DerivedN / Schema1 pinned. Still **STOP FOR APPROVAL**; no package implement.
- amended: 2026-10-06 — **MultiCluster LOCKED** (Sergio via Hand): multiple clusters per folder allowed; each cluster gets its own shared useful gist under the folder schema layer (one-gist→one-schema per gist). Still **STOP FOR APPROVAL**; no package implement.
- amended: 2026-10-06 — **Cut 2 / FolderOnly LOCKED** (Sergio via Hand): cluster membership = **same folder only**; cross-folder `relates_to` does **not** join force-gist clusters; subject-clustering / work-cluster / `--subject-folder` may move pages first; membership evaluated after location. Still **STOP FOR APPROVAL**; no package implement.

## Notes

Pins name writer (**verbatim/evidence-gated useful gist only** — titled stub path superseded), Cut 1b a LOCKED / b REJECTED, shared cluster gist N→1 + MultiCluster, **Cut 2 same-folder membership only** (cross-folder `relates_to` does not join; organise/move may precede), scope (`MISSING_GIST_TYPES` ∩ unfocused compile index — all covered), compile critical after migrate+stamp with grandfather, scan_gate on migrate/remember/optimise, Path-first cost, pilot compile-green exit, Rem1 same-turn useful gist or fail closed. Sleep still unimplemented. Heavy/fleet blocked until Sergio GO under the new bar.
