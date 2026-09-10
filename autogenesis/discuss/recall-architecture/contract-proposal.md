---
type: protostar
title: "Recall contract proposal: compose stages without conflating drivers"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Unapproved architecture proposal separating candidate discovery, ranking and typed-edge context, with working-tree correctness as a prerequisite."
status: open
kva: forming
growth: true
star_kind: refine
origin: derived
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/recall-architecture/hub.md
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: derived_from
---

## Pending

Refine and agree the Recall stage contract before entering formal Autogenesis
design. The following is one candidate architecture, not settled policy or a
finished behavioural contract.

## Candidate architecture

Terminology refined by the user: Semantic Memory Recall (SMR), with Coarse,
Rank and Retrieve stages. Third-party skills own Semantic Memory Organisation
(SMO). The ownership and configuration bridge is being refined on
[smr-smo-boundary.md](smr-smo-boundary.md).

Keep `atlas search` and the query skill path. Parse the query once into text,
metadata constraints and any explicitly designed traversal request.

Coarse Retrieval supplies candidate page identities. A scan/rg backend remains
available; tgrep is an optional accelerator, not a replacement query language.
Rank Retrieval orders candidates using the existing scorer or FTS5 BM25.
FTS5 can fuse candidate lookup and ranking: do not force every FTS5 query through
a separate tgrep pass. A trigram prefilter must not exclude documents admitted
by the selected ranker's tokenisation, case handling or OR/AND semantics.
Retrieve assembles page evidence and may expand typed edges from seeds, retaining direction,
provenance, hop distance and page traffic. Prefer separate ranked hits and
neighbourhood initially; blending scores needs an explicit policy.

Drivers and stages are different dimensions. Preserve existing `--engine`
behaviour through a compatibility mapping if the formal design introduces
stage-specific configuration. Do not pin new flag names during discussion.

## Correctness questions within this proposal

- Freshness: successful compile is not proof that a later dirty checkout
  matches the index. Choose current-checkout correctness with visible scan
  fallback, or an explicitly requested snapshot contract. Re-reading returned
  candidates cannot discover files missing from an obsolete index.
- Coverage: define eligible Atlas pages once, including custom staging
  exclusions and local authored pages. Align scan, FTS5 and tgrep against that
  definition rather than silently accepting each tool's default file set.
- Projection: a shared, gitignored, per-working-tree SQLite cache can hold
  pages, edges, FTS5 and version/freshness metadata. Publish atomically after
  validation; failed compile must not make an older projection look current.
- Direction: children usually point to a work hub with `implements`.
  Finding implementing children from a hub therefore needs incoming-edge
  traversal, not just outgoing edges. Define direction before adopting the
  advisor's `from:`/`kind:` examples.
- Limits: metadata and exit-state rules must also apply to expanded nodes.
  Exclude staging, bound depth/edges, handle cycles and unresolved external
  links visibly, and never infer that a high-degree hub is more relevant.
- Operations: tgrep needs readiness, root identity, complete corpus coverage,
  version compatibility and freshness evidence. Do not introduce automatic
  installation or daemon ownership without an explicit lifecycle decision.

## Suggested sequencing, not an approved plan

1. Agree answer semantics and representative quality/cost cases. Reconcile
   available memory with the advisor's unpublished source claims.
2. Build the shared page/edge projector and index validity contract.
3. Add title-weighted FTS5 ranking and separately bounded graph context,
   retaining the zero-index path.
4. Compare tgrep with that actual baseline. Count build/update costs, warm
   latency, filesystem work, memory and agent reads, not just upstream
   large-repository benchmark ratios.

The tgrep feasibility probe can occur earlier without making it the default
or blocking ranking and graph work. BM25 tokenisation is not automatically
equivalent to today's substring scoring, and 5/2/1 FTS5 weights are only a
starting hypothesis, not proof of behavioural equivalence.

## Boundary

Still discussion-only. No product implementation, migration, publishing of
missing advisor pages, store CI changes, hosted projector work or Cartograph
changes are authorised here. A later formal design must challenge the chosen
contract, persist an approval-ready plan and stop for explicit approval.
