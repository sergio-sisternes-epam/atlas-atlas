---
type: experience
title: "Implement document type + origin/sensitivity vocabulary"
description: "Atlas side of approved plan knowledge-crawl-output-agnostic-v1: expanded recommended types with document; formalised origin and sensitivity as recommended frontmatter."
created: 2026-08-24
work_id: knowledge-crawl-output-agnostic-v1
status: done
tags: [atlas, implement, document, origin, sensitivity, type-vocabulary]
origin: internal
sensitivity: internal
implements: knowledge-crawl-output-agnostic-v1
closes: knowledge-crawl-output-agnostic-v1
plan_path: knowledge-crawl/references/atlas/autogenesis/plans/knowledge-crawl-output-agnostic-v1.md
construct_eval: deferred
relates_to:
  - path: work/knowledge-crawl-output-agnostic-v1.md
    kind: implements
  - path: decisions/type-vocabulary-document-and-sensitivity.md
    kind: implements
  - path: decisions/type-vocabulary.md
    kind: related
---

## Context

User approved design plan knowledge-crawl-output-agnostic-v1 (pins for document type, origin/sensitivity, location-agnostic crawl product) and requested implement of both Atlas and knowledge-crawl.

## What happened

- SCHEMA.json and SCHEMA.contract.json: added `document` to recommended types and roles; notes for origin and sensitivity vocabularies.
- New template `templates/document.md` (required: type, title, created; recommended: origin, sensitivity, description, tags, status).
- Decision `decisions/type-vocabulary-document-and-sensitivity.md` accepted; supersedes prior recommended-list wording in type-vocabulary.md.
- SKILL.md core-contract table and remember path updated to list document and origin/sensitivity.
- Work hub created for shared work_id.
- Atlas compile green.

## Outcome

Atlas base type vocabulary now includes durable content objects (`document`) distinct from episodic acquisition (`experience`). origin/sensitivity are formal recommended keys without tightening the compile bar.

## Changed files

- references/atlas/SCHEMA.json
- references/SCHEMA.contract.json
- references/atlas/templates/document.md
- references/templates/document.md
- references/atlas/decisions/type-vocabulary-document-and-sensitivity.md
- references/atlas/decisions/index.md
- references/atlas/work/knowledge-crawl-output-agnostic-v1.md
- references/atlas/experiences/2026-08-24-implement-document-type-and-sensitivity.md
- SKILL.md
- references/paths/remember.md
- references/atlas/log.md

## Related

- Work hub and decision for this work_id
- Cross-skill: knowledge-crawl implement experience under knowledge-crawl subject Atlas

## Follow-ups

- Optional construct scenarios when document writes become runtime-critical
- Callers (Train / knowledge-crawl) may start emitting type:document pages
