---
type: decision
title: "Expand Atlas recommended types with document; formalise origin and sensitivity"
created: 2026-08-24
status: accepted
work_id: knowledge-crawl-output-agnostic-v1
description: "Add document as recommended type for durable content objects. Formalise origin (internal|third-party|user|derived) and sensitivity (public|internal|restricted) as recommended frontmatter. Differentiates document (raw content) from experience (episodic acquisition)."
relates_to:
  - path: decisions/type-vocabulary.md
    kind: supersedes
  - path: work/knowledge-crawl-output-agnostic-v1.md
    kind: implements
  - path: experiences/2026-08-24-implement-document-type-and-sensitivity.md
    kind: related
---

## Decision

1. Recommended SCHEMA types now include **`document`** alongside experience, decision, lesson, recipe, work.
2. **`document`** role: durable content object — source material, page, file, note (not an episodic event).
3. **origin** (recommended frontmatter): `internal | third-party | user | derived`.
4. **sensitivity** (recommended frontmatter): `public | internal | restricted`.
5. These keys remain optional (never hard-required by compile) so existing pages stay valid.
6. experience continues to mean episodic acquisition / process events; document is the artefact itself.

## Rationale

knowledge-crawl and third-party consumers need a clear type for raw durable content distinct from the act of acquiring it. origin/sensitivity already appeared in practice; formalising them removes ambiguity without tightening the compile bar.

## Alternatives considered

- Keep product pages as experience (rejected — conflates artefact with acquisition event).
- Closed enum for types (rejected — OKF freedom).
- Hard-require origin/sensitivity (rejected — would break existing pages).

## Consequences

- SCHEMA.json, SCHEMA.contract.json, and templates updated.
- New document.md template (required: type, title, created; recommended: origin, sensitivity, …).
- knowledge-crawl product output uses type: document.
- Prior type-vocabulary decision remains historical; this decision supersedes the recommended list.

## Related

- supersedes: [type-vocabulary](type-vocabulary.md)
- Cross-skill work_id: knowledge-crawl-output-agnostic-v1 (knowledge-crawl subject)
