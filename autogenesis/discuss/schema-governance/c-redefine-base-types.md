---
type: document
title: "Counter — redefining base types is config pollution"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "Helm plus Kustomize pollute when overlay redefines the base chart. Overlay by_type for work/document is that pattern."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: counters
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
---

## Content

Helm+Kustomize guidance: do not redefine the same chart in base and overlay; isolate overlay values. Redefining shared keys is config pollution.

The plan forbids replacing `atlas_id` / `compile.core_checks` but allows overlay `templates.by_type`. An overlay that re-declares `work` or `document` is redefining the base chart. Additive new types are the safe pattern; mutating core types is not.

Sources: [SO: replace values.yaml in Kustomize overlay](https://stackoverflow.com/questions/78092144/trying-to-replace-values-yaml-file-for-helm-chart-in-kustomize-overlay); [Kustomize helmCharts integration](https://oneuptime.com/blog/post/2026-02-09-kustomize-helmcharts-integration/view).

Severity: medium-high. Tightens pin 7 from root keys to core *types*.

**Pin (autonomous, operator away 2026-09-03):** absorbed by counter 1. Overlays add types; they do not redefine `work` / `document` / other core `by_type` entries.

## Provenance

think-challenge 2026-09-03 before sign-off.
