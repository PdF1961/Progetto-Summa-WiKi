---
type: meta
title: "Hot Cache"
updated: 2026-07-25
tags:
  - meta
  - hot-cache
status: evergreen
related:
  - "[[index]]"
  - "[[log]]"
  - "[[overview]]"
---

# Recent Context

Navigation: [[index]] | [[log]] | [[overview]]

## Last Updated

2026-07-25 — deep-dive of [[la-sintesi-tomistica]] Parti II-VII (same-day follow-up to the 13-source batch ingest below); the book is now read in full except 3 chapters of Parte Ottava.

## Key Recent Facts

- Vault's actual domain is **Thomism / Aquinas studies** (the "Modello" template's placeholder demo content on the LLM Wiki pattern itself is still present alongside — ignore it for domain questions).
- [[Dottrina di Atto e Potenza]] (real distinction essence/esse) is the load-bearing concept — nearly every other page links to it.
- Three secondary sources propose three different "keystones" for Thomism's metaphysics — see [[Il Cardine della Metafisica Tomista]] before assuming any one framing is *the* standard account.
- [[XXIV Tesi Tomiste]] were approved 1914 (Pius X motu proprio), not 1925 — 1925 is when Garrigou-Lagrange presented their applications at the Rome Congress. This correction required reading a second source ([[la-sintesi-tomistica]]) against the first ([[essenza-e-attualita-del-tomismo]]).
- Four sources in this batch are primary Aquinas texts genuinely too large to read in full this session: [[somma-teologica-struttura]] (5,318pp, structure verified), [[somma-contro-i-gentili-struttura]] (1,374pp, intro read), [[sulla-verita-de-veritate]] and [[dizionario-interdisciplinare-scienza-fede]] (both **unreadable** — image scans, no OCR, one exceeds tool size limits).
- `scripts/allocate-address.sh` required a one-line patch to skip `flock` (unavailable in this Windows Git Bash environment) — now falls back to unlocked single-writer mode. Safe only because this vault has one writer at a time.
- [[la-sintesi-tomistica]] (Garrigou-Lagrange, ~245k words, 8 Parts) is now read **in full** except Parte Ottava chs. II, III, V — a same-day follow-up session read Parti II-VII directly from a pandoc-converted plaintext (no epub-tool limits hit). Reading the whole book strongly confirmed Garrigou-Lagrange's own claim that essence/esse is the one generative root of the whole system — see the new section in [[Il Cardine della Metafisica Tomista]].
- The "ontological personality" gap flagged in [[Persona (Tomismo)]] is now resolved: Cajetan's formula (*id quo natura singularis fit immediate capax existentiae*) is covered in [[Incarnazione, Unione Ipostatica e Mariologia]].
- Address `c-000046` was allocated but never used (a planning miscount, not corruption) — the next free address is c-000052. Harmless gap, noted here and in the manifest rather than silently skipped.

## Recent Changes

- Created 13 source pages, 6 entity pages (5 people + hub entity for Aquinas), 8 concept pages, 1 comparison page — see [[Wiki/sources/_index]], [[Wiki/entities/_index]], [[Wiki/concepts/_index]] for full lists.
- `.raw/.manifest.json` created for the first time this session (delta-tracking + address_map now active going forward).
- Same-day follow-up: read [[la-sintesi-tomistica]] Parti II-VII in full and created 7 new concept pages — [[Le Cinque Vie]], [[Grazia Efficace e Premozione Fisica]], [[La Santissima Trinità (Sintesi Tomistica)]], [[Angeli e Anima Umana (Sintesi Tomistica)]], [[Incarnazione, Unione Ipostatica e Mariologia]], [[I Sacramenti nella Sintesi Tomistica]], [[Teologia Morale nella Sintesi Tomistica]] — plus updates to [[Gerarchia degli Esseri e Analogia]], [[Persona (Tomismo)]], and [[Il Cardine della Metafisica Tomista]].

## Active Threads

- Only Parte Ottava chs. II, III, V of [[la-sintesi-tomistica]] remain unread (realism of first principles vs. pragmatism; grace, now largely redundant with Parte Settima) — low priority, book is effectively fully ingested.
- Other open follow-ups from the original batch: (1) [[sul-male-de-malo]] Qq. 7-16 (the capital vices, demons) plus the full disputed-question text for Qq. 1-6; (2) [[le-thomisme-gilson]] chs. II-XIV; (3) most of [[mondin-dizionario-tommaso]] (~36 of 39 entries); (4) source a readable (OCR'd or text-layer) edition of *De Veritate* to replace the unreadable scan.
- No page yet for Jacques Maritain — flagged in [[index]] Gaps.
