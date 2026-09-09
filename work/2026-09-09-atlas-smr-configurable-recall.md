---
type: work
title: "Configurable Semantic Memory Recall with skill-owned organisation"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
status: implemented
description: "Implement configurable SMR stages and optional drivers, including argv tgrep coarse search, while third-party skills own SMO through SCHEMA extensibility."
origin: user
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/contract-proposal.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/smr-smo-boundary.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-json-configuration.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
  - path: experiences/2026-09-09-implement-tgrep-subprocess.md
    kind: records
  - path: experiences/2026-09-09-smr-kpi-bench.md
    kind: records
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: related
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: experiences/2026-09-09-smr-fast-path-probe.md
    kind: records
  - path: experiences/2026-09-09-smr-fast-path-product-bench.md
    kind: records
  - path: lessons/2026-09-09-smr-fast-path-published-fts5.md
    kind: related
  - path: lessons/2026-09-09-opt-in-ranked-after-fast-path.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md
    kind: related
  - path: autogenesis/plans/leaves/p-tgrep-serve-and-subset-rank.md
    kind: related
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: experiences/2026-09-09-implement-smr-configurable-recall.md
    kind: records
---

## Scope

Design Semantic Memory Recall (SMR) as configurable Coarse, Rank and Retrieve
stages. Explore existing scan/rg, FTS5 ranking, typed-edge retrieval and
microsoft/tgrep as complementary capabilities rather than interchangeable
engines.

Keep Semantic Memory Organisation (SMO) with third-party skills through
SCHEMA extensibility: domain types, fields, lifecycle meanings, relations,
templates, organisational conventions and skill setup remain skill-owned.
Atlas supplies generic validated bindings, projections and recall execution.

Define explicitly selected skill presets, host overrides, driver compatibility,
working-tree freshness, corpus coverage and a backwards-compatible transition
from current search behaviour.

## Status

**Implemented** in product source (Atlas 0.10.0).
Experience: [implement SMR](../experiences/2026-09-09-implement-smr-configurable-recall.md).
Canonical plan: [2026-09-09-atlas-smr-configurable-recall](../autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md).

## Accepted direction and decisions

- Scope is the wider SMR architecture; tgrep is one component.
- SMR stages are Coarse, Rank and Retrieve; SMO remains third-party skill-owned.
- Skills may supply optional recall presets; the store owner explicitly
  selects one. Installing a contribution does not activate its preset.
- [Configuration format decision](../autogenesis/discuss/recall-architecture/decision-json-configuration.md):
  JSON-only configuration initially, versioned JSON Schema Draft 2020-12,
  closed core/driver contracts and registered skill-owned extension schemas.
  Authored OKF page types and metadata remain open.

The approved plan also pins: legacy stores unchanged until opt-in; configure
path inside the existing Atlas skill; SCHEMA 1.0 to 2.0 upgrade with
compatibility preservation; safe YAML parsing for 2.0; current-tree
correctness; partial results only by explicit request; tgrep as argv
subprocess against a digest-keyed Atlas-owned index, never serve.

## Outcomes sought

- An approval-ready formal design for SMR stage composition and the SMO binding
  boundary, including contribution ownership and profile validation.
- A per-working-tree projection and freshness strategy that preserves eligible
  content, excludes staging and makes incomplete or invalid state explicit.
- A compatibility strategy for existing search configuration, filters and
  domain defaults without rewriting skill-owned content.
- An evidence-based driver assessment covering answer quality, coverage,
  indexing/update cost and search latency; tgrep adoption is not presumed.

## Memory and navigation

- [Discussion origin](../autogenesis/discuss/recall-architecture/hub.md):
  user scope choices, advisor handover provenance and observed source behaviour.
- [Architecture proposal](../autogenesis/discuss/recall-architecture/contract-proposal.md):
  stage composition, graph direction, freshness and suggested sequencing.
- [Current discussion branch](../autogenesis/discuss/recall-architecture/smr-smo-boundary.md):
  declarative bindings, skill-owned SMO and explicitly activated SMR profiles.
- [Accepted JSON decision](../autogenesis/discuss/recall-architecture/decision-json-configuration.md):
  configuration format and validation boundary.
- [Accepted tgrep subprocess decision](../autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md):
  argv index/search, digest rebuild, never serve.
- [Search KPI lesson](../lessons/2026-09-09-opt-in-ranked-after-fast-path.md):
  grep until opt-in; `atlas:ranked` wins speed and follow-up tokens after fast path.
- [Skill-pointer leaf](../autogenesis/plans/leaves/p-query-engine-kpis.md):
  keep that recommendation in Atlas `query` / `configure`.
- [Fast-path FTS5 decision](../autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md):
  skip YAML projection when cheap fingerprint matches.
- [Grep then ranked](../autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md):
  grep basic; `atlas:ranked` is the opt-in default.
- [tgrep improvement protostar](../autogenesis/plans/leaves/p-tgrep-serve-and-subset-rank.md):
  serve and subset Rank later; limited benefits now.

## Boundaries and related work

The existing [BM25 and live-migration work](atlas-bm25-and-live-migration-v1.md)
is related prior work, not renamed or closed by this card. Coordinate its
ranking scope during formal design; live okf-wiki migration is not a
prerequisite for this work.

Hosted search, Cartograph integration, store CI changes and publication of
unavailable advisor pages are outside the current scope. The next authority
gate is formal design and explicit approval, not implementation from discussion.
