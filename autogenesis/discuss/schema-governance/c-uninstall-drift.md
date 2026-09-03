---
type: document
title: "Counter — uninstall leaves drift"
created: 2026-09-03
status: settled
kva: alive
reality: current
description: "IaC overlay uninstall leaves leftover files. Deleting schema.d is not enough if claimed pages stay."
origin: derived
sensitivity: internal
relates_to:
  - path: autogenesis/plans/2026-09-03-atlas-schema-governance.md
    kind: counters
  - path: autogenesis/discuss/schema-governance/hub.md
    kind: derived_from
  - path: work/2026-09-03-atlas-schema-governance.md
    kind: implements
---

## Content

Uninstalling overlay/compose extensions in IaC often leaves fragments. Drift is the live tree no longer matching the declared desired state. Mitigation is a recorded write-set and destroy hooks, not “delete the overlay file”.

Pin 11 says uninstall deletes `schema.d/<id>.json` and files the overlay claimed it wrote. If pages were authored *into* a claimed folder after install, deleting them is data loss; if they are left, compile still sees types the overlay defined. That is drift.

Sources: [Spacelift drift management](https://spacelift.io/blog/drift-management); [Snyk detect and prevent configuration drift](https://snyk.io/articles/infrastructure-as-code-iac/detect-prevent-configuration-drift/).

Severity: high for pin 11.

**Pin (autonomous, operator away 2026-09-03):** uninstall deletes `schema.d/<id>.json` and receipt-listed CLI writes only. It never deletes pages authored after install. Compile warns if pages still use types that existed only on the removed overlay.

## Provenance

think-challenge 2026-09-03 before sign-off.
