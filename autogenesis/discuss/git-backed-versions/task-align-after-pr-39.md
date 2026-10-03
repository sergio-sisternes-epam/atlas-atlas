---
type: document
title: "Align memory-layer links after relates_to.ref merges"
created: "2026-10-03"
origin: derived
sensitivity: internal
description: "Task body for the pull request 39 follow-up. It depends on the three-layer task."
relates_to:
  - path: autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md
    kind: related
  - path: tasks/01M41NV1P6921FZ85WJXS194KV.md
    kind: related
---

## Content

This follow-up waits on the three-layer task. It also waits on atlas pull request 39, which implements optional relates_to.ref for issues 37 and 38. An absent ref still means the tip. A present ref is a git revision that tip compile does not resolve.

When both are done, align gist and frame links so they can point at a prior revision without rewriting the living page. Do not start this while the three-layer implement is still open.

## Provenance

Decision autogenesis/discuss/git-backed-versions/decision-relates-to-ref-time-travel.md. Pull request https://github.com/sergio-sisternes-epam/atlas/pull/39.
