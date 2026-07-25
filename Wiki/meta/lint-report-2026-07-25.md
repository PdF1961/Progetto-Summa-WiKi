---
type: meta
title: "Lint Report 2026-07-25"
created: 2026-07-25
updated: 2026-07-25
tags:
  - meta
  - lint
status: developing
---

# Lint Report: 2026-07-25

## Summary
- Pages scanned: 70
- Issues found: 9
- Auto-fixed: 6
- Needs review: 3

## Orphan Pages
- [[Claude SEO]]: no real inbound links (only self-referenced from its own "Ecosystem" section). Content was about an unrelated SEO Claude Code plugin (`AgriciDaniel/claude-seo`) — didn't fit this vault's two actual domains. Confirmed cross-vault contamination. **Fixed** — `Wiki/entities/Claude SEO.md` deleted; no other page referenced it.

## Dead Links
- [[Principi non Negoziabili]]: referenced in `Wiki/entities/San Tommaso d'Aquino.md` (line 50) but the actual page is [[principi-non-negoziabili-de-regimine]]. Real broken link — filename mismatch, not a placeholder. **Fixed** — link updated to `[[principi-non-negoziabili-de-regimine]]`.
- [[cherry-picks]]: referenced 15 times across `Wiki/sources/claude-obsidian-ecosystem-research.md`, `Wiki/comparisons/claude-obsidian-ecosystem.md`, and 5 entity pages (Ar9av, ballred, Claudian-YishenTu, kepano, Nexus, rvk7895), described as "prioritized feature backlog" / "action items." Page was never created. Suggest: create `Wiki/cherry-picks.md` (or equivalent) with the numbered items these pages already link to by heading anchor (e.g. `#4. Delta Tracking Manifest`), or remove the links if the backlog was abandoned.
- [[Wiki Map]]: referenced from `index.md`, `getting-started.md`, `concepts/_index.md` as "visual Fibonacci graph of all wiki pages." Never created. Suggest: create `Wiki Map.md` (or a `.canvas` file) or remove the references — note `Wiki Map.md` is in the address/tiling exclusion list, so it's an expected meta page, just missing.
- [[dashboard.base]]: referenced and embedded from `Wiki/meta/dashboard.md` (Obsidian Base file). Never created. Suggest: create the `.base` file or drop the embed until it exists.
- Template placeholder links in empty stub indices (`books/_index.md`, `gaps/_index.md`, `goals/_index.md`, `journal/_index.md`, `lessons/_index.md`, `papers/_index.md`, `thesis/_index.md`): `[[Titolo Libro]]`, `[[Fonte A]]`, `[[Fonte B]]`, `[[Titolo]]`, `[[Titolo Paper]]`, `[[Lezione N - Titolo]]`, `[[YYYY-MM-DD-slug]]`, `[[Sintesi del Campo]]`. These are template examples, not real dead links — no action needed unless the sections get populated.
- `[[Foo]]` / `[[notes/Foo]]` in `Wiki/concepts/DragonScale Memory.md` and `[[Three laws of motion]]` in `Wiki/concepts/Persistent Wiki Artifact.md` are illustrative examples inside spec prose, not real links — no action needed.

## Stale Index Entries
- `Wiki/sources/_index.md` line 45: still described [[la-sintesi-tomistica]] as "Intro + Parte I + Parte VIII cap. I read; Parti II-VII flagged" — out of date as of this session's deep-dive, which read Parti II-VII in full. `wiki/index.md` and `wiki/concepts/_index.md` were updated during the deep-dive's final cross-reference pass, but `wiki/sources/_index.md` was missed. **Fixed** — entry now reads "now read in full across all 8 Parts, expanded same day; only Parte Ottava chs. II, III, V remain."

## Frontmatter Gaps
None. All 70 pages have `type`, `status`, `created`, `updated`, and `tags`.

## Empty Sections
- `Wiki/sources/_index.md` § "Transcripts": genuinely empty (no content, no `<!-- placeholder -->` comment like its sibling sections "Articles"/"Papers"). Cosmetic inconsistency.
- `Wiki/entities/_index.md` line 51 and `Wiki/sources/_index.md` line 60: instructional text ("Add new entities here as they are identified during ingests.", "Add new sources here after each ingest.") is formatted as a literal `##` heading instead of an HTML comment, unlike the sibling "Organizations"/"Products & Tools"/"Articles"/"Papers" sections in the same files. Cosmetic; harmless but inconsistent.
- All other flagged headings (e.g. "Key Innovations" → "### Delta Tracking Manifest", "Domain Concepts" → "### Tomismo") are false positives from a naive heading-adjacency check: they're immediately followed by a subheading, which is normal document structure, not an empty section.

## Address Validation (DragonScale Mechanism 2)

- Counter state: `52`
- Highest c- address observed: `c-000051`
- Post-rollout pages checked: all non-meta pages with `created >= 2026-04-23`
- Address-map (`.raw/.manifest.json`) consistency: **all entries valid**, no mismatches.
- `c-000046`: allocated but intentionally unused (noted in `wiki/log.md` and the manifest as a harmless planning miscount from this session's deep-dive). Not a lint error — it's a documented gap.

### Errors (fixed)
- [[Persistent Wiki Artifact]]: was missing `address:`. Created 2026-04-24 (post-rollout); address required. **Fixed** — allocated `c-000052`.
- [[Query-Time Retrieval]]: was missing `address:`. **Fixed** — allocated `c-000053`.
- [[Source-First Synthesis]]: was missing `address:`. **Fixed** — allocated `c-000054`.

These three are pre-existing template/demo pages from before this session's Thomism work, not something introduced by the recent ingest or deep-dive. Addresses allocated via `./scripts/allocate-address.sh`; counter now at `55`; `.raw/.manifest.json` address_map updated with all three entries.

### Pending backfill (informational)
- 15 legacy pages (created before the 2026-04-23 rollout) have no address, as expected: the "Wiki vs RAG" and "claude-obsidian-ecosystem" comparisons, most of the LLM-Wiki-Pattern concept pages, most non-Tomismo entity pages, and `claude-obsidian-ecosystem-research.md`. No action required.

## Semantic Tiling
Skipped — `python3` is not available in this Windows Git Bash environment (same limitation noted during the original batch ingest), so `scripts/tiling-check.py` could not run. No duplicate-page analysis was performed.

## Stale Claims
Not deeply checked this pass — would require re-reading every page against every other source for contradictions, which is beyond a routine lint. No specific contradictions are known from this session's work; the [[Il Cardine della Metafisica Tomista]] comparison page already tracks the one known multi-source tension (three different proposed "keystones" of Thomism) and was updated during the deep-dive.

## Naming/Style
No filename collisions, no non-Title-Case filenames, no writing-style violations spot-checked in the new Tomismo pages.
