---
type: document
title: "Atlas vision — git-native SDLC knowledge protocol"
created: 2026-08-27
description: "Living vision statement. Atlas plays in storage and behaviour, not in competing with Microsoft retrieval products."
origin: user
sensitivity: internal
status: alive
kva: alive
reality: current
work_id: 2026-08-27-atlas-vision-comparison
relates_to:
  - path: atlas-project/comparison-correct.md
    kind: related
  - path: atlas-project/microsoft-as-realization.md
    kind: related
  - path: atlas-project/sdlc-first.md
    kind: related
  - path: atlas-project/branching-model.md
    kind: related
  - path: atlas-project/wrong-path-agent-memory-layer/exit-wrong-comparison.md
    kind: related
  - path: decisions/atlas-is-storage-behaviour-protocol.md
    kind: records
  - path: work/2026-08-27-atlas-vision-comparison.md
    kind: implements
  - path: experiences/2026-08-23-atlas-name-pin.md
    kind: related
---

## Content

Atlas is a **storage and behavioural protocol** for how knowledge is allowed to exist during software work.

It is a modular, git-based, branch-friendly knowledge system. Multiple teams mount it, read it, and contribute back through pull requests. Compile is the gate that decides whether a page may be treated as a claim.

### What Atlas is

- OKF v0.2 trees as the portable artefact.
- Typed pages (experience, decision, lesson, recipe, work, document, protostar) plus authoritative `relates_to`.
- Work hubs as the SDLC unit of effort.
- Mesh + git checkout (submodule) + PR as the multi-team protocol.
- Local-first: a squad can start an Atlas in a repo they already own.
- Optional enterprise projectors (search index, graph map, Foundry IQ knowledge source) that **read merged claims**. They do not mint pages.

### What Atlas is not

- Not a chatbot personalisation layer.
- Not a managed fact-extraction API.
- Not a rival to Azure AI Search or Foundry IQ.
- Not a central ring-fenced institutional pool that only a budget owner can write.

### Why git, not only cost

Teams grow as they **branch their work**. Agents evolve knowledge as fast as they evolve code. Fixed infrastructure (one schema, one indexer, one gatekeeper) cannot keep up. A branch can hold a temporary truth, be reviewed, merge, or be discarded. That is the growth model.

Central pools ring-fenced by expensive tools and corporate budgets starve agent knowledge: the people doing the work cannot write the understanding of the work.

### Sequence

Show the problem space first with real SDLC Atlases. Grow the platform practices the discipline requires only after a second team has mounted an Atlas and landed a knowledge PR. Non-functional scenarios wait until the five SDLC stages produce repeating shapes.

## Provenance

User framing 2026-08-27, aligned with the 2026-08-23 name pin (compiled modular project knowledge, including requirements).
