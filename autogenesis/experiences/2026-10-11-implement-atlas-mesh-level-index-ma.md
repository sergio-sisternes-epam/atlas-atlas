---
type: experience
title: "Implement Run: mesh-level index packets MA (mesh core) and MC (federated recall)"
created: 2026-10-11
work_id: 2026-10-10-atlas-mesh-level-index
implements: 2026-10-10-atlas-mesh-level-index
closes: []
status: implementing
kva: alive
description: "Packet MA of the approved mesh-level index plan was built by one fresh Copilot CLI session, with one more for a review Blocker, on atlas branch feat/mesh-core-ma (PR #63, head 5263b87), then packet MC by one more fresh session on feat/mesh-federated-recall-mc stacked on it (PR #64, head 28af545: recall run --scope mesh with tiered RRF and a restricted pre-filter). MA adds the library-only core/mesh_scope.py (members, atlas:// node ids, restricted pages withheld, a strict resolver with six unresolved reasons), the inert mesh config keys and index_location.mesh_index_dir. Output without the new keys is byte-identical to PR #61. Not merged."
origin: derived
sensitivity: internal
stage: implement
plan_path: autogenesis/plans/2026-10-10-atlas-mesh-level-index.md
external_ref: "github.com/sergio-sisternes-epam/atlas/pull/63, github.com/sergio-sisternes-epam/atlas/pull/64"
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

## Changed files

- `scripts/atlas_cli/core/mesh_scope.py` (new)
- `scripts/atlas_cli/core/index_location.py`
- `scripts/atlas_cli/core/meshfile.py`
- `scripts/atlas_cli/core/engine_preference.py`
- `scripts/atlas_cli/core/identity.py` (R1: `fold_host`)
- `scripts/atlas_cli/schemas/atlas-mesh.schema.json`
- `scripts/test_mesh_resolver.py`, `scripts/test_mesh_members.py`, `scripts/test_mesh_config.py`, `scripts/test_mesh_scope_default.py`, `scripts/test_mesh_review_r1.py` (new)
- `fixtures/mesh-default/goldens.json` (new)
- `references/scenarios/mesh-index-adversarial-v1.yaml` (new)
- `CHANGELOG.md` (`## Unreleased (targets 0.14.0)`)
- MC: see the MC changed files above

## Deviations from the plan

- **Store lookup:** stores under a `subpath` row, or a row with no `path`, are found by a member-root fallback, because `mesh_match` does not cover those rows.
- **Lenient loading:** the meshfile loader used for index location tolerates bad new keys, so single-store commands are unaffected. Mesh discovery validates strictly.
- **Mount upsert:** it now keeps `mesh_member`, as well as `recall`.
- **Unresolved edges:** they also keep `resolution`, recording how the target was written, next to `reason`.
- **Load failures:** a member that fails to load raises `MeshScopeError` instead of getting an `error` status. MC's payload is to handle member errors.
- **Scenario file:** it landed in MA, not ME, so that MA's smokes have real checks. `benchmark-goodhart` was tagged `MC`; its home is MF.
- **Host rule (R1):** a first segment counts as a host when it has a dot, a port or an IP literal, is `localhost`, or matches a mesh row's host. This makes M4's "no dot" test for the short form precise.

## Consequences flagged, not acted on

- MB and MF wait for Sergio's dispatch. MD and ME wait for the review of MB and MC.
- The 11 short-form links still need fixing in one small PR per store (M21). That is separate from the product packets.
