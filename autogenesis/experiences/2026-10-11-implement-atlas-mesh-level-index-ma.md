---
type: experience
title: "Implement Run: mesh-level index packets MA (mesh core), MB (mesh graph), MC (federated recall) and MF (benchmark kit)"
created: 2026-10-11
work_id: 2026-10-10-atlas-mesh-level-index
implements: 2026-10-10-atlas-mesh-level-index
closes: []
status: done
kva: alive
description: "Packet MA of the approved mesh-level index plan was built by one fresh Copilot CLI session, with one more for a review Blocker, on atlas branch feat/mesh-core-ma (PR #63, head 5263b87), then packet MC by one more fresh session on feat/mesh-federated-recall-mc stacked on it (PR #64, head 28af545: recall run --scope mesh with tiered RRF and a restricted pre-filter), then MB (PR #65, head 0ace304: graph --scope mesh and the structure-only _mesh graph index) and MF (PR #66, head fe1b5ab: fixtures/mesh and the contributor-only mesh-bench kit), each by one fresh session. MA adds the library-only core/mesh_scope.py (members, atlas:// node ids, restricted pages withheld, a strict resolver with six unresolved reasons), the inert mesh config keys and index_location.mesh_index_dir. Output without the new keys is byte-identical to PR #61. Not merged."
origin: derived
sensitivity: internal
stage: implement
plan_path: autogenesis/plans/2026-10-10-atlas-mesh-level-index.md
external_ref: "github.com/sergio-sisternes-epam/atlas/pull/63, /pull/64, /pull/65, /pull/66"
relates_to:
  - path: work/2026-10-10-atlas-mesh-level-index.md
    kind: implements
  - path: autogenesis/plans/2026-10-10-atlas-mesh-level-index.md
    kind: derived_from
  - path: autogenesis/experiences/2026-10-10-design-atlas-mesh-level-index.md
    kind: follows
---

## What was asked

Start condition M23 was met when atlas PR #61 merged as squash `7af5805` on `main` at 23:50 BST on 2026-10-10. Sergio then asked for the IMPLEMENT operation on the approved plan, packet MA only:
- **Product code:** built in one fresh Copilot CLI session (claude-opus-5.5), never `--continue`, with no hand edits.
- **Landing:** one PR into atlas `main` from a fresh branch.
- **Gates:** `run_tests.py`, `release_readiness --commit <sha>`, `apm audit`, a diff scan and a CHANGELOG entry.
- **Review:** CI must pass and the review threads are checked about 10 and 20 minutes after the push.
- **Not allowed:** merging or requesting a Copilot review.

## Enter (G4) checks

- **Plan:** `2026-10-10-atlas-mesh-level-index`, `change_class: new-surface`. It contains the mini-genesis artifacts: mermaid, interface sketch, cost note and acceptance.
- **Approval:** `approval_ref` is Sergio's 23:08 BST approval. M22 authorises MA, and the scope matches.

## What was done

- **Branch:** `feat/mesh-core-ma` from `origin/main` `7af5805`. PR [#63](https://github.com/sergio-sisternes-epam/atlas/pull/63) is titled "feat(mesh): MA mesh core: members, atlas:// ids, strict cross-store resolver". It links the plan PR atlas-atlas #28 by name only.
- **`a059de6`, packet MA:** one fresh Copilot CLI session, 18 min 25 s, 358.72 AI credits, +1,682/−2 lines.
  - `core/mesh_scope.py` provides:
    - mesh discovery, with members listed in file order as `ok`, `unmounted` or `excluded`;
    - `atlas://<atlas-id>/<path>` node ids;
    - restricted pages withheld, with no override (M20);
    - structure-only node records (M6);
    - the strict M4 resolver with the unresolved reasons `unmounted`, `excluded_member`, `missing_page`, `withheld`, `outside_mesh` and `noncanonical_atlas_uri`. The short form is never resolved as an alias (M21);
    - an in-memory `build_view`.
  - `index_location.mesh_index_dir` and `MESH_SEGMENT = "_mesh"`.
  - Config keys `recall.scope`, `recall.rrf_k`, `graph.scope`, `graph.driver` and row `mesh_member`, added to the schema and meshfile. They are inert in MA.
  - The adversarial scenario file and a CHANGELOG bullet.
- **`5263b87`, review R1:** a second fresh session, 5 min 40 s, 82.48 AI credits. It fixed the one Blocker from the automatic review: an id such as `localhost/acme/repo` was accepted by validation but did not round-trip through `parse_node_id` and the resolver. One shared host rule now covers node ids and links, and the short form stays strict. The thread was replied to and resolved.
- **Byte-identical default (M15):** `scripts/test_mesh_scope_default.py` compares 45 commands with goldens.
  - The goldens were captured with `ATLAS_UPDATE_GOLDEN=1` on the unmodified tree before any product edit.
  - Separately, the test and its goldens were copied onto a clean `7af5805` checkout, and the test passed there. So the goldens really are PR #61's output.
- **Author:** Copilot committed `a059de6` as itself. Hand amended only the author metadata to the branch's usual author, with no content change.

## Evaluation evidence

All of the following ran on Linux x86_64 with no nanograph present.
- **MA head `a059de6`:**
  - `python3 scripts/run_tests.py`: "All 42 repository test entrypoints passed" (1,912 checks);
  - `release_readiness.py --commit a059de6e361e28d76fabf07bbd4cc67016ebb12b`: pass;
  - `apm audit --no-drift`: "18 file(s) scanned -- no issues found";
  - diff scan of `origin/main..HEAD`: no private host name and no token patterns.
- **New tests:** `test_mesh_resolver.py` (44 checks), `test_mesh_members.py` (21), `test_mesh_config.py` (65), `test_mesh_scope_default.py` (92). R1 added `test_mesh_review_r1.py`.
- **R1 head `5263b87`:** `run_tests.py` passed all 43 entrypoints. `release_readiness --commit 5263b87…` passed, `apm audit` was clean and the diff scan was clean.
- **CI on PR #63 at `a059de6`:** all six checks green:
  - Python tests
  - Release readiness decision
  - APM package integrity
  - Consumer install (agent-skills)
  - Consumer install (stable-runtimes)
  - No site/ on main
- **Automatic review:** the review at 00:25 BST left 1 thread, a Blocker, fixed in R1. At 00:33 BST, about 15 minutes after the push, there were no new threads. After the R1 push (00:37 BST), the automatic review of `5263b87` at 00:43 BST added no threads, and none were open at 00:47 BST. CI at `5263b87`: all six checks green. PR #63 has 1 thread, resolved.
- **Adversarial smokes:** `references/scenarios/mesh-index-adversarial-v1.yaml` holds all 11 approved smokes. The MA smokes have real checks: no-alias-resolution, no-auto-mount, unresolved-visible, excluded-member-unread, id-collision, single-store-hyrum and the MA part of no-shared-text-index. The rest are marked `pending packet MB/MC`.
- **agent-spec `specify`:** still deferred, because there is no agent-spec package in this harness's catalogue. The plan requires it, or a recorded deferral, before MC merges.

## Packet MC (federated recall)

- **Branch:** `feat/mesh-federated-recall-mc`, stacked on `feat/mesh-core-ma` at `5263b87`. PR [#64](https://github.com/sergio-sisternes-epam/atlas/pull/64) has base `feat/mesh-core-ma` and is titled "feat(mesh): MC federated recall: --scope mesh with tiered RRF". It was pushed at 00:55 BST.
- **`28af545`:** one fresh Copilot CLI session, 13 min 8 s, 269.6 AI credits, +1,130/−60 lines.
  - **`recall run --scope store|mesh [--rrf-k N]`:**
    - Precedence: the flag, then the top-level config, then the built-in default. The payload reports `scope_source` and `rrf_k_source`.
    - Exit 2 for: `--rrf-k` in store scope; `--profile` or `--allow-partial` with mesh scope; no mesh; k out of range.
  - **New `core/mesh_recall.py`:**
    - Each member runs its own engine in process and fetches `2 × limit`.
    - Restricted pages are removed from each member's eligible set before ranking.
    - Fusion is tiered RRF: tier, then score, then row order, then path.
    - A failing member gets `status: error`; the run returns `complete: false` with exit 1.
  - The M12 payload, a short `SKILL.md`/`recall.md` synopsis, real checks for the MC smokes, `benchmark-goodhart` retagged `MF`, and a CHANGELOG bullet.
- **Evidence at `28af545`:**
  - `test_mesh_rrf.py` 56 checks, `test_mesh_recall.py` 101 checks, `test_mesh_scope_default.py` 92 checks with goldens unchanged;
  - `run_tests.py`: "All 45 repository test entrypoints passed";
  - `release_readiness.py --commit 28af5456971e368f3f10defc4e179a00e4089878`: pass;
  - `apm audit --no-drift`: clean;
  - diff scan of `feat/mesh-core-ma..HEAD`: clean.
- **CI on PR #64 at `28af545`:** the first run failed `APM package integrity` with a GitHub API 403 (rate limit while registering the marketplace), and so `Release readiness decision` was blocked. Rerunning the failed jobs at 01:00 BST turned all six checks green. At 01:05 BST, 10 minutes after the push, there were no automatic review and no threads. The automatic reviewer may only run on PRs into `main`.
- **MC deviations:**
  - `--allow-partial` with mesh scope exits 2, because it is per store.
  - With an explicit `--engine`, a member whose recall profile is enabled is reported as `error`, because P23 already rejects `--engine` with an enabled profile.
  - Extra payload fields: `scope_source`, `rrf_k_source`, `project`, `query`, `limit`, `count`, `members[].error`.
  - Excluded and unmounted members show `hits: 0`.
  - Text output omits the RRF score.
- **MC changed files:**
  - `scripts/atlas_cli/core/mesh_recall.py` (new)
  - `scripts/atlas_cli/commands/search.py`, `scripts/atlas_cli/core/recall.py`, `scripts/atlas_cli/cli.py`
  - `scripts/test_mesh_rrf.py`, `scripts/test_mesh_recall.py` (new)
  - `references/scenarios/mesh-index-adversarial-v1.yaml`, `SKILL.md`, `references/paths/recall.md`, `CHANGELOG.md`
- **Still open:** agent-spec `specify` is deferred for MC as well, because the harness has no agent-spec package. This deferral is recorded before MC merges, as the plan requires.

## Packet MB (native mesh graph)

- **Branch:** `feat/mesh-graph-mb`, stacked on `feat/mesh-core-ma` at `5263b87`. PR [#65](https://github.com/sergio-sisternes-epam/atlas/pull/65) has base `feat/mesh-core-ma` and was pushed at 01:39 BST.
- **`0ace304`:** one fresh Copilot CLI session, 19 min 1 s, 458.39 AI credits, +1,649/−9 lines.
  - **New `core/mesh_graph.py`:**
    - a structure-only `graph/_mesh/` index with generations and a `current.json` pointer;
    - the M8 `mesh_digest` with fingerprint checks;
    - M9 locking with OwnedLock, BuildLock and locked_build. A busy reader waits 5 s, then answers in memory with `mesh_index_busy`. No member lock is ever taken;
    - the M10 compile hook, which runs only when the index exists and never changes the exit code.
  - **`--scope store|mesh` on `graph nodes|edges|neighbours|export`:**
    - `--store <atlas-id>`;
    - titles hydrated only for returned nodes;
    - a native fallback note for `--driver nanograph`;
    - `export --format json` refuses an `--out` inside a member or under `.atlas/indexes/`;
    - `--format nanograph` in mesh scope exits 2, because it is MD.
  - **`index`:** `index build --mesh`, the `index status` mesh block and `index show --mesh`.
  - SKILL.md and `references/graph.md` synopsis lines, real checks for the MB smokes, and a CHANGELOG bullet.
- **Evidence:**
  - `test_mesh_graph.py`: 71 checks;
  - `test_mesh_graph_index.py`: 55 checks;
  - `test_mesh_scope_default.py`: 92 checks, goldens unchanged;
  - `run_tests.py`: "All 45 repository test entrypoints passed";
  - `release_readiness --commit 0ace304…`: pass;
  - `apm audit`: clean;
  - diff scan: clean.
- **CI on PR #65 at `0ace304`:** all six checks green on the first run.
- **Automatic review:** at 01:50 BST, about 11 minutes after the push, there was no automatic review and there were 0 threads.
- **MB deviations:**
  - The `index status` mesh block appears only when a mesh scope is configured or a mesh index exists, to keep M15.
  - Compile refreshes an existing mesh graph even when the store has critical findings, and the exit code is unchanged.
  - The digest also covers unmounted row ids.
  - `graph.driver` from config applies only in mesh scope.
  - `edges --store` filters by the store the link is written in. An excluded id exits 2.
- **MB changed files:**
  - `scripts/atlas_cli/core/mesh_graph.py` (new)
  - `scripts/atlas_cli/cli.py`, `commands/graph.py`, `commands/index.py`, `commands/validate.py`
  - `scripts/test_mesh_graph.py`, `scripts/test_mesh_graph_index.py` (new)
  - `references/scenarios/mesh-index-adversarial-v1.yaml`, `SKILL.md`, `references/graph.md`, `CHANGELOG.md`

## Packet MF (benchmark kit)

- **Branch:** `feat/mesh-bench-mf`, stacked on `feat/mesh-federated-recall-mc` at `28af545`, as the plan's MF row requires (MA for the query set, MC for scoring). PR [#66](https://github.com/sergio-sisternes-epam/atlas/pull/66) has base `feat/mesh-federated-recall-mc` and was pushed at 01:54 BST.
- **`fe1b5ab`:** one fresh Copilot CLI session, 14 min 41 s, 301.26 AI credits. Nothing under `scripts/atlas_cli/` changed. It adds:
  - `fixtures/mesh/`: 52 invented pages in three stores, plus an excluded store, an unmounted row, a restricted page and one link per unresolved reason;
  - `contributor/mesh-bench/`:
    - `queries.json`, 41 queries: 31 multi-store (9 of them three-store) and 10 controls;
    - `bench.py`, comparing the oracle single store, plain RRF, tiered RRF with k = 10, 60 and 100, a BM25 score merge, and a scratch single index;
    - a latency mode and an unresolved-link report;
    - `MAC-HARNESS.md`, with the M17 criteria verbatim and a sha256 question lock;
    - `README.md` and `test_bench.py` (20 tests);
  - the `benchmark-goodhart` check and a CHANGELOG bullet.
- **One run on fixtures/mesh, Recall@10 and MRR:**

  | Arm | Recall@10 | MRR |
  |---|---|---|
  | oracle single store | 0.528 | 0.988 |
  | plain RRF | 0.900 | 0.854 |
  | tiered RRF, k = 10, 60 and 100 | 0.900 | 0.976 |
  | BM25 score merge | 0.900 | 1.000 |
  | scratch single index | 0.624 | 1.000 |

  - Tier inversions: plain RRF 38, tiered 0.
  - Federated latency, median total: 12, 38 and 70 ms at 2, 5 and 10 members.
  - The labels were written by the same session that built the kit, so this checks that the kit works, not retrieval quality. M17 on the Mac decides promotion.
- **Evidence:**
  - `run_tests.py`: "All 46 repository test entrypoints passed";
  - `release_readiness --commit fe1b5ab…`: pass;
  - `apm audit`: clean;
  - diff scan: clean.
- **CI on PR #66 at `fe1b5ab`:** all six checks green on the first run. At 02:04 BST, 10 minutes after the last push, there was no automatic review on #64, #65 or #66, and there were 0 threads. The reviewer appears to run only on PRs into `main`, so the stacked PRs should be re-checked after they are retargeted. #63 has 1 thread, resolved.
- **MF deviation:** `MAC-HARNESS.md` defines the question format and the pre-run rules, but not the 40 Mac questions. They must be written from the real Mac corpus, which is not reachable here and must not go into the public repo.
- **MF changed files:**
  - `fixtures/mesh/**` (new, 57 files)
  - `contributor/mesh-bench/queries.json`, `bench.py`, `MAC-HARNESS.md`, `README.md`, `test_bench.py` (new)
  - `references/scenarios/mesh-index-adversarial-v1.yaml`, `CHANGELOG.md`

## MA rebase, reviews R2 to R4, and merge (2026-10-11 night)

At 02:46 BST Sergio asked for #63 to be merged. By then #63 conflicted with `main`, because #62 (the `index show` fix, squash `7e84953`) had landed after #61.
- **Rebase:** a fresh Copilot session rebased MA onto `7e84953`, at 43.96 credits.
  - The only conflict was `CHANGELOG.md`, and both sets of entries were kept.
  - The goldens were regenerated on a clean `7e84953` checkout. Six index show/status cases changed, all because of #62's `store_required` and `current_store` changes.
  - The new heads were `5d3c7af` and `3f8b8b9`. They were force-pushed with a lease at 02:59 BST.
- **Review rounds:** each push drew new automatic-review threads, and each round was fixed in a fresh session:
  - **R2 `aaea773`** (148.19 credits):
    - Blocker: mesh rows whose `path`/`subpath` is absolute, contains `..` or escapes through a symlink are `invalid` with reason `outside_project`. This is checked before any file access, with a containment helper shared with `resolve.py`.
    - Recommended: fragments are dropped on every canonical target.
  - **R3 `fc3d708`** (66.76 credits): Blocker. Node ids percent-encode `%`, `#`, `?`, whitespace and non-printable characters through `encode_path`/`decode_path`, so `notes/a#b.md` round-trips.
  - **R4 `ac2331a`** (148.35 credits): two Blockers.
    - Ids with an empty host (such as `/acme/repo`) are `invalid` members with reason `invalid_atlas_id`. The invariant now holds: every `ok` member's id round-trips and resolves as `atlas_uri`.
    - Members load through their pinned mesh location (`index_location.pinned()`), so `subpath` and pathless rows use their row-id index and run no git subprocess.
- **Evidence:** `run_tests.py` reached 47 entrypoints, and every round passed `release_readiness --commit <full sha>`, `apm audit` and the diff scan. Every thread was replied to and resolved.
- **Final state:** the automatic review of `ac2331a` at 04:12 BST added no threads. CI was 6/6 and the PR was CLEAN, with 0 unresolved threads out of 6.
- **Merged:** squash-merged with `--match-head-commit` at 04:16 BST as **`1c40aa7`** on `main`.
- **Not acted on:** global `atlas-mesh.json` validation still accepts empty-host ids. Mesh scope treats them as invalid. Tightening global validation would change single-store behaviour, so it is left for Sergio to decide.

## Rebasing MB, MC and MF onto merged MA (2026-10-11, 04:15 to 04:48 BST)

- **MC (#64):** a fresh session (107.86 credits) ran `git rebase --onto origin/main 5263b87`, which gave `02b404c`. Only `CHANGELOG.md` conflicted. The session then added **`6b1bc15`**, "adapt MC to the merged MA contract":
  - members are searched through their pinned mesh location (a `subpath` member had been getting a `local/...` id);
  - `invalid` members are reported with their reason;
  - hit ids are the encoded `node_id`;
  - regression checks were added for invalid members, `#` in paths and the pinned location.

  `run_tests.py` passed all 49 entrypoints, and `release_readiness`, `apm audit` and the diff scan passed. Force-pushed with a lease at 04:32 BST, and the base changed to `main`.
- **MB (#65):** a fresh session (193.87 credits) produced `ecdc064`. The conflicts were `CHANGELOG.md`, `SKILL.md` (the `index show [--store <id> | --mesh]` line) and `commands/index.py` (#62's error count kept, then the mesh block). It then added **`430a311`**, "adapt MB to the merged MA contract":
  - `invalid` members are never read and are reported in the digest, the pointer, the export receipt and status/show;
  - hydration goes through `load_member`;
  - `root_not_found` is kept on the `--mesh` verbs.

  49 entrypoints passed and the gates passed. Force-pushed with a lease at 04:36 BST, and the base changed to `main`.
- **MF (#66):** `git rebase --onto origin/feat/mesh-federated-recall-mc 28af545` conflicted only on `CHANGELOG.md`, which a fresh session (19.23 credits) resolved, giving **`06060b0`**. No adaptation was needed, and the benchmark table is unchanged. 50 entrypoints passed. Force-pushed with a lease at 04:48 BST; the base stays the MC branch.
- **CI:** one #64 run failed `APM package integrity` with a GitHub 403 rate limit. Its failed jobs were re-run through the GitHub connector and turned green. #64 and #65 are each 6/6 green and CLEAN.
- **Test isolation flake:** one local MF run failed three `test_drivers.py` nanograph checks. Stray `/tmp/nanograph.toml` and `/tmp/.env.nano` files had been written at 04:33:38 BST, while two suites ran at the same time. The fake nanograph `init` treats `/tmp` as its project directory. After the stray files were removed, the full suite passed. A test still leaks scaffolding into `/tmp` when suites run in parallel; this is flagged for a follow-up.
- **Automatic review:** none had appeared on #64, #65 or #66 by 04:48 BST. Further checks are at about +30 and +60 minutes.

## Changed files

- `scripts/atlas_cli/core/mesh_scope.py` (new)
- `scripts/atlas_cli/core/index_location.py`
- `scripts/atlas_cli/core/meshfile.py`
- `scripts/atlas_cli/core/engine_preference.py`
- `scripts/atlas_cli/core/identity.py` (R1: `fold_host`)
- `scripts/atlas_cli/schemas/atlas-mesh.schema.json`
- `scripts/test_mesh_resolver.py`, `scripts/test_mesh_members.py`, `scripts/test_mesh_config.py`, `scripts/test_mesh_scope_default.py`, `scripts/test_mesh_review_r1.py`, `test_mesh_review_r2.py`, `test_mesh_review_r3.py`, `test_mesh_review_r4.py` (new)
- `scripts/atlas_cli/core/paths.py`, `scripts/atlas_cli/commands/resolve.py`, `scripts/atlas_cli/core/graph.py` (R2 to R4)
- `fixtures/mesh-default/goldens.json` (new)
- `references/scenarios/mesh-index-adversarial-v1.yaml` (new)
- `CHANGELOG.md` (`## Unreleased (targets 0.14.0)`)
- MC, MB and MF: see the changed files in their sections above

## Deviations from the plan

- **Store lookup:** stores under a `subpath` row, or a row with no `path`, are found by a member-root fallback, because `mesh_match` does not cover those rows.
- **Lenient loading:** the meshfile loader used for index location tolerates bad new keys, so single-store commands are unaffected. Mesh discovery validates strictly.
- **Mount upsert:** it now keeps `mesh_member`, as well as `recall`.
- **Unresolved edges:** they also keep `resolution`, recording how the target was written, next to `reason`.
- **Load failures:** a member that fails to load raises `MeshScopeError` instead of getting an `error` status. MC's payload is to handle member errors.
- **Scenario file:** it landed in MA, not ME, so that MA's smokes have real checks. `benchmark-goodhart` was tagged `MC`; its home is MF.
- **Host rule (R1):** a first segment counts as a host when it has a dot, a port or an IP literal, is `localhost`, or matches a mesh row's host. This makes M4's "no dot" test for the short form precise.

## Consequences flagged, not acted on

- MD and ME wait for the review of MB and MC.
- The 11 short-form links still need fixing in one small PR per store (M21). That is separate from the product packets.
