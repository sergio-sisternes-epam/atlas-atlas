---
type: document
title: "Partner — Microsoft Foundry IQ"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: alive
kva: alive
role: projector
label: projector
realization: true
description: "Enterprise agentic retrieval over a knowledge base. Atlas pages can be a source. Not the birthplace of claims."
origin: third-party
sensitivity: public
sources:
  - https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/what-is-foundry-iq
  - https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/foundry-iq-faq
relates_to:
  - path: atlas-project/microsoft-as-realization.md
    kind: derived_from
  - path: atlas-project/partners/azure-ai-search.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Content

**Takes:** permissioned multi-source retrieval, agentic query planning, citations, Entra identity.

**Must not take:** SoR. Claims are born as compile-green Atlas pages (or other git sources), then projected.

2026-08 note: knowledge bases generally available; Azure AI Search is required underneath. New sources in preview include Fabric IQ, Work IQ, Azure SQL, MCP, Web IQ.

## Job test

IQ down must not stop a team from branching Atlas and opening a knowledge PR.
