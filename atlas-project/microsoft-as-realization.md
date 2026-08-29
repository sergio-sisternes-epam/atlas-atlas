---
type: document
title: "Microsoft products realize the Atlas blueprint"
created: 2026-08-27
description: "Cosmos DB, Azure AI Search, and Foundry IQ are enterprise-grade projectors of Atlas, not competitors."
origin: user
sensitivity: internal
status: alive
kva: alive
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/vision.md
    kind: derived_from
  - path: atlas-project/azure-planes.md
    kind: related
  - path: decisions/microsoft-products-realize-blueprint.md
    kind: records
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
---

## Content

Atlas does not compete with Microsoft knowledge products. Those products are the **enterprise-grade version of the same blueprint** when an organisation already runs Azure.

| Microsoft surface | Atlas plane it realises |
|---|---|
| GitHub / Azure Repos + PR + CI | SoR transport, review, `atlas compile` on the knowledge PR |
| Azure AI Search | Remote search index over compile-green pages |
| Azure Cosmos DB (NoSQL or Gremlin) | Optional graph map of pages and `relates_to` |
| Foundry IQ knowledge base | Agentic retrieval across the Atlas index **and** SharePoint, Fabric IQ, SQL, Web IQ (knowledge bases GA as of 2026-08 landscape pass; Search required underneath) |
| Foundry Agent Service memory | Working RAM (session / user / procedural) — not Atlas pages |
| Sensitivity labels + Entra | Enterprise enforcement of frontmatter `sensitivity` |

Rule: anything that exists only in Cosmos or IQ is not part of the blueprint. The blueprint is OKF + compile + types + work hubs + mesh/PR. Adapters carry a content hash back to a git path.

Default off. Skill-local Atlas must keep working with grep and no Azure credentials. That keeps the APM no-phone-home constraint.

## Provenance

User framing 2026-08-27. No prior Atlas pages existed for Cosmos / Search / Foundry IQ; this closes that gap as vision, not as an implementation plan.
