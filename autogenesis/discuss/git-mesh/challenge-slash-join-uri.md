---
type: document
title: "Challenge — slash-joined atlas URI and regex split"
created: 2026-08-29
work_id: 2026-08-26-atlas-modular-graph-protocol
status: in-discussion
kva: alive
reality: current
description: "User lean: full path with /, # is heading, deterministic split of id. Think-challenge counters recorded."
origin: user
sensitivity: internal
stage: discussion
relates_to:
  - path: autogenesis/discuss/git-mesh/atlas-uri-vs-hash.md
    kind: derived_from
  - path: autogenesis/discuss/git-mesh/decision-id-normaliser.md
    kind: related
  - path: work/2026-08-26-atlas-modular-graph-protocol.md
    kind: implements
---

## User lean

Keep a familiar URI. Join id and in-store path with `/`. Keep Markdown `#` as heading. Atlas splits id from path with a deterministic rule (regex or equivalent). Extra CPU on resolve is acceptable.

## Challenge outcome (see chat)

The lean is sound **if and only if** the split is the same function as `normalise`: host plus exactly two path segments, remainder is in-store path, fragment is heading. A searching regex is the failure mode. GitLab-style extra group segments break a fixed two-segment org/repo rule. CPU is not the real cost.
---
