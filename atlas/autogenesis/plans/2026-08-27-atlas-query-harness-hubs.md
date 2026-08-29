---
type: plan
title: "Plan — query-path harness and spine hubs"
created: 2026-08-27
work_id: 2026-08-27-atlas-query-harness-hubs
status: done
description: "Hardening: glossary-bounded query rewrite, spine pages for CLI evolution and BM25 ideas, query-path read of type/work_id. No new CLI verb. FTS5 and hit-card schema deferred to protostars."
origin: derived
sensitivity: internal
change_class: hardening
kva: forming
stage: design
plan_path: autogenesis/plans/2026-08-27-atlas-query-harness-hubs.md
relates_to:
  - path: work/2026-08-27-atlas-query-harness-hubs.md
    kind: implements
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: derived_from
  - path: experiences/2026-08-27-search-self-atlas-bm25-hard-query.md
    kind: derived_from
  - path: experiences/2026-08-27-search-self-atlas-cli-evolution-probe.md
    kind: derived_from
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: autogenesis/discuss/compile-type-contract/cli-compile-list-review.md
    kind: related
---

## Intent

Make the two query classes that failed on this store cheaper **without** a new search engine: (1) synonym / all-ideas, (2) synthesis / why / evolve. Agents rewrite from a bounded glossary, then search, then land on a spine page that lists the living cluster.

## Change-class

`hardening`

Agent procedure + two documents + glossary rows. No new CLI subcommand, no index file, no compile-flag inventory.

## Pinned decisions

1. **Glossary-bounded rewrite, not LLM expansion.** Second search may add at most a small set of alias tokens from `glossary.md` (and titles of already-opened `relates_to` pages). No free-form synonym generation.
2. **Spine pages are indexes, not essays.** They list living paths + one-line claims. Detail stays on experience/decision/protostar pages so the spine does not rot as a second SoR.
3. **No new CLI verb in this slice.** Honour `cli-compile-list-review.md`: compile = gate, search = ranked discovery. Do not hang inventory on compile again.
4. **Do not implement FTS5/BM25 here.** That remains `atlas-bm25-and-live-migration-v1` plus protostar `autogenesis/plans/leaves/p-fts5-bm25-index.md`.
5. **Do not change `search.py` output schema here.** Richer hit cards (print `work_id` / `kva` / match-field) is a protostar, not this packet.
6. **Query stays out of git-mesh.** No search design in `autogenesis/discuss/git-mesh/`.

## Scope (implement after approval)

- `references/paths/query.md`: after first `atlas search`, if the question is synthesis or the top hits are “mention-only,” rewrite using glossary aliases + optional `type:` / `work_id` from the question; run at most one extra search; then read 1–3 pages including any spine hit.
- `glossary.md`: add a **Search aliases** table (`bm25` → FTS5, `.atlas-index`, `search_engine`; `cli surface` → validate, compile, search, migrate, promote, init).
- New documents (short spines):
  - `atlas-project/cli-surface-evolution.md` (or `documents/` equivalent under this store’s free layout) — phase + 0.7.x timeline with `relates_to` to the implement experiences.
  - Expand `work/atlas-bm25-and-live-migration-v1.md` Outcomes with the idea list already gathered (FTS5, Azure projector, type-filter orthogonal, construct smokes). Do not write a second essay.
- `SKILL.md` query-path one-liner: rewrite from glossary; prefer spine / work hubs.
- Version bump only if SKILL contract text changes (patch).
- Remember + compile green on this store.

## Non-goals

- FTS5 / `.atlas-index` / sqlite-vec implementation.
- Changing `search.py` JSON or stdout columns.
- A `list` command or `--list-type` revival.
- Embeddings, Azure indexers, live okf-wiki migration.
- agent-spec Gherkin in this turn.
- Silent edits to other skills’ Atlases.

## Challenge

Internal think-challenge after the two self-Atlas probes. Grounded counters:

| Counter | Source | Severity | Pin |
|---------|--------|----------|-----|
| Query expansion over-adds terms and retrieves noise; rewrites can drift from intent. | Meilisearch query-rewrite RAG limits; Elastic rewrite guidance | high | Accept: aliases only from glossary + opened relates_to titles; cap extra tokens; keep original query as first search. |
| LLM query expansion fails when the model lacks corpus knowledge or the query is ambiguous. | LLM-based QE fails for unfamiliar/ambiguous queries (2025) | high | Accept: no generative expansion in this slice. |
| Hub / source pages go stale and become a second SoR. | Docs drift surveys; “documentation is already out of date” | high | Accept: spines are link indexes with one-line claims; remember path notes “update the spine when adding a cluster page.” |
| On a small corpus, more search ceremony is slower than following a known index. | Docsio: small docs sites do not need a search bar | medium | Accept in part: first search still runs; rewrite only on miss/synthesis. Do not add product search UX. |
| Bolting another flag onto the nearest CLI repeats 0.7.5. | `cli-compile-list-review.md` | high | Accept: this slice does not touch compile flags or search.py schema. |

## Genesis Artifacts

### Intent + scope + acceptance

See Intent, Scope, Non-goals, Acceptance below. Diagrams omitted (hardening).

### Acceptance

1. `query.md` names: first search → bounded rewrite → at most one extra search → read spine/work if present.
2. Glossary has a Search aliases table covering at least `bm25` and `cli surface`.
3. A CLI-evolution spine page exists and `relates_to` Phase 2–4 plus 0.7.5/0.7.6 implement experiences.
4. BM25 work hub lists the gathered ideas in Outcomes (not a duplicate essay).
5. `atlas compile --root references/atlas` exit 0.
6. No new CLI verb; `search.py` stdout schema unchanged.

## Catalogue Review

`catalogue_review: n/a` — no topology, gate, panel, or Enter/Exit change. Query-path prose + documents only.

## Behavioural contract (agent-spec)

`deferred: path-prose hardening and two spine pages; no new runtime CLI behaviour; specify when hit-card schema or FTS5 ships.`

## Evaluation plan

**Deterministic (primary)**

- Files exist: query.md contains `glossary` and `rewrite`; glossary contains `Search aliases`; CLI spine path resolves; BM25 work hub contains `FTS5` or `idea`.
- `atlas compile --root references/atlas` exit 0.
- `atlas search "cli surface" --root references/atlas` still runs (smoke: non-zero hits). Do not assert new stdout fields.

**Agent (secondary)**

- On a synthesis question, the agent’s second search uses an alias from the glossary table. Soft only.

## Adversarial scenario draft

Not materialised this slice (`deferred` with behavioural contract). When FTS5 or hit-card CLI ships, file `atlas/references/scenarios/query-harness-adversarial-v1.yaml` with smokes:

- `source: meilisearch-over-expansion` — rewrite that adds tokens absent from glossary is out of contract (forbidden).
- `source: cli-compile-list-review` — compile does not gain a list flag in this work.
- `source: docs-staleness` — spine page with no `relates_to` to living cluster is a warning in a later compile contract (out of this slice).

## Stop for approval

This path **stops here**. Do not implement SKILL/code until the operator approves this plan. After approval, activate Autogenesis path `implement` with the same `work_id`.
