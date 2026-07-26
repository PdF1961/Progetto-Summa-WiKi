---
type: source
title: "Quaestiones disputatae de veritate, qq.1, 16, 17, 24 — deep-ingest (OCR)"
address: c-000061
created: 2026-07-26
updated: 2026-07-26
tags:
  - tomismo
  - source
  - primary-text
  - deep-ingest
  - ocr
status: developing
related:
  - "[[sulla-verita-de-veritate]]"
  - "[[essenza-e-attualita-del-tomismo]]"
  - "[[San Tommaso d'Aquino]]"
  - "[[god-philosophy-universities]]"
  - "[[sul-male-de-malo]]"
  - "[[Il Male come Privazione]]"
source_type: book
author: "San Tommaso d'Aquino"
date_published: "1256-1259 (composition, per Mandonnet); this edition a 2011 parallel Latin-Italian critical text with introduction by Fernando Fiorentino"
url: ""
confidence: high
key_claims:
  - "First real ingest of this source: previously logged as fully unreadable (pure image scan, no OCR text layer, exceeds 100MB direct-image-viewing limit). Using the OCR pipeline verified in a prior session (pdftoppm/PyMuPDF rasterization + tesseract -l ita+lat), this file is in fact readable at high quality, and turns out to be a full parallel Latin-Italian critical edition (introduction and notes by Fernando Fiorentino), not Latin-only as first suspected from a low-resolution reconnaissance pass."
  - "Method: rendered pages via PyMuPDF (fitz) in-process rather than repeated pdftoppm subprocess calls — ~0.35s/page vs ~5s/page, a ~14x speedup — then OCR'd with tesseract. Two-column bilingual layout means low-resolution OCR interleaves the Latin and Italian columns into garbled mixed lines; re-rendering at 3x zoom (≈216dpi) and using tesseract --psm 6 resolved this for the passages actually quoted, though the article's opening 'objections' list (shorter per-line text) still interleaves somewhat while longer continuous prose (the RESPONSIO/RISPONDO sections) reads cleanly."
  - "Confirms directly from primary text: the triple definition of truth at q.1 a.1, correctly attributing 'veritas est adaequatio rei et intellectus' to Isaac (Israeli), not to Aquinas's own coinage; synderesis as either a natural habit or reason's power joined to that habit (q.16 a.1); conscience as binding through knowledge alone, analogous to physical contact transmitting force (q.17 a.3); and free will grounded in man being 'causa sui' — cause of his own acts (q.24 a.1)."
raw_file: ".raw/S. Tommaso d'Aquino - Sulla Verità.pdf"
---

# Source: Quaestiones disputatae de veritate, qq.1, 16, 17, 24 — deep-ingest

**Format**: image-only PDF scan, 1,152 pages, page size ~3065×2132pt (large-format), no embedded text layer — confirmed genuinely unreadable by `pdftotext`, but readable via OCR.

## The OCR pipeline used, and a speed discovery

The pipeline verified in a prior session (`pdftoppm -r 300` + `tesseract -l ita+lat`) works, but is slow on this file's oversized pages (~5s/page for rasterization alone). This session used **PyMuPDF (`fitz`) instead of `pdftoppm`** for rasterization — rendering in-process via `page.get_pixmap()` rather than spawning a subprocess per page — which cut rasterization to **~0.35s/page, roughly a 14x speedup**, making reconnaissance across a 1,152-page file practical. Combined with tesseract OCR (~3-8s/page depending on resolution), this made it feasible to locate specific questions by content search rather than exhaustive page-by-page indexing.

**Locating question boundaries**: this book has no embedded outline/bookmarks (`doc.get_toc()` returns empty) and OCR of running headers is inconsistent (page headers alternate between the author's name and, at question boundaries, the question's own title — e.g. `QUESTIONE 18 · LA CONOSCENZA DEL PRIMO UOMO NELLO STATO D'INNOCENZA`). Question boundaries were found via sparse sampling (every 4th page) searching for question-specific Latin vocabulary (`synderesis`, `conscientia`, `liberum arbitrium`), anchored against an initial proportional estimate from the known location of q.1 (p.59 of the PDF) and the book's total length. Confirmed boundaries this session: **q.1 starts p.59**, **q.16 (synderesis) starts ~p.600-604**, **q.17 (conscience) starts ~p.611**, **q.18 starts p.628** (confirming q.17 ends by p.627), **q.23 (voluntas Dei) starts p.760**, **q.24 (liberum arbitrium) starts ~p.793-794**.

## A parallel Latin-Italian edition — not Latin-only

A low-resolution reconnaissance pass (used only to locate question boundaries cheaply) misread this as a **Latin-only** critical edition, because tesseract's default page segmentation interleaves the two side-by-side columns into garbled mixed lines at low resolution, especially in the shorter-lined objection lists. Re-rendering at 3x zoom (≈216dpi) and OCR'ing with `--psm 6` revealed this is in fact a **parallel Latin-Italian text**: Fernando Fiorentino's Italian introduction and notes (the book's first ~59 pages) precede Aquinas's Latin text with a facing Italian translation, matching the format already familiar from this vault's Somma Teologica batches. Long continuous prose (each article's *Responsio*/*Rispondo* section) OCRs cleanly into one readable Italian block; the terser numbered-objection lists still interleave somewhat and would benefit from a genuine column-split before OCR in any future, more exhaustive pass on this source.

## Q1, a.1: the triple definition of truth

Confirms, from the primary text itself, the doctrine [[essenza-e-attualita-del-tomismo]] builds its truth-vs-pragmatism polemic on. After working through objections that would collapse *verum* into *ens* without remainder, Aquinas's *Respondeo* gives the analysis MacIntyre-adjacent and Garrigou-Lagrange-adjacent secondary sources summarize, but now in Aquinas's own words (translated from the parallel Italian): truth adds to being the *conformity or adequation of thing and intellect* — "la conformità o l'adeguazione della cosa e dell'intelletto" — arising because "il primo rapporto dell'ente con l'intelletto è che l'ente concordi con l'intelletto." He then distinguishes **three ways truth gets defined**, depending on which of three moments one names:

1. **What truth is grounded in** (the thing's own being, prior to any comparison with intellect): Augustine's *Soliloquia* — "*verum est id quod est*" ("the true is that which is").
2. **What truth formally consists in** — the actual conformity itself: here Aquinas is explicit that the famous formula is **not his own coinage but Isaac's** — "così Isaac dice che «la verità è l'adeguazione della cosa e dell'intelletto»" (*veritas est adaequatio rei et intellectus*) — with Anselm's *De veritate* cited alongside as an equivalent formulation ("*veritas est rectitudo sola mente perceptibilis*").
3. **Truth's consequent effect** (knowledge): Hilary — "*verum est declarativum et manifestativum esse*" — and Augustine's *De vera religione*.

This three-way taxonomy is a genuine addition to what this vault previously had on file (which cited only the middle formula as "the" definition) — it shows Aquinas treating *adaequatio* as one of three legitimate, non-competing ways of defining truth depending on explanatory priority, not the sole correct formula. Worth folding into any future revision of the truth-vs-pragmatism material in [[essenza-e-attualita-del-tomismo]] or [[la-sintesi-tomistica]] Parte Ottava cap. III (still flagged unread there).

## Q16, a.1: what synderesis is

Aquinas surveys three prior opinions — synderesis as a power distinct from and superior to reason; as reason itself under a different *ratio* (reason-as-reasoning vs. reason-as-naturally-knowing); or as reason's power joined with a natural habit — before resolving that synderesis names either **a natural habit** (analogous to the habit of first principles, *intellectus principiorum*, in speculative matters) **or reason's power united with that habit**, with little practical difference between the two framings. The argument's backbone is a participation principle from Dionysius: "la sapienza divina congiunge le parti terminali delle realtà prime con le parti iniziali delle realtà seconde" — a lower nature touches, at its own highest point, something proper to the nature above it (the human soul, at its summit, touches something proper to angelic knowledge — namely, knowing without inquiry). This natural habit of first practical principles is called a "seminarium" (seedbed) of all subsequent practical knowledge, exactly parallel to how the *intellectus principiorum* seeds all speculative knowledge. Directly relevant to [[god-philosophy-universities]] ch.10's natural law material and [[somma-teologica-trattato-legge]]'s q.94 (where this vault already has the Summa's more compressed parallel treatment) — this is the fuller, earlier, dialectically richer primary-text source for the same doctrine.

## Q17: what conscience is, and why it binds

**a.1** poses whether conscience is a power, habit, or act, citing Jerome (on Ezekiel: conscience "falls" in a way synderesis doesn't, suggesting they're not simply identical), Basil ("natural judicatory"), and Damascene ("the law of our intellect") — the objections and counter-citations are extensive; the article's own resolution wasn't fully re-transcribed in this pass (flagged for follow-up) but the standard Thomistic answer — conscience is an *act* (the application of knowledge, ultimately including the synderesis-habit's content, to a particular case) rather than a power or habit in its own right — is presupposed by a.3's argument.

**a.3** ("Utrum conscientia liget" — whether conscience binds) gives a striking analogical argument: physical binding requires *contact* (a material agent only necessitates what it physically touches); the analogous "contact" in the moral/spiritual order is **knowledge** — "come nelle realtà materiali l'agente materiale agisce per mezzo del contatto, così nelle realtà spirituali il comando lega per mezzo della conoscenza." Since conscience is nothing but "l'applicazione della conoscenza all'atto" (the application of knowledge to an act), it binds precisely by transmitting the force of a command through that knowledge — ultimately, the reply to objection 3 makes explicit, because "quantunque l'uomo non sia superiore a se stesso, tuttavia gli è superiore colui, di cui conosce il comando; e quindi è legato dalla sua coscienza" — one is not bound by *oneself*, but by the superior authority (ultimately God) whose command one's conscience makes known, so one is bound by conscience *derivatively*, as the vehicle of that command's contact with one's own action, not because conscience is somehow self-authorizing.

## Q24, a.1: free will as being "causa sui"

The article's *Respondeo* opens without hedging: "senza alcun dubbio bisogna sostenere che l'uomo è libero per arbitrio" — supported by faith (merit/demerit require it), by manifest evidence (people visibly choose one thing and reject another), and by demonstrative reason. The reasoning: things that move or act divide into those with an external principle of motion (things moved by violence, where "the patient contributes nothing of its own") and those with an internal principle; among the latter, some move *themselves* (animals) while others have an internal principle without being self-movers (heavy/light bodies falling or rising, which cannot be divided into a moving part and a moved part). Aquinas then invokes Aristotle's definitions directly: what is moved by an external principle cannot be called free, because "libero è «ciò che è causa di se stesso»" (*liberum est quod sui causa est*, *Metaphysics* I) — freedom requires being the *cause* of one's own motion, which only self-movers achieve. The chain of reasoning (not fully followed to its conclusion in this pass) proceeds to argue that among self-movers, only those whose self-motion is *guided by cognition of an end* — i.e., rational agents — possess free will properly speaking, distinguishing man from mere animal self-movers. This is the primary-text root of the "causa sui" formula this vault has previously seen only in application (e.g. God as *causa sui* in a different, analogically prior sense in the divine-attributes material) — worth cross-checking against [[sul-male-de-malo]] q.6 (free will and the possibility of sinning) in a future pass, not done here.

## What remains unread

The article bodies of q.1 aa.2-12, q.16 a.2, q.17 aa.1-2 and 4-5 (this session read only a.3 in full), and q.24's remaining articles, plus the other 25 questions of the work entirely (q.11's *De Magistro* remains a high-value target given [[god-philosophy-universities]] ch.11's parallel treatment of Aquinas's philosophy of teaching, as already flagged in [[sulla-verita-de-veritate]]). The page-boundary findings above make locating any of these considerably cheaper for a future session than the blind search this session required.

## Raw File

`.raw/S. Tommaso d'Aquino - Sulla Verità.pdf` — no text layer; readable only via OCR. Boundaries found this session: q.1 p.59, q.16 p.~600-604, q.17 p.~611-627, q.18 p.628, q.23 p.760, q.24 p.~793-794.
