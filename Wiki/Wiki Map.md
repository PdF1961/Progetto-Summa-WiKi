---
type: meta
title: "Wiki Map"
updated: 2026-07-26
tags:
  - meta
  - navigation
status: evergreen
related:
  - "[[index]]"
  - "[[overview]]"
  - "[[hot]]"
  - "[[dashboard]]"
  - "[[getting-started]]"
---

# Wiki Map

Navigation: [[index]] | [[overview]] | [[hot]] | [[dashboard]] | [[getting-started]]

A visual, whole-vault view of every content page (concepts, entities, sources, comparisons, questions — meta/index/log/hot/dashboard pages are excluded, same exclusion set DragonScale addressing uses). Pages are laid out on a Fibonacci (golden-angle) spiral, oldest/first-processed near the center, so the map grows outward as the vault grows instead of needing a full re-layout.

> [!tip] Embedded Canvas
> The map lives in [[canvases/wiki-map]]. Open that file directly for the interactive Obsidian canvas, or use the embed below.

![[canvases/wiki-map.canvas]]

## Reading the map

Node color marks page type:

| Color | Type |
|---|---|
| Blue | concept |
| Purple | entity |
| Green | source |
| Orange | comparison |
| Red | question |

## Regenerating

This canvas is generated, not hand-maintained. When the page count grows enough that the spiral feels stale (rule of thumb: after every batch ingest), regenerate it:

1. List every file under `wiki/` whose `type` frontmatter is `concept`, `entity`, `source`, `comparison`, or `question` (skip anything in `wiki/meta/` or `wiki/canvases/`, and skip `_index.md`/`index.md`/`log.md`/`hot.md`/`overview.md`/`dashboard.md`/`getting-started.md`/`Wiki Map.md` themselves).
2. Group by type (comparison, source, entity, concept, question, in that order) so same-type pages cluster as the radius grows.
3. Place page *i* at golden-angle spiral position `r = scale * sqrt(i+1)`, `theta = i * 137.50776°`, with `scale` around 230 so 260×90 file nodes don't overlap.
4. Write one Obsidian Canvas `file` node per page (color per the table above) plus one `text` node with a short caption, to `wiki/canvases/wiki-map.canvas`.

## See also

- [[dashboard]] — live Dataview/Bases queries, complementary to this static visual map
- [[index]] — the same page set, as a linked list rather than a graph
