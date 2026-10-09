---
type: experience
title: "Implement Run: real BM25 engine, atlas graph, driver overlay, .atlas/indexes and atlas index"
created: 2026-10-09
work_id: 2026-10-09-atlas-graph-query-nanograph
status: done
kva: alive
description: "Packets A–F of the approved plan (revisions 1–4) were implemented by fresh Copilot CLI sessions on atlas branch feat/graph-query-drivers (PR #61, head 37f1c3a): FTS5 bm25, atlas graph, driver overlay with nanograph on macOS arm64, indexes under .atlas/indexes/<driver-type>/<atlas-id>/, a self-refreshing preferred engine and the atlas index CLI. Not yet checked against a real nanograph binary."
origin: derived
sensitivity: internal
stage: implement
implements: work/2026-10-09-atlas-graph-query-nanograph.md
plan_path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
relates_to:
  - path: work/2026-10-09-atlas-graph-query-nanograph.md
    kind: implements
  - path: autogenesis/plans/2026-10-09-atlas-graph-query-nanograph.md
    kind: derived_from
  - path: autogenesis/experiences/2026-10-09-design-atlas-graph-query-nanograph.md
    kind: follows
---

## What was asked

On 2026-10-09 at 13:54 BST, Sergio approved packets A, B and C. Built-in drivers stay the default everywhere, and nanograph is enabled only on macOS arm64. A driver overlay leaves room for future Windows and Linux drivers. Only Copilot CLI writes product code, with a fresh session for each packet and no version bump.

## What was done

- **Branch:** `feat/graph-query-drivers` in `sergio-sisternes-epam/atlas`, from `b0b1012` (v0.13.0). PR [#61](https://github.com/sergio-sisternes-epam/atlas/pull/61), now at head `de8263d`: packets A–F, a merge of v0.13.1 from main, then six rounds of review fixes (it was `16c3b44` after packet C and `37f1c3a` after F). It is not merged and no Copilot review was requested.
- **Packet A, `58c6075`:** `--engine bm25` runs on SQLite FTS5 (fast path or a temporary index), with a labelled any-word retry and the `.atlas-index/` ignore guard.
- **Packet B, `d90ae24`:** `atlas graph nodes|edges|neighbours|export`, built on the shared projection, with golden nanograph export fixtures.
- **Packet C, `16c3b44`:** the driver interface, registry and platform matrix, plus the nanograph driver. It is gated to darwin/arm64 with version 1.3.0 or later, called with argument lists and timeouts, and run with embedding keys stripped. Its index lives under `.atlas-index/nanograph/<generation>/`. Commands added: `atlas graph drivers`, `--engine nanograph` and `--driver nanograph`.
- **Packets D to F** followed Sergio's later decisions (14:58, 15:01, 15:38 and 15:40 BST), recorded as plan revisions 2 to 4:
- **Packet D, `0a45cea` (revision 2):** `core/index_location.py`. Indexes move to `<project-root>/.atlas/indexes/<driver-type>/<atlas-id>/`, resolved in one of two ways:
  - mesh mode: the first `atlas-mesh.json` row whose path resolves to the store;
  - standalone mode: the store's git top level, with the origin id, or a `local/<name>-<hash8>` id when the store is not that top level.
  Ids are checked for safe paths. The guard puts `/.atlas/indexes/` in `info/exclude`, and a legacy `.atlas-index/` index is read only, with a warning, for 0.14.x.
- **Packet E, `230da26` (revision 3):** the preferred engine, with precedence `--engine` > `ATLAS_RECALL_ENGINE` > store row > project default > built-in default.
  - Indexes are created and refreshed automatically when the digest changes, at recall and at compile/validate.
  - Publishing is atomic (temporary folder, rename, pointer swap), with a `.lock` file.
  - Fallback runs nanograph → bm25 → grep.
  - On stores with their own recall profile, the profile wins: a bm25 preference is a no-op, and a nanograph/grep preference is ignored with a notice.
- **Packet F, `37f1c3a` (revision 4):** `atlas index set|unset|show|status|build`, with `--store`, `--default`, `--build`, `--all` and `--force`. Mesh writes are atomic and keep the file's formatting. `atlas recall index build` remains as a deprecated alias. A briefed `atlas recall engine` group was dropped for this shape before it was committed.
- **Tests and checks** on Linux x86_64, with no nanograph present:
  - After packet C: `run_tests.py` passed 23 entrypoints, and `release_readiness.py --commit 16c3b44` passed.
  - After packet F: `run_tests.py` passed all 26 entrypoints, and `release_readiness.py --commit 37f1c3a` passed. CI results are on the PR.
  - `apm audit` found no issues.
  - The diff scan found no private host name and no tokens.

## Review fixes (2026-10-09 evening)

Copilot's automatic reviewer left 12 unresolved threads on PR #61: 7 Blockers, 4 Recommended and 1 Nit. Sergio asked about them at 18:23 BST. All 12 were fixed in three fresh Copilot CLI sessions, each fix with a regression test. Each thread got a reply and was resolved.
- **R1 `a513b67`:**
  - external driver subprocesses get an allow-listed environment, and a deny pass strips GitHub/APM/Copilot tokens;
  - the platform override is injectable only through the test-only entry `scripts/testing/atlas_test_cli.py`;
  - the nanograph binary path is made absolute;
  - index locks carry an owner token, and stale takeover is guarded;
  - duplicate mesh ids are a validation error.
- **R2 `97e7ab9`:**
  - edge type names are collision-free, with a stable hash suffix, and the receipt records the mapping;
  - FTS eligibility is applied in SQL before the any-word retry is decided;
  - nanograph candidates are uncapped before Atlas filters them.
- **R3 `0c939d3`:**
  - CLI limits and caps are bounded;
  - SKILL.md has a per-verb `atlas index` synopsis and a single recall/graph routing rule.

`run_tests.py` passed all 30 entrypoints, and `release_readiness` passed.

After the fix push, the automatic review posted 4 new threads. Sergio asked at 19:17 BST for all four to be fixed in one session, and they were, in **R4 `8b263d3`**:
- freshness is decided by a content digest, and the path/size/mtime check can say only "stale". Cost on the 482-page atlas-atlas copy: a 48 ms digest, and a warm recall went from 161 ms to 206 ms;
- `graph neighbours`/`edges` refuse an exit-state starting page unless `--include-exits` is passed;
- ignore-guard failures are reported warnings, and `index show/status` report the ignore status;
- mesh writes are serialised under an owner-token lock.

The next automatic review posted 2 more threads. **R5 `db2052c`** fixed them:
- **Blocker:** nanograph `init` scaffolded `.env.nano` and `nanograph.toml` into the generation (confirmed in the v1.3.0 source). nanograph now runs in a private, empty working directory with the schema copy outside the index, its scaffolding is removed, and generations are scrubbed before publish.
- `graph neighbours --driver nanograph` now reports build warnings.

Two more Recommended threads followed. **R6 `ec68f0c`** fixed them:
- the nanograph neighbours caps now bound the subprocess calls, not just the output;
- lock release is serialised under the takeover guard.

The first R6 attempt could not start. The box had run out of inotify instances (1,024), held by about 1,300 orphaned `dbus-daemon` processes that keyring-using `gh` calls had auto-launched outside a desktop. Hand cleared them. Fleet rule since then: run `gh`, test suites and Copilot sessions with `DBUS_SESSION_BUS_ADDRESS=disabled:` (or with `DISPLAY` unset).

The next automatic review posted 4 Blockers. **R7 `37ef957`** fixed them:
- the nanograph pointer, the FTS5 pointer and the mesh write now publish inside an owner-checked critical section that holds the takeover guard;
- the freshness digest includes the projection inputs (SCHEMA/CONTRACT, schema.d, projection version).

The next automatic review posted 1 Blocker and 3 Recommended threads.
- **R8 `de8263d`** fixed the Blocker: FTS5 query words are split as SQLite's `unicode61` does, where before an ASCII-only pattern mangled `café`, `résumé` and `東京`.
- By decision, the 3 Recommended threads were left open and unfixed:
  - nanograph legacy reuse when the new-location index is stale;
  - the same gap for tgrep;
  - the unreported mesh-lock ignore failure.

25 threads were fixed and resolved. `run_tests.py` passed all 35 entrypoints, and `release_readiness` passed.

The lesson: the first report called the PR green on CI alone. The review threads were not checked, so "done" must include zero unresolved threads.

## Changed files

- `scripts/atlas_cli/cli.py`, `schemas/atlas-mesh.schema.json`
- `scripts/atlas_cli/commands/index.py` (new); `core/index_location.py`, `core/engine_preference.py` (new); `core/meshfile.py`, `core/recall_index.py`, `core/paths.py`, `core/driver_overlay.py`, `core/drivers/tgrep.py`
- `scripts/test_index_location.py`, `test_engine_preference.py`, `test_index_cli.py` (new); `test_memory_layers.py`, `test_recall_config.py` updated
- `references/paths/configure.md`, `references/paths/help.md`
- `scripts/atlas_cli/commands/search.py`, `recall.py`, `validate.py`, `graph.py` (new)
- `scripts/atlas_cli/core/graph.py` (new), `driver_overlay.py` (new), `ignore_guard.py` (new), `projection.py`, `recall.py`, `retrieve.py`
- `scripts/atlas_cli/core/drivers/fts5.py`, `nanograph.py` (new)
- `scripts/test_recall_bm25.py`, `test_graph.py`, `test_drivers.py`, `test_nanograph_live.py` (all new)
- `fixtures/graph/schema.pg`, `fixtures/graph/seed.jsonl` (new)
- `SKILL.md`, `references/graph.md` (new), `references/drivers.md` (new), `references/paths/recall.md`, `CHANGELOG.md` (`## Unreleased (targets 0.14.0)`)

## Deviations from the plan

- The nanograph index is reused only when both the corpus digest and the nanograph version match. The plan asked only for the digest; this is stricter.
- nanograph `neighbours` makes one subprocess call per page, edge kind and direction at each hop. That is correct but could be slow on large neighbourhoods.
- `--engine bm25` output now also carries `driver_used`.
- The recall neighbourhood now resolves `relates_to` targets written with a leading `./`, because it uses the shared helper. This is a small behaviour change.
- `--engine nanograph`, like every `--engine` value, still conflicts with enabled recall. That keeps the existing rule. The driver can be reached through recall only on stores where recall is off.

- The briefed id rule (origin id for any standalone store) was narrowed: a store below its repo's top level gets a `local/...` id, so two stores in one repo never share an index directory.
- When bm25 is the default only because of a SCHEMA `query.search_engine` setting, it keeps the old temporary-index behaviour. When bm25 is chosen explicitly or by preference, the index is saved under `.atlas/indexes/fts5/`.
- `atlas recall index build`, now an alias, exits 1 when a build fails; before, it gave a warning with exit 0.
- FTS5 generations are now pruned, keeping the current one plus the newest other one. nanograph gains a `current.json` pointer.
- The mesh schema rejects unknown keys, so a mesh file containing one is refused rather than "preserved".

## Still not proven

- The `.gq` syntax, the seed format and the field names in `nanograph run --format json` output have not been run against a real nanograph binary. The PR body has the manual check commands for an Apple Silicon Mac. `scripts/test_nanograph_live.py` covers them there and skips everywhere else.

## Consequences flagged, not acted on

- Releasing 0.14.0 belongs to Master of Packages.
- nanograph is an optional binary that users install themselves on macOS. It adds no box-restore or Grand Maester dependency.
