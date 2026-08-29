---
type: document
title: "Partner — Azure AI Search"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: alive
kva: alive
role: projector
label: projector
realization: true
description: "Remote search index over compile-green Atlas and other estate sources. Infrastructure under Foundry IQ."
origin: third-party
sensitivity: public
sources:
  - https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/foundry-iq-faq
  - https://azure.microsoft.com/en-us/products/ai-services/ai-search
relates_to:
  - path: atlas-project/microsoft-as-realization.md
    kind: derived_from
  - path: atlas-project/partners/foundry-iq.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Content

**Takes:** BM25 + vector index, indexers (including Cosmos), knowledge-base APIs.

**Must not take:** authorship. An indexed chunk without a git path + hash is not an Atlas claim.

Microsoft marketing sometimes names the product “Azure AI Search (Foundry IQ)”. In Atlas language they are stacked planes: Search = index, IQ = orchestrated retrieve.
