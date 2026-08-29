---
type: document
title: "Partner — Azure Cosmos DB"
created: 2026-08-27
work_id: 2026-08-27-atlas-landscape-review
status: alive
kva: alive
role: projector
label: projector
realization: true
description: "Optional graph/document map of Atlas pages. Also used by Foundry Agent Service as session memory — that use is not Atlas SoR."
origin: third-party
sensitivity: public
sources:
  - https://devblogs.microsoft.com/cosmosdb/powering-memory-in-foundry-agent-service-with-azure-cosmos-db/
relates_to:
  - path: atlas-project/microsoft-as-realization.md
    kind: derived_from
  - path: atlas-project/azure-planes.md
    kind: related
  - path: work/2026-08-27-atlas-landscape-review.md
    kind: implements
---

## Content

**Takes:** derived graph of pages and `relates_to`; optional vector/FTS over projected documents.

**Must not take:** SoR. Foundry Agent Service `CosmosMemoryContextProvider` is **out-of-frame** as Atlas identity (session/user memory). Do not list it as a competitor; do not treat it as Atlas pages.

Anything that exists only in Cosmos is not on the blueprint.
