---
type: document
title: "atlas-atlas"
created: 2026-08-29
description: "Dedicated Atlas store for the atlas skill. Git root is the OKF root."
origin: internal
sensitivity: public
---

# atlas-atlas

Dedicated Atlas store for the atlas skill (extracted from `references/atlas`).

This is a **knowledge store**, not an APM or skill package. Git root **is** the
OKF root (`SCHEMA.json`, `index.md`). The store has no package dependencies,
vendored CLI, or submodules.

## Mount

Authenticate GitHub access, then mount the store. The GitHub repository is
currently private; page-level `sensitivity` metadata remains independent of
repository visibility.

```text
python3 <atlas-v0.8.13>/scripts/atlas.py auth login --host github.com
python3 <atlas-v0.8.13>/scripts/atlas.py mount \
  github.com/sergio-sisternes-epam/atlas-atlas --ref main
```

The default mount and compile/query root is
`.atlas/github.com/sergio-sisternes-epam/atlas-atlas`. Use `--target` only when
the consuming repository needs a different submodule path.

## Compile

Atlas is released separately. Validate this store with Atlas v0.8.13, whose tag
resolves to commit `9c09edcfd88afbad674d877e4f3b038c8c55c33c`:

```text
python3 <atlas-v0.8.13>/scripts/atlas.py compile --root . --json
```

CI runs the same unfocused compile for every pull request and push to `main`.
Exit `0` passes, exit `1` passes with warnings retained, and exit `2` fails.
The JSON result is printed and uploaded as the `atlas-compile-json` artifact.

### Warning baseline

Atlas v0.8.13 currently reports six non-critical `atlas_uri_unmounted`
warnings for illustrative identifiers in the git-mesh design record:

- `autogenesis/discuss/git-mesh/monorepo-subpath.md`
- `autogenesis/discuss/git-mesh/decision-resolve-root-or-file.md`
- `autogenesis/discuss/git-mesh/atlas-uri-vs-hash.md`
- `autogenesis/discuss/git-mesh/id-normaliser.md`
- `autogenesis/discuss/git-mesh/uri-id-extract.md`
- `autogenesis/discuss/git-mesh/tension-url-as-id.md`

These examples intentionally use placeholder Atlas URIs that are not mounted in
this store. The Atlas compile contract accepts them as warnings; critical
findings and non-empty staging remain blocking. Any new warning, changed
warning identifier, or warning on another page must be reviewed and explicitly
dispositioned rather than silently added to this baseline.

## CI credential

The workflow downloads the CLI at the exact v0.8.13 commit from the private
`sergio-sisternes-epam/atlas` repository. Configure the repository Actions
secret `ATLAS_CLI_TOKEN` with read-only contents access to that repository.
The token is used only for CLI acquisition.
