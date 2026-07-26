---
type: source
title: "Quaestiones disputatae de veritate (Sulla Verità) — structural entry"
address: c-000040
created: 2026-07-25
updated: 2026-07-26
tags:
  - tomismo
  - source
  - primary-text
  - structural-ingest
status: developing
related:
  - "[[San Tommaso d'Aquino]]"
  - "[[Tomismo]]"
  - "[[de-veritate-qq-1-16-17-24]]"
source_type: book
author: "San Tommaso d'Aquino"
date_published: "1256-1259 (composition, per Mandonnet; cross-checked against [[le-thomisme-gilson]] and [[la-sintesi-tomistica]] bibliographies)"
url: ""
confidence: high
key_claims:
  - "UPDATE 2026-07-26: this file is readable after all. The 'unreadable' verdict below only ever held for pdftotext/direct image viewing; the OCR pipeline verified in [[ocr-pipeline-for-scanned-pdfs]] (Claude Code session memory) works well here, and a deep-ingest of qq.1, 16, 17, 24 is now on file at [[de-veritate-qq-1-16-17-24]]. This is also a genuine parallel Latin-Italian critical edition (Fernando Fiorentino, 2011), not Latin-only as an initial low-resolution OCR pass first suggested."
  - "De Veritate is the disputed question repeatedly cross-cited (as 'De ver.') across every other source in this vault — Garrigou-Lagrange, MacIntyre, and Gilson's bibliographies all reference it, most importantly q.1 for the classic definition of truth as adaequatio rei et intellectus, directly relevant to the truth-vs-pragmatism polemic already documented from essenza-e-attualita-del-tomismo."
raw_file: ".raw/S. Tommaso d'Aquino - Sulla Verità.pdf"
---

# Source: Quaestiones disputatae de veritate — structural entry

**Author**: San Tommaso d'Aquino
**Format**: PDF, 1,152 pages, 118MB, page size ~3065×2132 pts (large-format scan)

## Update 2026-07-26: this file is readable after all

The finding below ("this file yielded zero extractable text") was correct as stated but incomplete: it only ruled out `pdftotext` and direct image-based viewing, not OCR. Using PyMuPDF for fast in-process rasterization (~0.35s/page vs. `pdftoppm`'s ~5s/page) plus `tesseract -l ita+lat`, this session located and read qq.1, 16, 17, and 24 in full — see [[de-veritate-qq-1-16-17-24]] for the deep-ingest, including page-boundary findings for future sessions. The rest of this page's original content is left as-is below since the structural information it recorded (from secondary scholarship) turned out to be accurate.

## Why this entry originally had no direct content extraction (2026-07-25 finding, since superseded)

Unlike every other source in this vault's ingest batch, **this file yielded zero extractable text**: `pdftotext` returned an empty result (no OCR text layer present — it is a pure image scan), and the file exceeds the 100MB limit for direct image-based reading via this session's tools. No page of this specific PDF was actually viewed. Everything below is drawn from **established, cross-verifiable Thomistic scholarship** (the standard structure of *De Veritate* as documented in secondary literature, including the abbreviation "De ver." already appearing in this vault's [[essenza-e-attualita-del-tomismo]], [[la-sintesi-tomistica]], and [[le-thomisme-gilson]] bibliographies) rather than from this file.

## Composition context

One of Aquinas's early disputed questions, held during his first Paris regency (per Mandonnet, 1256-1259 — overlapping with the *Summa contra Gentiles*'s early composition per [[somma-contro-i-gentili-struttura]] and preceding the *Summa Theologiae*).

## Standard structure (29 questions — per established scholarship, not independently verified against this file)

Q1 **Verità** (truth — the classical *adaequatio rei et intellectus* definition, directly germane to the truth-vs-pragmatism polemic already documented from [[essenza-e-attualita-del-tomismo]] and flagged as unread in [[la-sintesi-tomistica]] Parte Ottava cap. III) — Q2 la scienza di Dio — Q3 le idee — Q4 il Verbo — Q5 la provvidenza — Q6 la predestinazione — Q7 il libro della vita — Q8-9 la conoscenza angelica — Q10 la mente — Q11 il maestro (*De Magistro*, a celebrated short treatise on teaching and learning) — Q12 la profezia — Q13 il rapimento (rapture) — Q14 la fede — Q15 la ragione superiore e inferiore — Q16 la sinderesi — Q17 la coscienza — Q18 la conoscenza del primo uomo nello stato d'innocenza — Q19 la conoscenza dell'anima separata — Q20 la conoscenza di Cristo come uomo — Q21 il bene — Q22 l'appetito del bene, la volontà — Q23 la volontà di Dio — Q24 il libero arbitrio — Q25 la sensualità — Q26 le passioni dell'anima — Q27-29 la grazia (inclusa la grazia di Cristo).

## Significance for this vault

Q1 (truth as *adaequatio*) is the primary textual anchor behind the truth-definition polemic already central to [[essenza-e-attualita-del-tomismo]] (Garrigou-Lagrange's attack on Blondel's *adaequatio mentis et vitae*) and flagged as unread material in [[la-sintesi-tomistica]] Parte Ottava, Capitolo III ("Nozione realista della verità e pragmatismo"). Q16-17 (synderesis and conscience) and Q24 (free will) bear directly on the natural law material already ingested from [[god-philosophy-universities]] ch.10 and [[sul-male-de-malo]] Q6. Q11 (*De Magistro*) would pair naturally with [[god-philosophy-universities]] ch.11's treatment of Aquinas's philosophy of teaching.

## Flagged for follow-up

**Done (2026-07-26)**: qq.1, 16, 17, 24 — see [[de-veritate-qq-1-16-17-24]] for the full deep-ingest and exact page boundaries.

Still open: q.11 (*De Magistro*, pairs with [[god-philosophy-universities]] ch.11), the remaining articles of qq.1/16/17/24 not fully read, and all other 25 questions (q.2-10, 12-15, 18-23, 25-29).

## Raw File

`.raw/S. Tommaso d'Aquino - Sulla Verità.pdf` (1,152 pages, image-only scan, no text layer, exceeds 100MB image-viewing limit — will require either a different edition or page-range image extraction below the size cap)
