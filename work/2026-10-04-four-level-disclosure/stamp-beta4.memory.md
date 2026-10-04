---
type: page
title: Decision: contract stamp stays 0.13.0-beta.4
created: 2026-10-04
work_id: 2026-10-04-four-level-disclosure
kva: alive
reality: current
status: settled
origin: user
sensitivity: internal
description: Do not re-litigate the shipped contract stamp.
relates_to:
  - path: work/2026-10-04-four-level-disclosure/hub.md
    kind: implements
  - path: work/2026-10-04-four-level-disclosure/theory.memory.md
    kind: related
  - path: work/2026-10-04-four-level-disclosure/one-gist-counts.memory.md
    kind: related
---

## What happened

Decision already taken. The stamp on the contract shape reads 0.13.0-beta.4. It shipped via package v0.13.0-beta.5, pull request 46, merge 4e2da945. Do not re-litigate that stamp.

This store does not carry that stamp. Its file is SCHEMA.json with no atlas_release. An unknown or newer stamp on SCHEMA.json fails closed, and the current shape is written to CONTRACT.json. The decision fixes the stamp value. It does not authorise rewriting this store's contract during the discussion.
