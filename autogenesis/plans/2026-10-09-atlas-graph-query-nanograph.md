---
type: plan
title: "Design — graph queries for Atlas, and whether nanograph replaces BM25"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: approved
approval_ref: "Sergio, 2026-10-09 13:54 BST: \"Let's do A, B and C, enabling nanograph only the supported platforms (Mac in this case). Let's make sure we have a driver overlay, in case we want to ship other drivers for Windows and Linux, but focus on nanograph for now\""
change_class: new-surface
description: "Approved (revision 1): keep SQLite FTS5 as default BM25, make --engine bm25 real with a labelled any-word retry, add a dependency-free atlas graph surface for discuss, add a nanograph export, and add a driver overlay whose only external driver is nanograph, enabled on macOS arm64 when the binary is detected."
origin: derived
sensitivity: internal
stage: implement
plan_path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
kva: forming
relates_to:
  - path: work/2026-10-09-atlas-graph-query-nanograph.md
    kind: implements
  - path: work/atlas-bm25-and-live-migration-v1.md
    kind: related
  - path: autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md
    kind: follows
  - path: autogenesis/discuss/recall-architecture/contract-proposal.md
    kind: derived_from
  - path: autogenesis/discuss/recall-architecture/smr-smo-boundary.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md
    kind: related
  - path: autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md
    kind: related
  - path: lessons/2026-08-27-search-harness-before-bm25.md
    kind: related
  - path: lessons/2026-09-09-opt-in-ranked-after-fast-path.md
    kind: related
  - path: autogenesis/plans/leaves/p-fts5-bm25-index.md
    kind: related
  - path: atlas-project/landscape/md-graph.md
    kind: related
---

# Graph queries for Atlas, and whether nanograph replaces BM25

Work ID: `2026-10-09-atlas-graph-query-nanograph`

Change-class: **new-surface**. It adds a CLI command group (`atlas graph`), an export format and, behind a gate, a new external driver. It does not create a skill, so it is not `new-skill`. It is more than a contract tweak, so it is not `hardening`.

Subject: Atlas. Baseline: `sergio-sisternes-epam/atlas` `main` at `b0b1012` (Release v0.13.0). Store: `github.com/sergio-sisternes-epam/atlas-atlas`, branch `main` at `e79aef0`.

Status: **approved with a direction change (revision 1).** Implementation of packets A, B and C is authorised.

## Revision 1 (2026-10-09, 13:54 BST): Sergio's decision

Approval, verbatim: "Let's do A, B and C, enabling nanograph only the supported platforms (Mac in this case). Let's make sure we have a driver overlay, in case we want to ship other drivers for Windows and Linux, but focus on nanograph for now".

He gave it straight after being told that nanograph ships only `aarch64-apple-darwin` binaries (every release from v0.8.1 to v1.3.0), that npm `nanograph-db` is macOS-only, and that a source build needs Rust 1.94.1 and `protoc`.

What changes:

- Packets A and B proceed as designed, with the recommended defaults for open questions 2 and 6: FTS5 retries with any-word matching when all-words finds nothing, and labels it in the output; `atlas graph` shares projection code with recall but stays a separate command.
- Packet C is reshaped into a **driver overlay**: a small documented driver interface with a registry and a platform-support matrix. Built-in drivers (SQLite FTS5 for BM25, native Python for graph) stay the default everywhere. nanograph is the only optional external driver. It is enabled only on a supported platform (macOS arm64 today) **and** when a `nanograph` binary at or above the minimum version is detected. Anywhere else it reports `unavailable on <platform>` and Atlas falls back with no error. Windows and Linux drivers are future slots in the matrix, not built.
- The old gate G-N (Linux binaries, a release in the last 90 days, a live probe before admission) is **dropped** in favour of this platform gate. Why: Sergio wants the capability where it can run today, and the overlay keeps the risk local. An absent or unsupported binary changes nothing for anyone else, the built-in drivers remain the default, and the export keeps data portable if upstream stalls (counter C1). The live probe becomes a manual check on Sergio's Mac rather than an admission gate.
- Open questions 3 and 4 (container build; upstream issue) are closed as not needed. Open question 5 (store move) is unchanged.

The original design text below is kept for provenance. Where it conflicts with this revision, this revision wins; P10 and P11 are replaced below.

## The request and what it turned out to mean

Sergio asked for a formal design to discuss, and possibly replace, Atlas's BM25 approach with nanograph. A key consumer is the `discuss` skill, whose lint, protostar search and consolidate views are graph questions answered today by walking files.

Two facts in the baseline change the question:

1. **`--engine bm25` is not BM25.** On a SCHEMA 1.0 store, `atlas recall run --engine bm25` calls `_bm25_search` in `scripts/atlas_cli/commands/search.py`. That function always returns a warning and falls back to grep, even when `.atlas-index/` exists ("BM25 engine not yet implemented in this CLI build"). The probe confirmed `engine_used: grep`. Real BM25 lives in the SMR pipeline as profile `atlas:ranked`: SQLite FTS5 `bm25(pages_fts, 0, 5, 2, 1)` over title, description and body. It needs SCHEMA 2.0 plus `recall activate`, and `recall index build` or compile publishes it. Both stores probed are still SCHEMA 1.0 with recall off. So most stores get grep today whatever the flag says.
2. **Atlas already has a graph.** The projection (`core/projection.py`) parses every page's `relates_to` into edges. `core/retrieve.py` already does bounded breadth-first neighbourhoods, in both directions, with exit-state filtering. The published generation already stores `edges_json` per page. What is missing is a query surface that is not tied to a text query, works on SCHEMA 1.0 stores, and accepts any frontmatter field. That gap is why discuss still walks files with regular expressions.

So the design question is now two questions. Should nanograph replace or join SQLite FTS5 for ranked recall? And what graph capability should Atlas expose, and on what engine?

## Store resolution and recorded contradictions

- The brief cites a standing decision that atlas-atlas moved into the atlas repo's `atlas` branch as an orphan commit. **The move has not happened.** `git ls-remote` on `sergio-sisternes-epam/atlas` shows no `atlas` branch. `atlas-mesh.json` on `main` still lists `github.com/sergio-sisternes-epam/atlas-atlas`. The repository `sergio-sisternes-epam/atlas-atlas` is not archived and was last pushed 2026-10-06. The move plan dated 2026-10-08 names release `v0.13.0-beta.14`; `v0.13.0` shipped instead, without the move. This Run therefore writes to atlas-atlas, the store that actually exists. When the move lands, this page moves with the squash.
- `atlas-mesh.json` lists **two** stores (atlas-atlas and atlas-cartograph-atlas). Autogenesis rules make that ambiguous unless the id is explicit, so this Run used the explicit id `github.com/sergio-sisternes-epam/atlas-atlas`, the Autogenesis store for subject Atlas, as in earlier Runs.
- The mesh row pins `ref: docs/skill-help-pilot`, which is 6 ahead of and 29 behind `main`. Atlas's own SKILL.md card says `ref: main`, and earlier Autogenesis Runs opened their PRs against `main`. This Run mounted the store, resolved it, and branched from `origin/main`.
- The store's `.gitignore` does not list `.atlas-index/`, and Atlas does not add it anywhere. A store with recall enabled can therefore commit its SQLite generations through `git add -A`. A nanograph `.nano` folder would make that much worse. Pin P9 addresses this.

## Source memory and authority

| Memory | Design use |
|---|---|
| `work/atlas-bm25-and-live-migration-v1.md` | Older BM25 work, still draft. Coordinate with it; do not close or absorb its okf-wiki migration scope |
| `autogenesis/plans/2026-09-09-atlas-smr-configurable-recall.md` | Coarse/Rank/Retrieve stages, driver capabilities, the tgrep gate this plan copies |
| `autogenesis/discuss/recall-architecture/contract-proposal.md` | Graph direction (incoming `implements`), limits, freshness and coverage rules |
| `autogenesis/discuss/recall-architecture/smr-smo-boundary.md` | Skills own meanings (KVA, stance kinds); Atlas runs generic predicates |
| `autogenesis/discuss/recall-architecture/decision-grep-then-ranked.md` | Grep stays the basic default; `atlas:ranked` is the opt-in default |
| `autogenesis/discuss/recall-architecture/decision-fast-path-fts5.md` | Cheap fingerprint gate; reuse it for graph reads |
| `autogenesis/discuss/recall-architecture/decision-tgrep-subprocess.md` | Precedent for an external binary: argv only, pinned, never serve, honest unsupported diagnostic |
| `lessons/2026-08-27-search-harness-before-bm25.md` | Filter on frontmatter first; the index is rebuildable and never merged across branches |
| `lessons/2026-09-09-opt-in-ranked-after-fast-path.md` | Measured `atlas:ranked` against grep on this store |
| `atlas-project/landscape/md-graph.md` | Earlier symbiont idea: graph plus FTS5 over Markdown, not a second store of record |

## Evidence

### nanograph, as checked on 2026-10-09

| Question | Finding | Source |
|---|---|---|
| Licence | MIT | GitHub API; `LICENSE` at tag `v1.3.0` |
| Release cadence | 15 releases from 2026-02-20 to 2026-05-16, then none. Last push 2026-05-17 (a reverted 1.3.1). Nearly five months quiet. One main contributor (112 of 113 commits). 157 stars | GitHub API |
| Platforms | Release assets for every release from v0.8.1 to v1.3.0: `aarch64-apple-darwin` tarball and a Swift xcframework only. **No Linux or Windows binary.** npm `nanograph-db@1.3.0` ships only `nanograph.darwin-arm64.node`, and its install script throws on Linux. Homebrew tap is the documented install | GitHub release API; npm tarball inspected, integrity verified |
| Binary size | macOS tarball 62 MB compressed (v1.3.0). The Node addon is 166 MB unpacked. Atlas today is pure Python plus the standard library's `sqlite3` | Release assets; npm tarball |
| Source build | `cargo install nanograph-cli --locked` needs Rust 1.94.1 (`rust-toolchain.toml`) and `protoc`. lance 6.0.0 needs Rust 1.91 or later; datafusion 53 needs 1.88 or later | README; crates.io |
| Python access | None native. SDKs are TypeScript (napi) and Swift. Python would call the CLI as a subprocess with `--format json`, as Atlas already does for tgrep | Docs |
| Storage | A `<name>.nano/` folder of Lance datasets: one per node type and per edge type, plus snapshot, transaction (CDC) and tombstone tables. Binary. Upstream advises gitignoring it and keeping `schema.pg` and seed JSONL in git | `docs/user/folder-structure.md` |
| Seed format | JSONL: nodes `{"type","data"}`, edges `{"edge","from","to"}` resolved by `@key`. `export --format jsonl` writes the same shape | `docs/user/cli-reference.md` |
| BM25 | Two paths. With `@index` on a `String` property, a Lance inverted index (positions on, no stemming, no stop words, no ASCII folding). Without it, an in-engine scorer (k1 1.2, b 0.75) that computes document frequency over the rows reaching it, which is how graph-constrained ranking works. Tokens split on non-alphanumerics and lower-case **ASCII only**. `bm25()` takes one property, so Atlas's title/description/body weights need `rrf()` or a concatenated field. Query terms are ORed | `crates/nanograph/src/plan/planner.rs`, `store/indexing.rs`, `store/runtime.rs` at `v1.3.0` |
| Determinism | Scoring sums over `AHashMap` iteration, so tie order is not guaranteed between runs. Queries need an explicit secondary `order` key. Not measured, because no binary ran | Source reading |
| Offline, no embeddings | Possible: a schema with no `Vector`/`@embed` never calls a provider. Providers are OpenAI, Gemini, LM Studio and a mock | `docs/user/embeddings.md` |
| Query language | Typed Datalog with GraphQL-shaped syntax. Conjunctive `match`, `not {}`, bounded hops `{1,3}`, aggregates. **No OR, no optional match, no recursion.** Traversal cannot bind edge properties, so each relation kind must be its own edge type. Edge endpoints are fixed to one source and one target node type | `docs/user/queries.md`, `docs/user/schema.md`, `query.pest` |
| Lineage and CDC | `NamespaceLineage` keeps a change ledger and time travel. Redundant here, because git already holds history and the index is rebuildable | Docs |

### Fail-fast probe (scratch, `/workspace/nanograph-probe/`)

**The live nanograph half is deferred**, for the platform reasons above. The binary cannot be obtained for Linux, and a source build needs a newer Rust and `protoc`, which belong to Grand Maester. The Atlas half ran in full on copies of two stores:

| Measure | atlas-atlas (470 pages) | waza-apm (36 pages) |
|---|---|---|
| Edges exported / dangling | 2,099 / 0 | 125 / 0 |
| Distinct relation kinds (= nanograph edge types needed) | 19 | 6 |
| Seed JSONL size | 1.8 MB | 0.2 MB |
| Current-tree projection | 0.12 s | 0.01 s |
| `--engine bm25` engine actually used | grep (stub) | grep (stub) |
| CLI median, grep | 0.19 s | 0.11 s |
| CLI median, `atlas:ranked` fast path | 0.15 s | 0.11 s |
| Top-5 overlap, nanograph-formula replica vs `atlas:ranked` (queries where ranked returned 5 or more) | 0.71 mean over 11 queries | 0.90 mean over 6 |
| Top-10 overlap, same | 0.76 | 0.83 |
| Graph question "forming protostars `derived_from` X", Python over the projection | 3 ms, 8 children of `autogenesis/plans/2026-08-27-atlas-landscape-review.md` | 0.3 ms |
| 2-hop "forming protostars under anything that implements the work hub" | 9 | 0 |
| discuss `lint.py` wall clock | 0.07 s, FAIL (findings below) | 0.04 s, PASS |

The replica is a Python port of nanograph's non-indexed `bm25()` formula over title, description and body joined together. It is evidence about the formula, not about the binary. One query shows the main semantic gap: `memory layers gist` returns 0 hits from `atlas:ranked`, because the FTS5 driver ANDs every token, and 10 hits from the OR-semantics replica.

At these sizes speed is not a reason to change engines. Python graph questions take milliseconds; CLI start-up dominates every timing.

discuss `lint.py` on atlas-atlas reported real findings: one L4, three L2 (`kva: surviving`), one L6 and two L1. One L1 flags `work/2026-08-26-atlas-modular-graph-protocol.md` because 18 protostars `implements` it. Discuss's own sprout rule requires protostars to `implements` their work hub. That is a contradiction inside discuss, not an Atlas problem; it is recorded under discuss consequences below.

## Recommendation

**Complement, not replace, and not nanograph first.**

- Keep SQLite FTS5 as Atlas's BM25 engine. nanograph's BM25 is lexically weaker for Atlas: ASCII-only case folding, no field weights, no prefix or phrase operators, unstable ties. It also adds a 60 MB-plus binary that does not exist for Linux, and it ran no faster at Atlas sizes.
- Fix the stub instead. `--engine bm25` should run the existing FTS5 driver.
- Build the graph capability discuss needs **natively** on the projection Atlas already has, with no new dependency.
- Give nanograph an **export** now (schema plus seed, pure Python), so anyone can load an Atlas into nanograph. Admit it as an optional external **driver** later, only if gate G-N passes.

"Potentially replace" was Sergio's framing. The evidence does not support replacement.

## Pinned decisions

| # | Decision |
|---|---|
| P1 | SQLite FTS5 (`sqlite-fts5` driver) stays the BM25 engine and `atlas:ranked` stays the opt-in default. nanograph does not replace it. |
| P2 | `atlas recall run --engine bm25` stops being a stub. With recall disabled, it ranks with the `sqlite-fts5` driver: the published generation when the cheap fingerprint matches, otherwise an ephemeral index built from the current-tree projection and deleted after the query. Output reports `engine_used: sqlite-fts5` and `ephemeral`. If the local `sqlite3` lacks FTS5, it falls back to grep with the existing warning. Grep stays the default when no flag is passed. |
| P3 | New command group `atlas graph` with four verbs: `nodes`, `edges`, `neighbours`, `export`. They work on every store (SCHEMA 1.0 and 2.0, CONTRACT.json and SCHEMA.json) whether recall is on or off. There is no Atlas graph query language in v1. |
| P4 | Graph reads use the same projection and coverage rules as recall: eligible paths, staging excluded, log role excluded. Reuse the published generation when the cheap fingerprint matches; otherwise project the current tree in memory. No new index, no new table in v1. |
| P5 | Atlas stays semantics-free. `--where field=value` filters on any top-level scalar frontmatter field, compared as text, with `true`/`false` and numbers normalised. Atlas does not know what `kva`, `growth` or stance kinds mean. The existing exit-state rule (terminated, deprecated, superseded hidden unless `--include-exits` or explicitly filtered) applies to returned nodes, as in recall. |
| P6 | Edges keep their authored direction: the page holding `relates_to` is the source. `--direction in|out|both` is explicit on `edges` and `neighbours`. Hops are capped at 3, with existing node and edge limits, cycle-safe, and `truncated: true` when a cap bites. Unresolved targets are returned with `resolved: false` (and `external: true` for `atlas://`), never silently dropped. |
| P7 | Output is deterministic: sorted by hop, then path, then kind. JSON carries `generation`, `corpus_digest`, `fast_path` and `complete`, as recall does. |
| P8 | `atlas graph export --format nanograph --out <dir>` writes `schema.pg` and `seed.jsonl` in pure Python. Mapping: one `Page` node type, `@key slug` = store-relative path, OKF `type` as a property (OKF types are open, and nanograph edge endpoints are fixed per type, so subtypes would multiply edge declarations). Scalar frontmatter becomes nullable properties; `text` = title, description and body. One edge type per relation kind actually present, plus any declared in the effective schema, named in PascalCase (`kva_terminate` becomes `KvaTerminate`, queried as `kvaTerminate`). `atlas://` targets become `External` nodes. No `Vector` fields. `--format json` writes the same graph as plain JSON for other tools. |
| P9 | Compile and any index build make sure `.atlas-index/` is ignored: they add it to the store's `.git/info/exclude` when the store is a git checkout and the pattern is missing, and report that they did. They never edit a committed `.gitignore` without the path that owns it. |
| P10 (superseded by P15–P19) | A `nanograph` driver (Rank stage, plus a graph backend for `neighbours`) is **gated**. It is admitted only through a new design amendment after gate G-N passes. Its shape is fixed now so the gate has something to test: argv subprocess only; pinned version and SHA-256; capability probe; database at `.atlas-index/nanograph/<generation>/`; rebuilt with `init` and `load --mode overwrite` from the P8 export when a generation is published; no `.env.nano`; no embeddings; fail closed with `unsupported_capability: nanograph_binary_missing`; never a default; never a server. |
| P11 (dropped in revision 1) | Gate G-N, all required: (1) official Linux x86_64 and arm64 binaries with published checksums, or a box-restore entry approved by Grand Maester; (2) an upstream release within the last 90 days, or a named maintained fork; (3) the live probe on atlas-atlas: top-10 overlap with `atlas:ranked` of at least 0.7 on the evaluation query set, graph answers identical to `atlas graph` on the fixed graph cases, two runs give identical order, and it runs with networking blocked; (4) the result shows something native Atlas cannot do at Atlas sizes. |
| P12 | Python reaches nanograph only through the CLI. No TypeScript or Swift bridge. |
| P13 | Discuss changes are not made here. They need their own Autogenesis design with discuss as subject, after this plan ships. This plan lists what discuss would use. |
| P15 | **Driver overlay.** A documented driver interface: `id`, `capabilities` (subset of `bm25_search`, `graph_traversal`), `platforms` (supported `sys.platform`/machine pairs), and lifecycle methods `detect()` (returns available or an unavailable reason), `build(export_dir, index_dir)`, `query(...)` per capability, and `health()`. A registry lists drivers and a platform-support matrix. Built-ins `sqlite-fts5` (BM25) and `native-graph` (Python) are always registered, always available and the default. |
| P16 | **nanograph driver.** The only external driver. Supported platform: macOS arm64 (`darwin`/`arm64`) only. Enabled when the platform matches **and** `nanograph` is found on PATH (or `ATLAS_NANOGRAPH_BIN`) at minimum version 1.3.0, read from `nanograph --version`. Otherwise `detect()` returns `unavailable on <platform>` or `binary not found` or `version below 1.3.0`, and callers fall back to built-ins with an informational note, exit code unchanged. Argv subprocess only, with timeouts. Never a server. |
| P17 | **Selection.** Built-ins stay the default. nanograph is used only when explicitly asked: `atlas recall run --engine nanograph` and `atlas graph neighbours --driver nanograph`. When unavailable, output carries `driver_used: <built-in>` and `driver_note: "nanograph unavailable on <platform>"`. `atlas graph drivers` lists the matrix and detection results. |
| P18 | **Index and build.** The nanograph database lives at `.atlas-index/nanograph/<generation>/` (generation = corpus digest prefix), built from the pure-Python P8 export with `nanograph init` and `nanograph load --mode overwrite`. Rebuilt when the digest changes. No `.env.nano`, no vector fields, no embeddings, no network. |
| P19 | **Future slots.** Windows and Linux rows exist in the matrix as `planned: none`. No other external driver is built. |
| P14 | Implementation runs through Copilot CLI only: `env -u GH_TOKEN copilot -p "<packet prompt>" --model claude-opus-5.5`, a fresh session per packet, never `--continue`. |

## Genesis Artifacts

### Intent and scope

Give agents and skills a deterministic, dependency-free way to ask an Atlas graph questions: which pages match these frontmatter values, what points at this page and with which kind, what lies within N hops. Make the BM25 flag do what it says. Let users load an Atlas into nanograph without making Atlas depend on it.

Trigger: an agent or skill (discuss lint, sprout, consolidate, constellation; Atlas recall's relates_to hop; Autogenesis) needs a set of pages or edges by structure rather than by words.

Dispatch description sketch (Atlas SKILL.md CLI surface; no new path module, because graph verbs are tools used inside paths `recall`, `work` and `remember`, like `recall run`):

> `atlas graph nodes|edges|neighbours|export` — structural lookups over the store's parsed `relates_to` graph and frontmatter. Use for "which pages have field=value", "what links to X and how", bounded neighbourhoods and exports. Not ranked search (use `recall run`), not compile.

### Non-goals

- Replacing SQLite FTS5 or changing `atlas:ranked`.
- A graph query language, an OR or optional-match grammar, recursion beyond 3 hops, or graph algorithms such as PageRank or communities.
- Embeddings, semantic or hybrid search.
- Making nanograph, Lance or any binary a required dependency, a default, or a server.
- Committing any index, `.nano` folder or seed into a store.
- Encoding discuss's rules (L1 to L6, stance kinds, KVA meanings) in Atlas.
- Closing or absorbing the okf-wiki migration half of `atlas-bm25-and-live-migration-v1`.
- Releasing, tagging or publishing; that belongs to Master of Packages.

### Component diagram

```mermaid
flowchart LR
  subgraph store["Atlas store (git, Markdown = source of truth)"]
    pages["md pages<br/>frontmatter + relates_to"]
  end
  subgraph cli["Atlas CLI (Python stdlib)"]
    proj["projection.py<br/>(existing)"]
    gen[".atlas-index/recall generation<br/>pages + edges_json (existing)"]
    fts["sqlite-fts5 driver (existing)"]
    recall["recall run<br/>--engine bm25 → fts5 (P2, changed)"]
    graph["atlas graph<br/>nodes | edges | neighbours (P3, new)"]
    export["atlas graph export<br/>json | nanograph (P8, new)"]
    ignore["ignore guard (P9, new)"]
  end
  subgraph gated["Gated by G-N (P10/P11, not in this approval)"]
    ngdrv["nanograph driver<br/>argv, pinned"]
    nano[".atlas-index/nanograph/GEN/x.nano"]
  end
  discuss["discuss lint / sprout /<br/>consolidate (later design)"]
  agent["agents, Autogenesis"]
  pages --> proj
  proj --> gen
  gen --> fts
  fts --> recall
  proj --> graph
  gen --> graph
  proj --> export
  ignore -.-> gen
  export -.-> ngdrv
  ngdrv -.-> nano
  graph --> discuss
  graph --> agent
  recall --> agent
```

### Interface sketch

```text
atlas recall run "<q>" --root <atlas> --engine bm25 [--json] [--limit N]
  -> engine_used: sqlite-fts5 | grep (only if FTS5 missing), ephemeral: bool

atlas graph nodes --root <atlas> [--where field=value]... [--path <prefix>]
                  [--include-exits] [--limit N] [--json]
  -> {nodes:[{path,type,title,kva?,status?,work_id?,fields:{...}}], count, generation, complete}

atlas graph edges --root <atlas> (--from <page> | --to <page> | --all)
                  [--kind K]... [--include-exits] [--json]
  -> {edges:[{from,to,kind,resolved,external?}], count}

atlas graph neighbours <page> --root <atlas> [--kind K]... [--direction in|out|both]
                  [--hops 1..3] [--where field=value]... [--max-nodes N] [--json]
  -> {seed, nodes:[{path,type,hop,...}], edges:[{from,to,kind,direction,hop}], truncated}
  (--where filters returned nodes; traversal passes through non-matching nodes)

atlas graph export --root <atlas> --format json|nanograph --out <dir>
  -> json: graph.json | nanograph: schema.pg + seed.jsonl + export-receipt.json
     (counts per kind, unresolved, corpus_digest)

Exit codes follow the CLI: 0 ok, 1 incomplete corpus (with --allow-partial), 2 invalid input.
```

How discuss would call it:

| Discuss need | Today | With this plan |
|---|---|---|
| Protostar search (`kva: forming` and `growth: true`) | `atlas recall run "kva:forming"` (no `growth:` token exists, and SKILL.md writes `kva: forming` with a space, which the parser reads as free text) | `atlas graph nodes --where type=protostar --where kva=forming --where growth=true --json` |
| Forming ideas born from node X | file walk | `atlas graph neighbours X --direction in --kind derived_from --hops 1 --where kva=forming --json` |
| Lint L1 to L6 | `lint.py` regex parses frontmatter and walks `rglob("*.md")`, with its own skip rules | `lint.py` keeps its rules but reads `atlas graph export --format json`, the same parse and coverage as compile and recall |
| Consolidate step 1 (hub, views, pages with `kva`) | agent reads files | `atlas graph neighbours <hub> --direction both --hops 2` plus `nodes --where consolidation=true` |
| Constellation | same as consolidate | same |
| L4 exit-reason checks | regex | `edges --from <page> --kind kva_terminate` plus `nodes` on the target |

### Cost note

- Runtime cost: none new for packets A and B. Standard library only; projection is about 0.12 s on 470 pages.
- Token cost: graph verbs return compact JSON (path, type, a few fields) so agents stop opening pages to discover structure. The recall path's 1-to-3 page reads remain the main cost.
- Maintenance cost: one command module plus tests. The nanograph export is a small pure-Python writer whose risk is drift in nanograph's schema grammar. It is pinned to the v1.3.0 grammar and tested by golden files.
- Gated packet C: 60 MB-plus binary per platform, a box-restore entry, upstream risk (see challenge), and a second BM25 implementation to keep in step.
- Implementation cost: Copilot CLI (`claude-opus-5.5`), about three packets.

### Acceptance

1. `--engine bm25` on a SCHEMA 1.0 store returns `engine_used: sqlite-fts5`. Its hits equal `atlas:ranked` on a 2.0 copy of the same tree for the evaluation queries.
2. `atlas graph nodes|edges|neighbours` give the same answers on SCHEMA 1.0 and 2.0 copies of one tree, with and without a published generation.
3. A discuss-rule replica built from `atlas graph export --format json` reproduces `lint.py`'s findings exactly on the discuss fixtures and on an atlas-atlas snapshot.
4. `atlas graph export --format nanograph` output is byte-stable across two runs and matches golden files. Every edge is either loaded or listed as unresolved.
5. After compile on a recall-enabled store, `git status --porcelain` shows nothing under `.atlas-index/`.
6. No new runtime dependency in `scripts/requirements.txt`. Existing tests stay green.
7. (Revision 1) On Linux CI, every nanograph path reports unavailable and falls back; the fake-binary tests exercise build and query; the live test is skipped with a reason.

### Stop for approval

This design stops here. Implementation needs Sergio's explicit approval of this persisted plan, naming which packets.

## SOLID lens

| Principle | Status | Rationale / design consequence |
|---|---|---|
| S | applicable | `recall run` stays ranked text discovery. `atlas graph` owns structural lookup. Export owns interchange. Three reasons to change, three surfaces. Graph verbs are tools, not a new path module. |
| O | applicable | Revision 1: the driver overlay is the governed extension point: new platform drivers are added by registering a driver, without touching recall or graph commands. Closed: recall semantics, `atlas:ranked`, grep default, exit-state rule. Open through the existing driver capability registry (P10), not a new plug-in system. Changing `--engine bm25` from stub to FTS5 is an intended, versioned behaviour change (CHANGELOG, minor bump). |
| L | trade-off | Interchangeability is claimed twice. `--engine bm25` must give the same hits as `atlas:ranked`'s FTS5 stage (acceptance 1). A future nanograph driver must match the native graph answers exactly and BM25 top-10 at 0.7 or more. Exact BM25 parity is not claimed, because the tokenisers differ; the driver must report its own `driver` field so callers can tell. |
| I | applicable | Four narrow verbs with flags, not one query language, following nanograph's own "one query, one tool" stance. Discuss needs `nodes` and `neighbours` for search and `export --format json` for lint. Nothing forces it to learn recall profiles. |
| D | applicable | Callers depend on the projection contract and on the driver interface (P15), not on SQLite, Lance or a binary. Revision 1 justifies the abstraction now: there are two real implementations per capability (built-in and nanograph) and announced future platform slots. |

## Catalogue Review

- Scope: in scope, narrowly, because P10 defines an extension contract (an external driver).
- Genesis matches: none for agent topology. This is a CLI and tool surface; no panel or fan-out.
- Autogenesis extensions: B17 ACTIVATION CARD unchanged (graph verbs run under the caller's card). `autogenesis:S8`: not selected, because no private skill module is added.
- Composition mode: INLINE for packets A and B (inside the Atlas CLI). EXTERNAL for nanograph (out-of-process binary behind capability probe).
- Inherited anti-patterns avoided: second store of record; automatic installation; daemon ownership (all from the tgrep decision).
- pattern_applicability: not-applicable (no new pattern). pattern_admission: not-selected.

## Behavioural contract (agent-spec)

Deferred: agent-spec is not in this harness's skill catalogue (`/home/box/agent-data/workflows` has no agent-spec package), so `specify` cannot run. Implement must run `specify` before packet B merges, or record a new deferral. Protecting scenarios to name there: `@critical` "`--engine bm25` never reports grep while FTS5 is available"; `@forbidden` "graph or export writes inside the store outside `.atlas-index/`"; `@forbidden` "any network call from graph, export or the nanograph driver".

## Evaluation plan

Deterministic smokes (primary):

| Check | Command or test |
|---|---|
| BM25 flag is real | New test in `scripts/test_recall_pipeline.py`: SCHEMA 1.0 fixture, `--engine bm25 --json`, assert `engine_used == "sqlite-fts5"`, and hits equal the 2.0 `atlas:ranked` copy |
| FTS5 missing fallback | Monkeypatch `fts5_available()` false; assert `engine_used == "grep"` and warning present |
| Graph parity across shapes | New `scripts/test_graph.py`: one tree as SCHEMA 1.0, 2.0 and CONTRACT.json; `nodes`, `edges`, `neighbours` JSON identical apart from generation fields |
| Direction and caps | Fixture with a cycle and a hub; `--hops 3`, `--max-nodes 2`; assert `truncated`, no duplicates, incoming `implements` found |
| Unresolved edges | Fixture with a missing target and an `atlas://` target; assert both returned with `resolved: false` |
| Exit-state rule | Terminated page hidden by default, shown with `--include-exits` and with `--where kva=terminated` |
| discuss parity | Test harness that runs `lint.py` and a small rule replica over `export --format json` on discuss fixtures and an atlas-atlas snapshot; finding sets equal |
| Export golden files | `export --format nanograph` twice; byte-identical; matches checked-in golden `schema.pg` and `seed.jsonl` for a fixture |
| Ignore guard | Temporary git store, recall on, compile; `git status --porcelain` empty under `.atlas-index/`; `.git/info/exclude` contains the pattern |
| No new dependency | `scripts/requirements.txt` unchanged; `python3 scripts/run_tests.py` green |
| Store compile | `atlas compile --root <store>` exit 0 on atlas-atlas after the change |

Agent evaluations (secondary): a recall-path trajectory check that an agent asking "what forming ideas came from X" uses `atlas graph neighbours` rather than a tree grep. Never the only evidence.

Gate G-N evaluation (packet C only, later): live probe script from `/workspace/nanograph-probe/bin/` against the binary, using `export/atlas.gq`.

## Adversarial scenario draft

Target file: `references/scenarios/graph-query-adversarial-v1.yaml` in the atlas repo.

```yaml
id: graph-query-adversarial-v1
packages: [atlas]
work_id: 2026-10-09-atlas-graph-query-nanograph
adversarial: true
expect:
  fts5_stays_bm25: true
  graph_is_dependency_free: true
  nanograph_is_gated: true
smokes:
  - id: bm25-flag-not-grep
    source: "Probe 2026-10-09: --engine bm25 returned engine_used grep on both stores; commands/search.py _bm25_search stub"
    expect: "With FTS5 available, --engine bm25 never reports engine_used grep."
  - id: no-required-binary
    source: "Counter C1 (KuzuDB archived Oct 2025, The Register); nanograph v1.3.0 ships macOS-only binaries"
    expect: "atlas graph and atlas graph export run with no nanograph, Lance or Rust present; requirements.txt unchanged."
  - id: no-index-in-git
    source: "Store .gitignore lacks .atlas-index/; nanograph folder-structure doc says gitignore .nano"
    expect: "After compile with recall on, nothing under .atlas-index/ is staged or untracked-visible."
  - id: authored-direction
    source: "recall-architecture contract-proposal: children point at hubs with implements"
    expect: "neighbours <hub> --direction in --kind implements returns the children; --direction out does not."
  - id: no-semantics-in-atlas
    source: "smr-smo-boundary: skills own meanings"
    expect: "No Atlas source file hard-codes discuss stance kinds or L1-L6 rules for graph verbs."
  - id: unresolved-visible
    source: "contract-proposal limits: unresolved external links visible"
    expect: "Missing and atlas:// targets appear with resolved false; export receipt counts them."
  - id: ascii-fold-gap
    source: "nanograph planner.rs tokenize_search_terms uses to_ascii_lowercase; atlas FTS5 uses unicode61"
    expect: "Any future nanograph driver reports driver nanograph on hits and is never selected by default."
  - id: deterministic-order
    source: "nanograph scoring iterates AHashMap; P7"
    expect: "Two runs of every graph verb give byte-identical JSON."
  - id: offline
    source: "nanograph embeddings doc: providers are network services"
    expect: "Graph, export and any nanograph driver make no network calls; no .env.nano is created."
  - id: graph-not-for-speed
    source: "Probe: Python graph answers in 3 ms on 470 pages; SQLite recursive CTE guidance for <5K nodes (SitePoint)"
    expect: "The plan's admission of nanograph cites capability evidence, not latency at Atlas sizes."
```

## Implementation packets

All packets: Copilot CLI only, `env -u GH_TOKEN copilot -p "<packet prompt>" --model claude-opus-5.5`, fresh session, never `--continue`. Each packet is one PR into `sergio-sisternes-epam/atlas` `main`, with tests.

| Packet | Content | Depends on |
|---|---|---|
| A | P2 (`--engine bm25` runs FTS5) and P9 (ignore guard). SKILL.md and `references/paths/recall.md` engine text updated. CHANGELOG | none |
| B | P3 to P8: `atlas graph nodes|edges|neighbours|export`, tests, golden files, SKILL.md CLI surface lines, `references/paths/recall.md` note that structural questions use `atlas graph` | A (shares projection reuse) |
| C | Revision 1: driver overlay (P15–P19), nanograph driver gated to macOS arm64 plus detected binary. Tests use a fake `nanograph` script and platform mocking so they run on Linux; one live test skips unless the platform and binary are present | B |

Release of A and B belongs to Master of Packages.

## Consequences outside Atlas

- **discuss** (separate Autogenesis design, subject discuss): switch `lint.py` input to `atlas graph export --format json` and drop its regex frontmatter parser; fix L1 so a protostar's `implements` edge to its work hub is not a shortcut (it contradicts sprout rule 5 today); correct SKILL.md to `kva:forming` and point protostar search at `atlas graph nodes`; let consolidate and constellation use `neighbours`. Discuss would need a minimum Atlas version.
- **Master of Packages**: releases for packets A and B (minor bump; `--engine bm25` behaviour change goes in CHANGELOG).
- **Grand Maester**: only if gate G-N is pursued. Rust 1.94.1 and `protoc`, or a nanograph Linux binary, would be new system tools.
- **box-restore**: a nanograph binary on the shared box would need a box-restore entry. Nothing is added now.

## Challenge and dispositions

Search-grounded counters (think-challenge), with dispositions:

| # | Counter | Source | Severity | Disposition |
|---|---|---|---|---|
| C1 | Young embedded graph databases can vanish. KuzuDB, MIT-licensed and popular, was archived by its company in October 2025, leaving users to pick forks; its file format had also been changing. nanograph has one main author and no release for nearly five months | The Register, 2025-10-14; github.com/kuzudb/kuzu (archived); GitHub API for nanograph | High | **Accepted.** P10 and P11: no required dependency, gate includes recent release or maintained fork; export keeps the data portable |
| C2 | At this scale SQLite already does the graph work. Practitioners report recursive CTEs fine up to about 5K nodes and 3 hops, with no new dependency; one team replaced Neo4j with 45 SQL statements | SitePoint, "Kùzu vs SQLite Recursive CTEs"; rohansx/ctxgraph blog; sqlite.org WITH clause | High | **Accepted.** P3 and P4 build graph natively. The probe answered in milliseconds in plain Python |
| C3 | Steel-man for nanograph: graphs do improve retrieval on multi-hop questions. gbrain reports P@5 rising from about 18 to 49 with typed-edge recall; the ICLR 2026 GraphRAG study finds graphs help on complex questions | garrytan/gbrain RETRIEVAL.md; ICLR 2026 "When to use graphs..." | Medium | **Modified.** The win comes from typed edges in retrieval, which Atlas already has and P3 exposes. It is not specific to nanograph. Kept as gate criterion (4) |
| C4 | The same study and a BEIR SciFact benchmark find graph expansion does not help, and can hurt, single-fact lookups, which dominate | ICLR 2026 paper Obs. 4; tahasiddiquii/hybrid-graph-rag (+3.9% nDCG only on 7.7% multi-evidence queries) | Medium | **Accepted.** Graph stays a separate verb; recall ranking is unchanged and `atlas:ranked-graph` stays opt-in |
| C5 | A query language is more expressive than four verbs. Without one, discuss must post-process | ctxgraph blog ("no native graph query language" listed as its main cost) | Medium | **Rejected for v1**, with reason: Atlas must not encode discuss's rules (SMO boundary), and nanograph itself argues for narrow tools. Revisit if a second skill needs the same post-processing |
| C6 | Internal: the probe's BM25 side is a formula replica, not the binary | This Run | Medium | **Accepted.** Recorded as deferred; gate G-N requires the live probe |

Named-theory smokes added: Hyrum's law (users may depend on `--engine bm25` returning grep-like results) is covered by the CHANGELOG entry and acceptance 1.

### C1 to C5 and Genesis check

| Criterion | Result |
|---|---|
| C1 non-trivial counter | Pass: six counters, four grounded externally |
| C2 high-severity counters disposed | Pass: C1 and C2 accepted and pinned (P10, P11, P3, P4) |
| C3 pins visible | Pass: P1 to P14 |
| C4 scope intact | Pass: no implementation; discuss changes deferred to their own design |
| C5 no implementation | Pass: no product file touched |
| Change-class stated | Pass: new-surface |
| Genesis Artifacts complete for class | Pass: intent, scope, non-goals, one mermaid, interface sketch, cost note, acceptance, stop |

## Open questions for Sergio

1. **Approve packets A and B now and park C?** Recommendation: yes. A and B carry all the value discuss needs, with no dependency.
2. **Should FTS5 fall back to OR when AND finds nothing?** `memory layers gist` returns nothing today. Recommendation: yes, as a small addition to packet A, marked in output as `match: any`; keep AND first for precision.
3. **Should the live nanograph probe be built from source in a container** (podman, Rust 1.94.1 plus protoc, two compile jobs, scratch only)? Recommendation: not now. The box has about 4 GB free memory and the result cannot change P1. Ask Grand Maester only if Sergio wants gate G-N pursued.
4. **Ask upstream for Linux binaries?** Recommendation: optional. A GitHub issue on nanograph asking for Linux release assets is cheap, but it is an external post and needs Sergio's go-ahead.
5. **Should the atlas-atlas move to the `atlas` branch happen before packet A?** Recommendation: no dependency either way; do the move when planned and carry this page with the squash.
6. **Should `atlas graph` also be offered as a recall Retrieve driver (replacing `pages-graph` internals)?** Recommendation: no. Share the code, keep the surfaces separate.

**Approved 2026-10-09 13:54 BST** (revision 1 above): packets A, B and C as revised.
