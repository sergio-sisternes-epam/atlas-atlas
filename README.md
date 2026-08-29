# atlas-atlas

Dedicated Atlas store for the atlas skill (extracted from `references/atlas`).

This is a **knowledge store**, not a skill package. Git root holds packaging files only (`README.md`, `apm.yml`, `.gitignore`). Do not flatten store pages to the git root.

OKF root is `atlas/` (`atlas/SCHEMA.json`), not the git root.

```text
atlas auth login --host github.com
atlas mount github.com/sergio-sisternes-epam/atlas-atlas --ref main
```

Default clone path: `.atlas/github.com/sergio-sisternes-epam/atlas-atlas`  
Compile/query root: `.atlas/github.com/sergio-sisternes-epam/atlas-atlas/atlas`

In this repository, compile against `./atlas` (CLI lives in the atlas skill package; it is not vendored here):

```text
atlas compile --root atlas
```

## APM

```text
apm install sergio-sisternes-epam/atlas-atlas
```

Store package depends on `sergio-sisternes-epam/okf` and `sergio-sisternes-epam/atlas`.
