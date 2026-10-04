---
type: page
title: Counter: overlapping schemas interfere unless split on large prediction error
created: 2026-10-04
work_id: 2026-10-04-four-level-disclosure
kva: alive
reality: current
status: settled
origin: third-party
sensitivity: internal
relates_to:
  - path: work/2026-10-04-four-level-disclosure/hub.md
    kind: implements
  - path: work/2026-10-04-four-level-disclosure/theory.memory.md
    kind: counters
  - path: work/2026-10-04-four-level-disclosure/counters.memory.md
    kind: related
---

## What happened

Engaged counter, kept. Overlapping schemas can catastrophically interfere. Splitting models avoid that when a large prediction error creates a separate representation. Blocked training on a new structure can outperform interleaving if the error is large enough to split; below that threshold a shared representation can be better. Source: Beukers and colleagues, Communications Psychology, 2024, https://www.nature.com/articles/s44271-024-00079-4.pdf

Applied here: do not mint a second schema for a small drift. Do split when the subject change is a large prediction error against the current schema. One schema still groups the gists of one subject.
