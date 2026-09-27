---
type: experience
title: "Pin — relates_to with `ref` are not compiled (for now)"
created: "2026-09-27"
work_id: "2026-09-27-git-backed-versions"
status: in-discussion
kva: forming
reality: current
description: "Compile contract for off-tip links. Edges that carry ref are ignored by atlas compile path resolution for now, so tip compile stays cheap. Historical materialisation is deliberate recall, not a compile gate."
tags: [ref, compile, pin, claim-b, forming]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-27-git-backed-versions.md
    kind: implements
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: derived_from
  - path: autogenesis/discuss/git-backed-versions/pin-candidate-frontmatter-ref.md
    kind: follows
  - path: autogenesis/discuss/git-backed-versions/claim-b-summary-on-head-trial-in-git.md
    kind: related
  - path: autogenesis/discuss/git-backed-versions/open-pointer-shape.md
    kind: related
---

## Context

Sergio confirmed the edge-level `ref` shape (2026-09-27) and pinned compile behaviour: `relates_to` entries that carry `ref` are **not compiled for now**, because resolving history in compile makes the work much more expensive.

## What happened

### Pin (forming → ready to treat as current for this orbit)

1. Tip edges (`path` + `kind`, no `ref`) — compile resolves as today.
2. Off-tip edges (`path` + `kind` + `ref`) — compile does **not** resolve the blob at that revision. Do not fail the tip compile because the path is absent on HEAD.
3. Historical materialisation stays a deliberate, higher-cost recall step — not a compile gate.

### Consequences

- Compile and default indexing stay scoped to the active tip (matches consolidation rationale).
- Agents may still *write* `ref` edges as durable pointers; tools that walk history opt in later.
- A later compile mode (optional, expensive) could validate `ref` edges; that is out of scope for the “for now” pin.

### Still open after this pin

- How much of the trial subgraph leaves tip.
- Claim A (version hints on living pages).
- Whether absent tip path + missing `ref` remains a hard compile error (should stay yes).

## Outcome

Compile cost fence accepted for this orbit. Schema/implement still not authorised from Discuss alone.
