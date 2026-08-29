---
type: decision
title: "Add protostar to Atlas recommended types"
created: 2026-08-26
status: accepted
work_id: 2026-08-26-residuals-vs-protostar
origin: user
sensitivity: internal
description: "protostar is a recommended page type for forming ideas linked to origin and work hub. residuals/ is not a store convention."
relates_to:
  - path: decisions/type-vocabulary-document-and-sensitivity.md
    kind: follows
  - path: decisions/type-vocabulary.md
    kind: related
  - path: work/2026-08-26-residuals-vs-protostar.md
    kind: implements
---

## Decision

1. Recommended SCHEMA types include **`protostar`** alongside experience, decision, lesson, recipe, work, document.
2. Role: forming idea that may be worth chasing later. Not implement authority.
3. Required practice when `work_id` exists: `relates_to` work hub `implements`, plus origin `derived_from`.
4. Do not file protostars under a `residuals/` folder.

## Rationale

Findability is `type` plus `kva: forming`. Context is relations. Autogenesis and discuss were inventing a residuals bucket because the substrate did not name the type.

## Alternatives considered

- Keep protostar discuss-only (rejected — every Atlas consumer needs the same shape).
- Closed enum (rejected — OKF freedom).

## Consequences

SKILL.md, SCHEMA.contract.json, process SCHEMA, remember path, and `templates/protostar.md` updated.
