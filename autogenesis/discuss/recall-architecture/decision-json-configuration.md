---
type: decision
title: "SMR configuration: JSON with closed, extensible validation contracts"
created: 2026-09-09
work_id: 2026-09-09-atlas-smr-configurable-recall
description: "Accepted: JSON-only configuration validated with versioned JSON Schema; explicit skill-owned extension points preserve SMO ownership and OKF openness."
status: settled
kva: alive
origin: user
sensitivity: internal
stage: discussion
artifact: autogenesis/discuss/recall-architecture/smr-smo-boundary.md
relates_to:
  - path: work/2026-09-09-atlas-smr-configurable-recall.md
    kind: implements
  - path: autogenesis/discuss/recall-architecture/smr-smo-boundary.md
    kind: derived_from
  - path: autogenesis/discuss/recall-architecture/hub.md
    kind: records
---

## Decision

Use JSON as the sole configuration format initially for the proposed
Semantic Memory Recall (SMR) configuration and skill contributions.
Validate configuration against a real, versioned JSON Schema using
Draft 2020-12. Do not introduce parallel YAML configuration authoring.

Close Atlas-owned configuration objects and stage/driver options against
their applicable schemas. Reject unknown configuration keys explicitly.
Third-party extensions enter through registered contribution namespaces,
with each payload validated against its skill-owned schema.

Use composition-aware closure, including `unevaluatedProperties: false`
where appropriate, so intended properties supplied through `$ref`/composition
are not accidentally rejected by a closed base object.

Strict JSON parsing must reject duplicate keys and non-standard numeric
constants. Structural validation covers types, required fields, recognised
keys and bounds. Semantic validation additionally checks profile and binding
references, driver compatibility and host override limits.

Closed configuration must not close authored OKF content: unknown valid page
types and metadata remain portable. YAML frontmatter is unchanged.
Semantic Memory Organisation (SMO) remains skill-owned.

## Rationale

JSON matches existing SCHEMA.json and installed JSON overlays and keeps the
parsing contract small. YAML could also be validated using JSON Schema after
parsing, so closed validation alone does not force JSON. Supporting YAML
would introduce additional policy for tags, aliases, merge keys, non-string
keys and implicit scalar typing without a demonstrated need here.

Explicit extension schemas preserve third-party ownership without making
the entire configuration permissive or allowing one contribution to
overwrite another's contract.

## Consequences

The current `references/SCHEMA.contract.json` is a normative field list, not
a full JSON Schema validator. Formal design must introduce the real schemas
and validation integration rather than assuming they already exist.

The decision pins format, validation approach and extension boundaries.
Exact property names, contribution binding vocabulary, profile schema
versions, validator dependency and compatibility migration remain design work.
This is not approval to implement the wider SMR architecture or mutate
existing store schemas.

## Approval and provenance

In the 2026-09-09 discussion, the user asked whether configuration should use
YAML or JSON given the need for closed validation. After the JSON-only,
versioned JSON Schema recommendation, the user explicitly replied:
"Agreed, capture that design decision".

The originating proposal is
[SMR/SMO boundary](smr-smo-boundary.md). The wider
[Recall discussion](hub.md) remains open.
