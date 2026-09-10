---
type: document
title: "What is Cartograph? Visual help for Atlas"
created: 2026-09-10
reviewed_at: 2026-09-10
subject: atlas
topic: cartograph-overview
status: published
origin: derived
sensitivity: internal
description: "Explore Atlas knowledge pages and relationships in the GitHub Copilot Cartograph canvas."
applies_to:
  product: atlas-cartograph
  version: "0.3.0"
  harness: github-copilot-app
  source_revision: 41ca3e2a0c2918acaa57ce5ec898033d7a17b786
relates_to:
  - path: autogenesis/work/2026-09-10-skill-help-pilot-cartograph.md
    kind: derived_from
  - path: atlas-project/vision.md
    kind: related
  - path: help/open-cartograph.md
    kind: related
  - path: help/install-and-open-cartograph.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/help/atlas-connection.md
    kind: related
  - path: atlas://atlas-cartograph-atlas/decisions/cartograph-v030-interaction-contract.md
    kind: derived_from
sources:
  - https://github.com/sergio-sisternes-epam/atlas-cartograph/blob/41ca3e2a0c2918acaa57ce5ec898033d7a17b786/README.md
  - https://github.com/sergio-sisternes-epam/atlas-cartograph-atlas/blob/fd17c25c7bf4151e4e86960a987a605324a64901/decisions/cartograph-v030-interaction-contract.md
---

# See how your Atlas connects

**Cartograph is a visual explorer for Atlas knowledge.** It reads your Atlas
pages, their types and their links, then shows them as a navigable graph in a
GitHub Copilot App canvas. Atlas remains the knowledge store; Cartograph is a
view of it, not a replacement storage system.

If you are new to Atlas, the map is useful for seeing how a decision connects
to an experience, how a lesson connects to its evidence, or how several
knowledge stores relate. You can keep the map open while exploring pages with
the agent. [Open it from Copilot's Canvas menu](open-cartograph.md), or use the
[installation guide](install-and-open-cartograph.md) if it is not available.
This native canvas guidance applies only to GitHub Copilot App with canvas
support, not arbitrary Copilot clients or other agent harnesses.

## What you can explore

Search by title, ID, Atlas, path, type or kind. Search can find pages on hidden
layers too. Select a node to focus on it and its visible immediate neighbors;
select it again to open the Markdown. Layer controls let you explore core
types and installed schema contributions. These behaviors come from the
[Cartograph interaction contract](atlas://atlas-cartograph-atlas/decisions/cartograph-v030-interaction-contract.md)
and the pinned package README.

Opening without an explicit root discovers recognized stores beneath the
current project's `.atlas/`. With no stores it shows a picker. Supplying a
root instead selects that store rather than the whole discovered collection.
The [two-store connection](atlas://atlas-cartograph-atlas/help/atlas-connection.md)
explains how Atlas onboarding links to Cartograph-specific knowledge.

There is a current identifier compatibility limit: graph links use schema IDs
such as `atlas-skill-memory`, whereas Atlas mount/resolve use full
`host/org/repo` identities. Atlas compile may therefore warn that a short
graph URI is unmounted even when both stores are open in Cartograph. Use the
full identities for CLI operations; do not invent mesh entries to silence
that warning. The [recorded experience](../autogenesis/work/2026-09-10-skill-help-pilot-cartograph-experience.md)
separates actual graph resolution from this warning.

## What the map does not prove

Nearby nodes are not automatically related evidence. The galaxy arrangement
is a visual layout, not a measure of truth, relevance or confidence. Read the
page and its typed relationships before drawing conclusions. A `related` link
is navigation; a `derived_from` link identifies claimed supporting knowledge.
Neither replaces checking what that source actually says.

Opening the map does not install Atlas, mount repositories or authorize
publication. It also does not start privileged read monitoring. Ordinary graph
updates follow accessible folder changes; file-access highlighting is a
separate opt-in collector with additional platform and permission requirements.

## For help authors

Suggest the visualiser when seeing relationships would help, not as a
prerequisite for understanding Atlas. Do not change a help request into an
installation. Use this article and its linked knowledge for explanation;
query the relevant Atlas when references are insufficient. If retrieval fails,
say that the help is limited and which Atlas is unavailable for this answer.
If retrieval succeeds without an answer, report a knowledge gap instead.
