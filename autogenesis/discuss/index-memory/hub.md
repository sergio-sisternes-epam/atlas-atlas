---
type: experience
title: "Hub — index.md as short-term memory"
created: "2026-09-18"
work_id: "2026-09-18-index-md-semantic-memory"
status: in-discussion
kva: alive
reality: current
description: "discussion_root for organising Atlas index.md as working memory, with two-layer recall."
tags: [index-md, short-term-memory, query, discuss]
origin: user
sensitivity: internal
relates_to:
  - path: work/2026-09-18-index-md-semantic-memory.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: related
  - path: decisions/atlas-memory-layers.md
    kind: related
  - path: work/2026-09-03-human-memory-model.md
    kind: related
  - path: autogenesis/discuss/index-memory/requirements.md
    kind: follows
  - path: autogenesis/plans/2026-09-18-index-md-semantic-memory.md
    kind: follows
  - path: autogenesis/discuss/index-memory/protostar-forget-path.md
    kind: related
  - path: autogenesis/discuss/index-memory/stm-artefact.md
    kind: follows
  - path: autogenesis/discuss/index-memory/layer-2-incomplete.md
    kind: follows
  - path: autogenesis/discuss/index-memory/compile-incomplete.md
    kind: follows
  - path: autogenesis/discuss/index-memory/order-hottest-first.md
    kind: follows
  - path: autogenesis/discuss/index-memory/heat-signal-insert.md
    kind: follows
  - path: autogenesis/discuss/index-memory/conclusion-approved-issue.md
    kind: related
---

## Context

Subject: treat Atlas `index.md` as short-term memory, and evolve query plus skill instructions around that.

Objective: extract and sort requirements, pin an Autogenesis design for the Semantic Memory Organisation core (index-first recall, then deeper search), park forget for later, and leave a plan that a GitHub issue can link.

This page is `discussion_root`. It does not move.

## What happened

The 2026-09-18 conversation framed `index.md` as the nearest memories, the ones an agent should scan first so it does not traverse the whole store. New memories join the index so they stay discoverable. Forget is wanted later, but access-count tracking is weak today, so that path is parked. Order-as-frequency was named, including a contested claim that the top of the index should eventually drop.

A cheap probe of current Atlas compile shows `index.md` is an OKF folder inventory (`index_md_present`), not an LRU working set. That tension is live on this hub.

## Outcome

KVA keep this thread alive. Requirements and the Autogenesis plan are the engaged expansions. Forget is a forming protostar. Batch questions stay here until picked 1-by-1.

## Batch still on the hub

0. Compile rule — engaged on compile-incomplete.md. Presence stays. Completeness goes. Dangling links fail.

1. Which artefact is STM — engaged on stm-artefact.md.
2. Order — engaged on order-hottest-first.md. Hottest at top. Forget later drops the bottom.
3. Who writes — engaged on heat-signal-insert.md. Remember inserts at top. Query is read-only.
4. Deeper recall — engaged on layer-2-incomplete.md. Unlisted pages are LTM.
5. GitHub issue — engaged. Lineage on conclusion-approved-issue.md.

Unexpanded later path: forget / access counts (protostar).
