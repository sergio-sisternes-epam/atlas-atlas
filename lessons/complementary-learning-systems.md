---
type: lesson
title: "Complementary learning systems — fast episode store plus slow schema store"
created: 2026-09-03
status: stable
work_id: 2026-09-03-human-memory-model
description: "Hippocampus writes fast and sparse; neocortex integrates slowly. Un-interleaved fast cortical writes overwrite prior knowledge."
origin: third-party
sensitivity: public
sources:
  - uri: https://onlinelibrary.wiley.com/doi/10.1111/j.1551-6709.2011.01214.x
    note: "O'Reilly 2014 CLS review of McClelland, McNaughton, O'Reilly 1995"
  - uri: https://royalsocietypublishing.org/rstb/article/375/1799/20190637/23829/Integration-of-new-information-in-memory-new
    note: "Integrating new information in CLS; schema-consistent items"
  - uri: https://pmc.ncbi.nlm.nih.gov/articles/PMC9606815/
    note: "Bidirectional hippocampal–cortical replay for sequential experiences"
relates_to:
  - path: work/2026-09-03-human-memory-model.md
    kind: implements
  - path: lessons/consolidation-transforms.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
---

## Content

Complementary Learning Systems (CLS) splits memory into two stores with opposite write speeds.

The hippocampus learns rapidly with sparse, pattern-separated codes so similar episodes do not immediately smash into each other. The neocortex learns slowly with overlapping codes so it can extract shared structure. If the cortex is forced to accept new items at hippocampal speed, earlier knowledge is catastrophically overwritten.

Replay and interleaving are the transfer mechanism: the fast store reactivates episodes so the slow store can absorb them beside old knowledge. Offline hippocampal–cortical dialogue is bidirectional in later models, not only hippocampus driving cortex.

## Implication for Atlas

`remember` of a raw episode is the fast store. Promoting it into guidance, recipes, or “current theory” is the slow store and must not silently replace sibling pages. Compile / dream is the interleaving pass.
