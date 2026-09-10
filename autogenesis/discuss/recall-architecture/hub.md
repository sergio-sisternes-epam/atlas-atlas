---
type: document
title: "Recall architecture discussion: tgrep as one component"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "User selected wider Recall architecture rather than a standalone tgrep adapter; the handover is advisory, not implementation authority."
status: in-discussion
kva: alive
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/recall-architecture/contract-proposal.md
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/decision-json-configuration.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: autogenesis/plans/leaves/p-fts5-bm25-index.md
    kind: related
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: related
  - path: lessons/2026-09-09-search-kpis-speed-tokens-accuracy.md
    kind: related
  - path: autogenesis/plans/leaves/p-query-engine-kpis.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md
    kind: related
  - path: autogenesis/plans/leaves/p-tgrep-serve-and-subset-rank.md
    kind: related
---

## Objective and current reality

Canonical [work card](../../../work/2026-09-09-atlas-smr-configurable-recall.md):
implementing. Approved plan:
[2026-09-09-atlas-smr-configurable-recall](../../plans/2026-09-09-atlas-smr-configurable-recall.md).

Decide how Atlas Recall composes retrieval stages, including microsoft/tgrep.
The user initially asked to discuss embedding tgrep as another driver, using
an independent advisor's handover. When offered standalone-driver versus
wider-Recall scope, the user explicitly selected "Wider Recall architecture;
tgrep is one component".

This pins discussion scope only. It does not approve the advisor's packet
ordering, automatic background processes, or daemon ownership.
The narrower standalone-driver option was not selected; tgrep remains in
scope as a gated adapter. Formal design is approved; implementation is in
progress.

## SMR and SMO ownership refinement

The user names the retrieval pipeline Semantic Memory Recall (SMR), with
Coarse, Rank and Retrieve stages. Semantic Memory Organisation (SMO), including
schema extensions and skill setup, should remain the responsibility of
third-party skills. These user terms take precedence over the advisor's
earlier stage labels in the candidate architecture.

The user explicitly selected: "Skills may offer presets; the store owner
explicitly selects them". Installing a skill therefore does not select its
recall preset or change the host's active retrieval policy.

The proposed semantic-binding mechanism, profile syntax and compatibility
migration remain forming at
[smr-smo-boundary.md](smr-smo-boundary.md). This is not approval to implement.

## Accepted design decisions

- [JSON configuration](decision-json-configuration.md): the user approved
  JSON-only configuration with versioned JSON Schema validation, closed core
  contracts and explicit skill-owned extension points. OKF content remains open.

## Inputs and observed evidence

The user supplied "Atlas Recall - technical handover", dated 2026-09-09,
attachment filename `2026-09-09-atlas-recall-implementation-handover.md`.
It proposes Recall stages named Coarse Retrieval, Rank Retrieval and Semantic
Retrieval, preserving Markdown/git as source of record. It recommends a
pages/edges projector, graph expansion, FTS5 BM25, and optional measured tgrep.
Those proposals are inputs, not independently verified prior approvals.
The advisor's unpublished pages were not available in this checkout and have
not been reconstructed, published or treated as existing decisions.

Repository inspection of `scripts/atlas_cli/commands/search.py` confirmed:
grep currently tokenises free text, admits matches on any token, filters
metadata, applies title/description boosts and returns relates_to previews.
The BM25 implementation remains a warning-and-grep-fallback stub.
`scripts/atlas_cli/core/paths.py` defines the concept corpus; its Python
enumeration does not use gitignore. An optional single-token rg prefilter
already introduces a coverage distinction from pure Python scanning.

Atlas queries were `tgrep Recall bm25`, then the single glossary-assisted
rewrite `tgrep Recall bm25 FTS5 .atlas-index search_engine`. The selected
existing work hub is draft; its FTS5 child is forming, not an approved plan.
The rewrite also illustrates a relevance problem: tokenising `.atlas-index`
adds common `atlas` and `index` words and raises unrelated pages.

Upstream source: https://github.com/microsoft/tgrep/blob/d55b022023518646c90742f4761488dc95633b73/README.md
The README was retrieved from main; this was the main SHA observed during
the same inspection. Upstream documents empty initial-build responses,
partial-index responses, polling fallback, non-atomic reconciliation,
ignored/hidden-file exclusions and a default 64 MiB file-size limit.
It also states that flags widening hidden/ignored coverage bypass the index.
These are documented behaviours, not locally benchmarked results.

## Discussion state

The scope decision is usable and recorded (`kva: alive`). The architecture
proposal remains forming on the linked branch. No speedup, answer-quality
improvement, fresh-snapshot guarantee or successful tgrep integration is claimed.

## Persistence boundary

The discussion is saved locally in the subject Atlas mount, not published.
No product files remain changed. Mount normalisation briefly changed the
consumer mesh ref to HEAD; the original main declaration was restored.

Store-wide Discuss lint reports existing L1 connector findings in the
GitHub Spec Kit page and historical work hubs. They are outside this
discussion's scope; no historical graph pages were rewritten.
defer: historical L1 graph cleanup is outside the Recall discussion scope.
