---
type: document
title: "SDLC-first scenarios for Atlas"
created: 2026-08-27
description: "Prove Atlas on app modernisation, requirements, development, testing, and operations before non-functional scenarios."
origin: user
sensitivity: internal
status: alive
kva: alive
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/vision.md
    kind: derived_from
  - path: atlas-project/branching-model.md
    kind: related
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
---

## Content

Do not invent a type zoo per stage. Reuse Atlas types. Change which pages and relations dominate.

| Stage | Dominant pages | Dominant edges | Behaviour to enforce |
|---|---|---|---|
| App modernisation | `document` (as-is), `decision`, `protostar`, `work` | `derived_from`, `supersedes`, `implements` | As-is and to-be coexist; staging cannot answer “what is current” |
| Requirements | requirement-shaped `document`, `decision`, `work` | `implements`, `follows` | Scope change is a PR; agents cannot silently rewrite |
| Development | `recipe`, `decision`, `experience`, `work` | `implements`, `records` | Decision is SoR; a code PR can cite `atlas://` |
| Testing | `experience`, `lesson`, `recipe` | `records`, `derived_from` | Failures become lessons only after compile |
| Operations | `recipe` (runbook), `experience` (incident), `decision` | `follows`, `supersedes` | Runbook update is a PR to the ops Atlas |

Non-functional scenarios (security, cost, accessibility, SRE principles) wait until these five produce repeating shapes. Then promote a lesson or recipe convention — not a new product.

Suggested proving order: requirements + modernisation decisions first; second team mounts and lands one knowledge PR; then write contribution behaviour; then project merged main into Search/IQ.

## Provenance

User framing 2026-08-27. Name pin of 2026-08-23 already listed requirements and project knowledge graphs in Atlas scope.
