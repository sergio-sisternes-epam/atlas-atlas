---
type: lesson
title: "Memory identity is a reactivable pattern, not a byte-stable file"
created: 2026-09-03
status: stable
work_id: 2026-09-03-human-memory-model
description: "An engram is a cell and synapse pattern that can be re-expressed. Molecules turn over; the pattern can last."
origin: third-party
sensitivity: public
sources:
  - uri: https://www.uclahealth.org/news/release/lost-memories-might-be-able-to-be-restored-new-ucla-study-indicate
    note: "Glanzman — long-term memory not stored as the encoding-day synapse set"
  - uri: https://www.wired.com/story/the-molecular-bond-that-helps-secure-your-memories/
    note: "KIBRA–PKMζ partnership; Crick molecular-turnover problem"
  - uri: https://www.nature.com/articles/s41380-023-02137-5
    note: "Engram encoding, consolidation, retrieval, forgetting"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Content

A biological memory is an engram: a sparse pattern of cells and synapses that can be reactivated together. It is not a document whose identity is an exact byte string.

UCLA / Glanzman work on Aplysia argues long-term memory is not stored as “the synapses that grew at encoding.” After reconsolidation disruption, which synapses remain does not match the original grown set, and a reminder can restore behaviour that looked erased. Storage and expression come apart.

Molecules at synapses turn over in days to weeks. One proposed stabilizer is a persistent partnership (KIBRA and PKMζ) that keeps location and association while individual proteins are replaced — Crick’s question of how a trace outlives its molecules.

## Implication for Atlas

Do not treat a page hash as the identity of a living belief. Identity for query is the current reactivable slot (status, kva, supersedes). The file is a snapshot of an expression, not the whole memory.
