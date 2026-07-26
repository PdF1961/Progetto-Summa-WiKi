---
type: meta
title: "Hot Cache"
updated: 2026-07-26
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

2026-07-26 — completed batches 5-6: deep-ingest of *Summa contro i Gentili* Libro I (ch.13, God's existence) and Libro II (ch.56-59, 79, the soul), same-day follow-up to the 4-batch Somma Teologica plan completed earlier today.

## Key Recent Facts

- **Two primary Aquinas texts now have real deep-ingests beyond structural placeholders**: Somma Teologica (4 batches: [[somma-teologica-de-deo-uno]], [[somma-teologica-trinita]], [[somma-teologica-trattato-legge]], [[somma-teologica-sacramenti]]) and Summa contro i Gentili (2 batches: [[contra-gentiles-libro-primo]], [[contra-gentiles-libro-secondo]]). Every doctrine previously known only via Garrigou-Lagrange's secondary synthesis now has a direct primary-text citation, with no divergence found anywhere checked.
- **Two different page-mapping methods needed, by source**: the Summa Teologica PDF is clean digital text — full extract + Python regex on each question's `ARGOMENTO N` header gives an exact page-index cheaply. The Contra Gentiles PDF is genuine scan-OCR with real error rates ("CAPITOLO" garbles to "CaritoLo," accents render as replacement chars) — clean regex header search is unreliable there; use targeted content-keyword search instead (works well, e.g. "motore immobile", "Averroè").
- **Trap** (Summa Teologica only): question numbers reset at each Part (I, I-II, II-II, III) — same numbers can point to completely different treatises. Anchor to the correct Part's page range first.
- Both Summa PDFs are **parallel Latin-Italian editions** (Latin prooemium before the Italian translation on the Summa Teologica; Latin scripture/Aristotle citations throughout the Contra Gentiles) — useful for future close Latin readings.
- Vault's actual domain is **Thomism / Aquinas studies** (the "Modello" template's placeholder demo content is still present alongside — ignore it for domain questions).
- [[Dottrina di Atto e Potenza]] (real distinction essence/esse) is the load-bearing concept — nearly every other page links to it.
- [[sulla-verita-de-veritate]] and [[dizionario-interdisciplinare-scienza-fede]] remain **unreadable** with current extraction tools (image scans, no text layer) — but see [[ocr-pipeline-for-scanned-pdfs]] memory: `pdftoppm` + `tesseract -l ita+lat` is a verified working pipeline, not yet applied. This is the natural next front if continuing the paced ingestion plan.

## Recent Changes

- 2026-07-26 (2nd session): created [[contra-gentiles-libro-primo]] and [[contra-gentiles-libro-secondo]] (addresses c-000059, c-000060); updated [[somma-contro-i-gentili-struttura]], [[Le Cinque Vie]], [[god-philosophy-universities]], [[Angeli e Anima Umana (Sintesi Tomistica)]] with primary-text cross-links.
- 2026-07-26 (1st session): created 4 Somma Teologica deep-ingest pages (c-000055 to c-000058); updated [[somma-teologica-struttura]], [[Le Cinque Vie]], [[Il Cardine della Metafisica Tomista]], [[La Santissima Trinità (Sintesi Tomistica)]], [[god-philosophy-universities]], [[I Sacramenti nella Sintesi Tomistica]].
- 2026-07-25: created 13 source pages, 6 entity pages, 8 concept pages, 1 comparison page from a batch ingest; same-day follow-up read [[la-sintesi-tomistica]] Parti II-VII in full, adding 7 concept pages.

## Active Threads

- Next address is **c-000061**.
- Within all 6 Somma batches (Teologica + Contra Gentiles): many chapters/questions are structurally-confirmed-but-not-read-article-by-article — see each page's "What remains unread" section. Highest priority if continuing Contra Gentiles: Libro II chs.60-78 (the fuller anti-Averroist polemic, ch.59 is only its opening).
- Other open fronts: (1) apply the verified OCR pipeline to *De Veritate* and the *Dizionario Interdisciplinare* (both currently unreadable placeholders); (2) [[sul-male-de-malo]] Qq. 7-16 plus full text for Qq. 1-6; (3) [[le-thomisme-gilson]] chs. II-XIV; (4) most of [[mondin-dizionario-tommaso]] (~36 of 39 entries); (5) Tertia Pars qq.1-59 (the Incarnation itself) not yet deep-ingested from the Summa Teologica primary text.
- No page yet for Jacques Maritain — flagged in [[index]] Gaps.
