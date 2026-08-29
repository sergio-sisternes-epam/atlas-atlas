---
type: document
title: "Orbit — which file is the rulebook for SCHEMA.json"
created: 2026-08-27
work_id: 2026-08-27-atlas-compile-type-contract
status: settled
kva: alive
reality: current
description: "Pin: Open/Closed. Contract is closed. Store SCHEMA extends by adding type checklists."
origin: derived
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/compile-type-contract/leaves/p-contract-vs-live-schema.md
    kind: derived_from
  - path: autogenesis/discuss/compile-type-contract/init-surface.md
    kind: follows
  - path: work/2026-08-27-atlas-compile-type-contract.md
    kind: implements
---

## Content

Each Atlas folder has its own SCHEMA.json. The atlas skill also has a contract file that describes what a SCHEMA.json should contain. Those two files already disagree on one check name (`orphans`).

**I — the folder’s SCHEMA.json is the only rulebook.** Compile reads that file and checks pages against it.

**J — the skill contract file checks the folder’s SCHEMA.json first.** Then compile uses the folder file. Init must write a SCHEMA that matches the contract.

**Pin (operator 2026-08-27): Open/Closed.**  
Closed: we do not change compile code for each new type.  
Open: a store SCHEMA adds type checklists; compile reads them.  
The skill contract defines the shape of SCHEMA.json. The store file is where we add types. That is J plus extension. Existing pages are not frozen; they get warnings until repaired.

## Provenance

Next parked item after pin F.
