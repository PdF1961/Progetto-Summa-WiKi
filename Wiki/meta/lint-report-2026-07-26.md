---
type: meta
title: "Lint Report 2026-07-26"
created: 2026-07-26
updated: 2026-07-26
tags:
  - meta
  - lint
status: developing
---

# Lint Report: 2026-07-26

Triggered after the two same-day sessions that added 6 primary-text deep-ingest pages (4 Somma Teologica batches, 2 Contra Gentiles batches) — the first lint pass since [[lint-report-2026-07-25]].

## Summary
- Pages scanned: 78 (64 content pages + 14 meta/index)
- Issues found: 6
- Auto-fixed: 6
- Needs review: 0

---

## Second pass, same day (post-OCR-ingest of De Veritate + Dizionario Interdisciplinare)

Triggered by a third same-day session that OCR'd and deep-ingested [[de-veritate-qq-1-16-17-24]] and [[dizionario-anima-finalita-leggi-naturali]] (addresses c-000061, c-000062), closing the full four-text ingestion plan.

**Summary**: pages scanned 81 (66 content + 15 meta/index); issues found 2; auto-fixed 2.

**Dead link, same mistake as the first pass (real bug, fixed)**: despite this exact mistake being caught and fixed in `wiki/hot.md` earlier the same day (see above), the new session's own two source pages — `wiki/sources/sulla-verita-de-veritate.md` and `wiki/sources/dizionario-interdisciplinare-scienza-fede.md` — each introduced a fresh `[[ocr-pipeline-for-scanned-pdfs]]` link in their `key_claims` frontmatter, pointing at the same Claude Code memory file rather than a vault page. **Fixed** — reworded both as plain prose ("a verified OCR pipeline ... recorded in this session's Claude Code memory, not a vault page"), same treatment as the first fix. **Process note**: this is a recurring failure mode specific to sessions that discover something via cross-session memory and then summarize it into vault prose — worth a mental check ("is this bracket target actually a wiki page?") anytime a memory-derived fact gets written into frontmatter or body text.

**Address counter / manifest: verified correct, not re-broken this time**: `c-000061`/`c-000062` were again assigned by hand, but the lesson from the first pass was applied proactively — `./scripts/allocate-address.sh --rebuild` and the `.raw/.manifest.json` update were both run at the end of the ingest session itself, before this lint pass started. Re-verified here rather than re-fixed: counter already at `63` (correct), no duplicate addresses among 46 addressed pages, `address_map` at 0 missing/0 extra/0 mismatched (same one pre-existing `DragonScale Memory.md` legacy gap as before, still out of scope).

**Wiki Map canvas staleness, same pattern as the first pass (real gap, fixed)**: 2 new source pages were missing (61 pages should exist, canvas had 59). **Fixed** — regenerated with the same algorithm, now 61/61.

**Everything else re-checked and clean**: no orphans beyond the two archival lint-report pages themselves; no frontmatter gaps; no stale `updated:` fields this time (all touched pages were dated correctly during the ingest session); no filename collisions. Full link sweep: 18 non-resolving targets, all pre-existing known false positives (template placeholders, spec-prose examples, the `dashboard.base` gap, the `wiki-map`/`wiki-map.canvas` checker limitation, and retrospective mentions inside the lint reports themselves — including this file's own `` `[[...]]` `` in prose, which is not a link).

## Address Allocator Desync (real bug, fixed)

The 6 new source pages this session (`somma-teologica-de-deo-uno.md` through `contra-gentiles-libro-secondo.md`, addresses c-000055–c-000060) were assigned manually in frontmatter rather than via `./scripts/allocate-address.sh`, because the ingest work was done directly rather than through the allocator. This left `.vault-meta/address-counter.txt` at `55` — the next call to the allocator would have handed out `c-000055` again, colliding with an already-assigned page. **Fixed**: ran `./scripts/allocate-address.sh --rebuild`, which rescans all page frontmatter and resets the counter to the correct `61`. Verified no duplicate `address:` values exist across all 44 addressed pages.

**Process note**: any future session that assigns addresses by hand (rather than via the allocator) should run `--rebuild` before finishing, or better, just call the allocator each time even when working outside the ingest skill.

## Manifest Desync (real gap, fixed)

`.raw/.manifest.json`'s `address_map` still ended at `c-000054` and its `sources` entries for the two Summa PDFs still only listed the 2026-07-25 structural-entry pages — none of this session's 6 new pages or cross-linked updates were recorded, even though the manifest is the vault's authoritative provenance/delta-tracking record. **Fixed**: added all 6 new addresses to `address_map`; updated both PDF entries' `pages_created`, `pages_updated`, and `note` fields to describe the new batches (hashes reverified unchanged: `b397be48…` for Somma Teologica, `862bd80b…` for Contra Gentiles, confirming these are re-reads of the same files, not re-ingests of edited copies).

Cross-checked `address_map` against live frontmatter afterward: 43 entries (excl. `_unused`), 0 missing, 0 extra, 0 mismatched — except one pre-existing, out-of-scope gap: `wiki/concepts/DragonScale Memory.md` carries an `address: c-000001` in its frontmatter (likely predating the manifest system) that was never in `address_map`. Not introduced this session; left as-is per the same "informational, no action" judgment the 2026-07-25 report applied to similar legacy gaps.

## Dead Link (real bug, fixed)

`wiki/hot.md` linked to `[[ocr-pipeline-for-scanned-pdfs]]` — this resolves to a Claude Code cross-session *memory* file (outside this Obsidian vault entirely), not a wiki page, so the link was dead inside Obsidian. Introduced this session when summarizing a memory-system finding into the hot cache without noticing it wasn't a vault page. **Fixed** — reworded as plain prose describing the pipeline directly, with a note that it lives in session memory rather than the vault.

Full link sweep (84 unique `[[...]]` targets across the vault): the other 16 non-resolving targets are all known false positives already documented in the 2026-07-25 report (template placeholders in empty stub indices, illustrative examples in spec prose, `dashboard.base` — a pre-existing, still-uncreated Obsidian Base file, and the old lint report's own retrospective mentions of already-fixed links) plus one checker limitation: `[[canvases/wiki-map]]` / `![[canvases/wiki-map.canvas]]` in `Wiki Map.md` register as "broken" only because this pass's link checker matches against `.md` filenames — the `.canvas` file exists at `wiki/canvases/wiki-map.canvas` and both references resolve correctly in Obsidian.

## Wiki Map Canvas Staleness (real gap, fixed)

`wiki/canvases/wiki-map.canvas` (the Fibonacci-spiral visual map) had 52 file nodes; 59 content pages now exist. Diffed the "should be in canvas" set (every `type: concept/entity/source/comparison/question` page outside `wiki/meta/`) against actual canvas nodes: **7 missing, 0 stale/extra**. 6 of the 7 are this session's new source pages; the 7th, `wiki/concepts/cherry-picks.md`, is a pre-existing gap — it was created during the 2026-07-25 lint pass but the canvas (built in a later commit that same day) never picked it up. **Fixed**: regenerated the full canvas per the algorithm documented on `[[Wiki Map]]` itself (group by type in order comparison→source→entity→concept→question, alphabetical within each group, golden-angle spiral `r = 230·√(i+1)`, `θ = i·137.50776°`) — all 59 pages now present, JSON validated.

## Stale `updated:` Frontmatter (real gap, fixed)

8 pages were substantively edited across the last two sessions (2026-07-25 and 2026-07-26) without their `updated:` frontmatter field being bumped: `wiki/index.md`, `wiki/sources/_index.md`, `wiki/sources/somma-teologica-struttura.md`, `wiki/sources/somma-contro-i-gentili-struttura.md`, `wiki/sources/god-philosophy-universities.md`, `wiki/concepts/Le Cinque Vie.md`, `wiki/comparisons/Il Cardine della Metafisica Tomista.md`, `wiki/concepts/La Santissima Trinità (Sintesi Tomistica).md`, `wiki/concepts/I Sacramenti nella Sintesi Tomistica.md`, `wiki/concepts/Angeli e Anima Umana (Sintesi Tomistica).md`, and `wiki/Wiki Map.md`. **Fixed** — all bumped to `2026-07-26`.

## Stale Index Header (real gap, fixed)

`wiki/index.md`'s summary line still read "Last updated: 2026-07-25 | Total pages: ~51" despite today's 6 new pages. **Fixed** — updated to "2026-07-26 | ~64 content pages (78 incl. meta/index)" and noted the two new deep-ingest batches alongside the original 14-source count.

## Orphan Pages

None among content pages. Only one page has zero inbound `[[...]]` links: `wiki/meta/lint-report-2026-07-25.md` itself — expected, lint reports are archival and not meant to be cross-linked from content pages (this new report will be equally "orphaned" by the same convention).

## Frontmatter Gaps

None on content pages (all have `type`, `status`, `created`, `updated`, `tags`, and — where post-rollout — `address`). The 16 meta/index pages (`hot.md`, `log.md`, `index.md`, all `_index.md` files, etc.) lack `created:` by design — they're evergreen running documents, not point-in-time ingests, consistent with the convention already noted in the 2026-07-25 report.

## Naming/Style

No filename collisions (only the expected one-per-directory `_index.md` repeats). No non-Title-Case filenames introduced this session.

## Semantic Tiling

Skipped — `scripts/tiling-check.py` now fails at `import fcntl` (Unix-only module) rather than the previous "`python3` unavailable" reason, since a working Python 3.14 install was located this session (`/c/Python314/python`). Still not runnable on this Windows Git Bash environment regardless of the ollama dependency; would need a Windows-compatible file-locking rewrite to ever run here. No duplicate-page analysis performed.

## Stale Claims

Not deeply checked, consistent with the 2026-07-25 report's judgment that this is beyond routine lint scope. Both this session's new source pages and the concept pages they cross-link into were written specifically to verify (not contradict) existing secondary-source claims, and each verification was noted inline where checked — no new cross-source tensions surfaced.
