---
type: document
title: "Counter — composition is additive, not a merge overlay"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "JSON Schema allOf does not override. Conflicting properties fail. Plan merge of templates.by_type is the same trap."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: counters
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
  - path: experiences/2026-09-03-challenge-schema-governance-plan.md
    kind: records
---

## Content

The plan treats overlay merge as object-key union with clash-fail. That matches “no last-writer-wins” at the *root* of SCHEMA.

The live risk is nested merge: `templates.by_type.work.frontmatter.required` in core plus the same path in an overlay. JSON Schema `allOf` is composition, not inheritance. Two subschemas that declare the same property differently do not overlay; the instance cannot satisfy both. OpenAPI authors who try to override an inherited property with `allOf` hit this. Tools that flatten `allOf` either error or pick the most restrictive constraint — they do not last-writer-wins.

Sources: [Swagger allOf](https://swagger.io/docs/specification/v3_0/data-models/oneof-anyof-allof-not/); [SO: allOf cannot override inherited property](https://stackoverflow.com/questions/61177034/openapi-spec-using-allof-to-override-inherited-property); [SO: allOf best practice](https://stackoverflow.com/questions/79823407/best-practice-use-of-allof-in-openapi-specification).

Severity: high. If we deep-merge `templates.by_type`, we re-introduce the conflict the plan thought it closed.

**Pin (autonomous, operator away 2026-09-03):** overlays may only add types. They must not mutate core `templates.by_type` entries. Nested merge of `work` / `document` / other core types is forbidden. Counter 5 (redefine base types) is absorbed.

## Provenance

think-challenge 2026-09-03 before sign-off.
