---
type: experience
title: "2026-08-27 search self-Atlas: hard BM25 idea query"
created: 2026-08-27
work_id: atlas-bm25-and-live-migration-v1
status: raw
description: "Query-path test on this skill's own Atlas. Search for how search works, then all BM25 ideas. Grep found the cluster; synthesis needed many reads and synonym searches."
origin: internal
sensitivity: internal
tags:
  - atlas
  - search
  - query-path
  - bm25
relates_to:
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: implements
  - path: experiences/2026-08-23-implement-atlas-phase3.md
    kind: follows
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: atlas-project/landscape/sqlite-vec.md
    kind: related
---

## Context

User asked to test Atlas search on Atlas's own store (`references/atlas/`), then collect every idea on BM25, then judge how hard that was. A later easier query will test the hypothesis recorded in the linked lesson.

## What happened

Query path used `atlas search` only (no unbounded tree grep). Engine: SCHEMA `grep`.

- `how atlas search works` ranked `experiences/2026-08-23-implement-atlas-phase3.md` first (score 87). That page states the pilot: ranked grep, BM25 flag, fallback when `.atlas-index/` is missing.
- `bm25` ranked the same experience (14) then the draft work hub (8). Remaining hits scored 1–4. Many were “BM25 is out of scope here.”
- Ideas that did not use the token `bm25` lived under FTS5, `.atlas-index`, `relative-index-portable`, `answerability-concrete`, Azure AI Search, md-graph. Follow-up searches and `relates_to` hops were required.
- `--engine bm25` warned and fell back. `type:experience|work|decision|protostar` filters worked.
- The work hub `work/atlas-bm25-and-live-migration-v1.md` is a stub (draft, two construct names, almost no design).

## Outcome

Search can name the cluster. It cannot assemble “all ideas on X” when the hub is thin and synonyms are unindexed. Agent cost: one primary search, several type/synonym searches, ~10 page reads.

Hypothesis and cheaper fixes distilled to `lessons/2026-08-27-search-harness-before-bm25.md`.

## Follow-ups

- Done: CLI-evolution probe at `experiences/2026-08-27-search-self-atlas-cli-evolution-probe.md`.
- Lesson revised; Autogenesis design must not start from “implement BM25” as the first packet.
