---
type: protostar
title: "Prediction error may choose update versus a second trace"
created: 2026-09-03
status: open
work_id: 2026-09-03-human-memory-model
kva: forming
growth: true
star_kind: probe
origin: third-party
sensitivity: public
description: "Small mismatch interferes with the original; large mismatch more often stores a separate version."
sources:
  - uri: https://pubmed.ncbi.nlm.nih.gov/42259243/
    note: "Competition between memory updating and differentiation; prediction-error weighted Hopfield-style model"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: lessons/reconsolidation-gated-update.md
    kind: derived_from
---

## Pending

Test whether Atlas `remember` should treat a small correction to an existing slot as `supersedes` on that slot, and a large contradiction as a new page with `contradicts`, without collapsing them in query.

## Origin

Grown from the reconsolidation lesson: the gate on whether retrieval updates or differentiates is modelled as prediction-error size. Similar follow-ups interfere; dissimilar follow-ups are stored separately; larger PE makes people more often recall two versions.

## Implication for Atlas

Do not auto-merge every contradiction into the parent page. PE-sized difference is still a forming rule, not compile law.
