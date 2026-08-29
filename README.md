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

This is a **knowledge store**, not a skill package. Git root **is** the OKF root (`SCHEMA.json`, `index.md`).

```text
atlas auth login --host github.com
atlas mount github.com/sergio-sisternes-epam/atlas-atlas --ref main --target references/atlas
```

Mount path = compile/query root: `references/atlas`

In this repository:

```text
atlas compile --root .
```

## APM

```text
apm install sergio-sisternes-epam/atlas-atlas
```

Store package depends on `sergio-sisternes-epam/okf` and `sergio-sisternes-epam/atlas`.
