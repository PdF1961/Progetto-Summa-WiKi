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

2026-07-26 — completed the **entire four-text paced ingestion plan** agreed 2026-07-25: Somma Teologica (4 batches), Summa contro i Gentili (2 batches), and now De Veritate + Dizionario Interdisciplinare via OCR (the two sources previously logged as fully unreadable).

## Key Recent Facts

- **All four originally-flagged large sources now have real deep-ingests**, not just structural placeholders: [[somma-teologica-struttura]] (4 batches), [[somma-contro-i-gentili-struttura]] (2 batches), [[sulla-verita-de-veritate]] (1 batch, via OCR), [[dizionario-interdisciplinare-scienza-fede]] (1 batch, via OCR). Every doctrine previously known only via secondary synthesis now has a direct primary-text citation somewhere in the vault.
- **OCR is fast enough for real work here**: PyMuPDF (`fitz`) in-process rasterization beats `pdftoppm` subprocess calls by ~10-50x (~0.1-0.35s/page vs ~5s/page), making even 1,000+ page scanned/print-to-PDF files practical to search and read via `tesseract -l ita+lat`. Neither De Veritate nor the Dizionario has embedded PDF bookmarks (`doc.get_toc()` returns empty in both) — navigate via sparse-sample content search anchored on proportional estimates, or (Dizionario only) the book's own front-matter index plus running headers that name the current entry.
- **De Veritate is a parallel Latin-Italian edition** (Fernando Fiorentino, 2011) — a low-res OCR pass first misread it as Latin-only because two-column layouts interleave into garbled lines at low resolution; 3x zoom + `tesseract --psm 6` fixed this.
- **Independent convergence discovered**: the Dizionario's ANIMA and LEGGI NATURALI entries (written in 2002, no connection to this vault) cite the exact same primary-text passages (*Contra Gentiles* II c.56, *S.Th.* I q.51 a.1, *S.Th.* I-II qq.93-94) this vault ingested directly from primary sources the same day — strong independent confirmation the right passages were located.
- **Question numbers reset per Summa Teologica Part** (I, I-II, II-II, III) — a real trap hit and documented in [[somma-teologica-trattato-legge]].
- Vault's actual domain is **Thomism / Aquinas studies** (the "Modello" template's placeholder demo content is still present alongside — ignore it for domain questions).
- [[Dottrina di Atto e Potenza]] (real distinction essence/esse) remains the load-bearing concept — nearly every other page links to it.

## Recent Changes

- 2026-07-26 (3rd session): OCR-ingested [[de-veritate-qq-1-16-17-24]] (c-000061) and [[dizionario-anima-finalita-leggi-naturali]] (c-000062); flipped both source placeholders from "unreadable" to structural-entry-plus-deep-ingest; cross-linked into [[essenza-e-attualita-del-tomismo]], [[god-philosophy-universities]], [[somma-teologica-trattato-legge]], [[Angeli e Anima Umana (Sintesi Tomistica)]], [[Gerarchia degli Esseri e Analogia]].
- 2026-07-26 (2nd session): lint pass — fixed address-counter/manifest desync, one dead link, a stale Wiki Map canvas (7 missing pages), 8 stale `updated:` fields. Full report: [[lint-report-2026-07-26]].
- 2026-07-26 (1st session): created 6 Somma Teologica/Contra Gentiles deep-ingest pages (c-000055 to c-000060).
- 2026-07-25: created 13 source pages, 6 entity pages, 8 concept pages, 1 comparison page from a batch ingest; same-day follow-up read [[la-sintesi-tomistica]] Parti II-VII in full, adding 7 concept pages.

## Active Threads

- Next address is **c-000063**.
- Highest-priority remaining targets, in order: (1) De Veritate q.11 (*De Magistro*, pairs with [[god-philosophy-universities]] ch.11); (2) the Dizionario's ANALOGIA entry (cross-referenced twice by material read this session, ties directly to [[Gerarchia degli Esseri e Analogia]]) and its Parte Seconda author-entry on Aquinas himself, if one exists; (3) Tertia Pars qq.1-59 (the Incarnation itself) — not yet deep-ingested from the Summa Teologica primary text at all; (4) [[sul-male-de-malo]] Qq. 7-16 plus full text for Qq. 1-6; (5) [[le-thomisme-gilson]] chs. II-XIV; (6) most of [[mondin-dizionario-tommaso]] (~36 of 39 entries).
- No page yet for Jacques Maritain — flagged in [[index]] Gaps.
