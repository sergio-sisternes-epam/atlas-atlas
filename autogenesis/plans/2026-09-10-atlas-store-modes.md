---
type: plan
title: "Design — Atlas storage strategy shared vs dedicated"
created: "2026-09-10"
work_id: "2026-09-10-atlas-store-modes"
status: implemented
change_class: new-surface
description: "Extend init with strategy shared|dedicated (default shared). Mesh strategy field. Rehost preserves git history both ways. GitHub driver is post-git."
origin: derived
sensitivity: internal
stage: implement
plan_path: autogenesis/plans/2026-09-10-atlas-store-modes.md
kva: alive
catalogue_review: in-scope
behavioural_contract: deferred:agent-spec not in this harness catalog
relates_to:
  - path: work/2026-09-10-atlas-store-modes.md
    kind: implements
  - path: autogenesis/discuss/store-modes/hub.md
    kind: derived_from
  - path: autogenesis/discuss/store-modes/pin-identity-consumer-repo.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-naming-two-axes.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-default-shared.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-setup-extend-init.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-mesh-strategy-field.md
    kind: related
  - path: autogenesis/discuss/store-modes/pin-migrate-one-path.md
    kind: related
  - path: decisions/mount-dot-atlas-submodule.md
    kind: related
---

# Design — Atlas storage strategy (shared vs dedicated)

## Intent + scope

Give Atlas a first-class **storage strategy** on the consumer git repository.

- **shared** (default for new consumers): knowledge lives on isolated branch `atlas` of the consumer repo. `atlas_id` is the consumer `host/org/repo`. Mount remains a same-repo git submodule at `.atlas/<encoded-id>/`.
- **dedicated**: today's separate store repository. Distinct `atlas_id`. Mount remains a submodule.

**Embedded** stays the `references/atlas` skill-mount sense. It is not a storage strategy name.

Setup extends path **init** (`strategy: shared|dedicated`). Migrate stays one path and gains a **mode** for strategy moves (plus the living `references/atlas` relocate mode). Git process is common. A GitHub driver runs **after** git when the host is GitHub.

This packet designs Atlas skill behaviour (CLI + path modules + mesh schema). It does not implement.

## Change-class

`new-surface`

## Pinned decisions

1. **Two axes.** Embedded = skill subpath `references/atlas`. Storage strategy = `shared` | `dedicated`.
2. **shared identity.** `atlas_id` = consumer repo. Mesh `ref` = `atlas`. Submodule URL is that same remote.
3. **Default shared** for new init. Existing mesh rows without `strategy` are dedicated. Do not rewrite live dedicated mounts as a side effect of the default.
4. **Explicit mesh `strategy`.** Do not infer from id+ref. Present-but-contradictory strategy fails closed.
5. **Extend init.** No new setup path. Init still never creates the host repository. Shared creates or reuses branch `atlas` on the existing consumer remote.
6. **Bootstrap.** Missing `atlas` → orphan empty tree + deterministic bootstrap commit, then SCHEMA templates. Not forked from the default branch. ([orphan branch](https://stackoverflow.com/questions/19980631/what-is-git-checkout-orphan-used-for))
7. **Existing `atlas`.** Reuse if `SCHEMA.json` is at the store root. Fail closed if the tree is not an Atlas. Do not delete or overlay product history.
8. **Git common, GitHub adds.** Driver is post-git. Mandatory: ruleset blocking direct push to `atlas`. Recommended: Copilot Reviews on PRs into `atlas`.
9. **Self-hosted.** Warn and continue. Do not fail closed for missing rulesets.
10. **One migrate path.** Card **mode** required. Modes: living relocate, and strategy move. Missing mode is incomplete Enter.
11. **Strategy migrate preserves history.** Push store commits to the destination. Fail closed on unrelated destination history that cannot fast-forward. No page-import rewrite. No dual-write.
12. **Both directions.** Card names **destination** strategy. Same source and destination fails closed. Dedicated destination still needs an existing remote.
13. **Migrate onto shared** runs the GitHub driver. Reverse does not strip rulesets unless the operator asks separately.
14. **Bootstrap then ruleset.** Apply GitHub ruleset **after** the empty `atlas` branch exists on the remote, so the creating push is not blocked. ([rulesets require PR](https://github.com/orgs/community/discussions/170970))
15. **Same-repo submodule cost.** Recursive clone of the consumer clones the git object store twice. Accept for v1; document it. Do not switch mount to worktree. Relative submodule URL is allowed. ([same-repo submodule](https://stackoverflow.com/questions/43356087/git-repo-where-each-submodule-is-a-branch-of-same-repo-how-to-avoid-double-trip))
16. **Submodule branch tracking.** `.gitmodules` records `branch = atlas` for shared. Writes check out that branch inside the mount; do not rely on detached HEAD.

## Non-goals

- Creating host repositories.
- Replacing submodule mount with worktree.
- Renaming Embedded away from `references/atlas`.
- Auto-migrating existing dedicated stores.
- Stripping GitHub rulesets on migrate to dedicated.
- Query/BM25 changes.
- Autogenesis product files.

## Challenge counters

| # | Counter | Source | Sev | Disposition |
|---|---------|--------|-----|-------------|
| 1 | Same-repo submodule double-clones on `--recursive` | [SO 43356087](https://stackoverflow.com/questions/43356087/git-repo-where-each-submodule-is-a-branch-of-same-repo-how-to-avoid-double-trip) | high | **Pin 15** — document; keep submodule |
| 2 | `checkout --orphan` keeps the working tree; easy to commit product files onto `atlas` | [SO 19980631](https://stackoverflow.com/questions/19980631/what-is-git-checkout-orphan-used-for) | high | **Pin 6** — empty tree before bootstrap commit |
| 3 | Ruleset “require PR” blocks the first push of `atlas` | [GitHub discussion 170970](https://github.com/orgs/community/discussions/170970) | high | **Pin 14** — push branch, then ruleset |
| 4 | Submodule update leaves detached HEAD | git-submodule docs | medium | **Pin 16** — record and checkout `branch = atlas` |

## Genesis Artifacts

### Intent + scope + non-goals

See sections above.

### Sequence (mini-genesis mermaid)

```mermaid
sequenceDiagram
  participant Op as Operator
  participant Init as atlas init
  participant Git as git remote
  participant GH as GitHub driver
  participant Mesh as atlas-mesh.json
  Op->>Init: strategy shared (default)
  Init->>Git: orphan empty atlas branch + SCHEMA
  Init->>Git: register same-repo submodule
  Init->>Mesh: id=consumer ref=atlas strategy=shared
  alt host is github.com
    Init->>GH: ruleset no direct push; recommend Copilot Reviews
  else self-hosted
    Init-->>Op: warn, continue
  end
```

### Interface sketch

**init card** adds `strategy: shared | dedicated` (default shared).

**atlas-mesh.json** store row adds `strategy`.

**migrate card** adds `mode: relocate | strategy` and, for strategy, `destination_strategy`.

CLI (illustrative):

```text
atlas init --remote <url> [--strategy shared|dedicated]
atlas migrate --mode strategy --destination-strategy shared|dedicated --root <consumer>
```

GitHub driver: after git succeeds, create ruleset on `atlas` (bypass not required if the branch already exists). Self-hosted: stderr warning, exit 0 for the driver step.

### Cost note

Balanced. Extra git objects for same-repo submodule (pin 15). No agent fan-out. Driver is a small GitHub API step. Token cost is path-module prose plus CLI, not a panel.

### Acceptance

- New init without strategy writes `strategy: shared` and an `atlas` branch that is an Atlas root.
- Existing mesh without strategy still mounts as dedicated.
- Init fails closed if `atlas` exists and has no `SCHEMA.json`.
- Strategy migrate pushes history, rewrites gitlink + mesh `id`/`strategy`, compile green, no second store left writable.
- GitHub shared: ruleset present after init; first bootstrap was not blocked.
- Self-hosted shared: warning in output, init still succeeds.

## Catalogue Review

- Genesis matches: **uses** A9 SUPERVISED EXECUTION (init/migrate plan-execute-verify), **uses** S7 DETERMINISTIC TOOL BRIDGE (git + GitHub API, not LLM-asserted branch state). No A1 PANEL.
- Autogenesis extension: **uses B17** on init and migrate cards (`strategy`, `mode`).
- Composition: **INLINE** in the Atlas skill (path modules + CLI). No new catalog skill.
- Inherited anti-patterns: tool-less assertion of git state; discussion→implement short-circuit (this packet stops for approval).
- Delta only: storage strategy + migrate mode. Mount stays submodule.
- Admission: B17 already active; no new Autogenesis pattern.

## Behavioural contract (agent-spec)

deferred: agent-spec is not in this harness catalog. Pins 1–16 are the behaviour source until specify can run in implement or a follow-up design.

Forbidden (must remain red if shipped): dual-write; overlay SCHEMA onto a non-Atlas `atlas` branch; infer strategy from id+ref when the field is present and contradicts; create host repositories.

## Evaluation plan

Deterministic primary:

- Mesh JSON has `strategy` after init; missing field on fixtures treated as dedicated.
- Shared mount path contains `SCHEMA.json`; branch name `atlas`.
- Init exit non-zero when `atlas` exists without SCHEMA.
- Migrate destination git log contains source tip; parent gitlink URL/id changed; old root not written.
- GitHub fixture or recorded API: ruleset created after branch exists.

Agent evals optional: card completeness for missing `mode`.

## Adversarial scenario draft

Filename (implement): `references/scenarios/atlas-store-modes-adversarial-v1.yaml`

```yaml
id: atlas-store-modes-adversarial-v1
adversarial: true
work_id: 2026-09-10-atlas-store-modes
packages: [atlas]
smokes:
  - id: no-dual-write
    source: pin-11
    expect: fail if two writable store roots after strategy migrate
  - id: no-overlay-product-branch
    source: pin-7
    expect: fail if init writes SCHEMA onto existing non-Atlas atlas branch
  - id: no-infer-when-field-contradicts
    source: pin-4
    expect: fail closed when strategy contradicts id/ref
  - id: no-create-host-repo
    source: pin-5
    expect: fail if dedicated init creates a repository
  - id: bootstrap-before-ruleset
    source: pin-14
    expect: fail if ruleset is applied before atlas branch exists
  - id: orphan-not-default-tree
    source: pin-6 / SO 19980631
    expect: fail if atlas branch contains consumer default-branch product files
```

## C1–C5

- C1: four grounded counters.
- C2: high-severity 1–3 pinned.
- C3: pins 1–16 visible.
- C4: scope is Atlas init/migrate/mesh/GitHub driver.
- C5: no implementation in this path.

## Stop for approval

This is a design packet only. Do not implement until this plan is explicitly approved.
