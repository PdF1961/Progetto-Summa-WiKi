---
type: source
title: "Dizionario Interdisciplinare di Scienza e Fede — voci Anima, Finalità, Leggi Naturali (deep-ingest, OCR)"
address: c-000062
created: 2026-07-26
updated: 2026-07-26
tags:
  - source
  - primary-text
  - deep-ingest
  - ocr
  - scienza-e-fede
status: developing
related:
  - "[[dizionario-interdisciplinare-scienza-fede]]"
  - "[[somma-teologica-trattato-legge]]"
  - "[[contra-gentiles-libro-secondo]]"
  - "[[Angeli e Anima Umana (Sintesi Tomistica)]]"
  - "[[Gerarchia degli Esseri e Analogia]]"
  - "[[sul-male-de-malo]]"
source_type: book
author: "a cura di Giuseppe Tanzella-Nitti e Alberto Strumia"
date_published: "2002 (Urbaniana University Press); this file a 2022 Print-to-PDF scan"
url: ""
confidence: high
key_claims:
  - "First real ingest of this source: previously logged as fully unreadable (668MB print-to-PDF scan, no text layer, vastly exceeding the 100MB direct-viewing limit). Using PyMuPDF for fast in-process rasterization (~0.1s/page on this file's normal A4 pages — far faster than either the De Veritate or earlier pdftoppm benchmarks) plus tesseract OCR, the book turns out to be efficiently navigable: running page headers name the current dictionary entry directly, and the front matter (p.27-29) contains a full alphabetical 'Indice delle Voci' plus a subject-area classification table (p.30-31)."
  - "Located and read three of the entries flagged as highest-priority for this vault's Thomistic focus: ANIMA (the soul, pp.~84-101), FINALITÀ (teleology, pp.~650-671), and LEGGI NATURALI (natural law, pp.~776-807) — out of 109 thematic entries total (Parte Prima, pp.33-1530) plus a second part of author-biography entries (Parte Seconda, pp.1531-2164)."
  - "Both ANIMA and LEGGI NATURALI cite, chapter-and-verse, the exact primary-text passages this vault ingested earlier the same day: ANIMA cites Contra Gentiles II c.56 and Summa Theologiae I q.51 a.1 / I q.75 a.6 on the soul as forma corporis; LEGGI NATURALI cites Summa Theologiae I-II q.93-94 (eternal law, natural law) nearly verbatim to how this vault's own somma-teologica-trattato-legge.md batch summarizes them."
raw_file: ".raw/Dizionario Interdisciplinare di Scienza e Fede (NP).pdf"
---

# Source: Dizionario Interdisciplinare di Scienza e Fede — voci Anima, Finalità, Leggi Naturali

**Format**: 2,339-page A4 Print-to-PDF scan (Microsoft Print To PDF from an XPS source), no text layer, 668MB.

## This file is readable — and unusually navigable, once OCR'd

The 2026-07-25 placeholder entry marked this "unreadable with current tools." That verdict held for `pdftotext` and direct image viewing, not for OCR. PyMuPDF rasterizes this file's normal-sized A4 pages at **~0.1s/page** (vs. ~0.35s/page for De Veritate's oversized scan pages, and ~5s/page for `pdftoppm` on either) — fast enough that OCR-ing dozens of pages for reconnaissance is cheap. Two structural features made this book unusually easy to navigate once that was possible:

1. **Running headers name the current entry directly** (e.g. `Anima 94`, `Finalità`, `Leggi naturali 784`) — no need to infer location from content alone.
2. **A full front-matter index exists**: p.7's `INDICE GENERALE` gives exact page numbers for every major section (confirmed to map 1:1 with PDF page numbers from p.9 onward — pp.1-8 are front-cover/copyright pages interleaved with blank "torrossa.com" licensing-watermark pages that don't follow the same numbering); p.27-28 lists all **109 thematic entries** ("Voci Tematiche") alphabetically with no per-entry page number, but combined with the section boundaries (**Parte Prima**, thematic entries, pp.33-1530; **Parte Seconda**, entries on individual thinkers, pp.1531-2164; **Parte Terza**, magisterial documents/anthologies/indices, pp.2165-2339) and the running-header trick above, any entry can be located by a short proportional-estimate-then-sample search, the same technique used on the Contra Gentiles and De Veritate earlier this session.

**Entries relevant to this vault's Thomistic focus, per the p.30-31 "Aree disciplinari" classification table**: ANALOGIA, ANGELI, ANIMA, CREAZIONE, DIO, FINALITÀ, LEGGI NATURALI, METAFISICA, RAGIONE, VERITÀ all fall under "area teologica" or "area filosofica" — a substantially larger set than the three read in this pass, flagged for follow-up below.

## ANIMA (pp.~84-101): the soul, from patristics to Kant

A long historical survey — Justin Martyr, Athenagoras, Irenaeus, Tertullian ("*caro cardo salutis*"), then Origen's Platonizing dissent, then Augustine (soul's priority over body, rejection of both Plotinian emanationism and Origenist pre-existence, unresolved between traducianism and individual creationism) — before reaching Aquinas directly (p.92):

> «Il corpo non è unito in modo accidentale all'anima, perché il più profondo essere dell'anima è lo stesso essere del corpo, e dunque un essere comune ad entrambi» (*Quaestio disputata de anima*, a.1, ad 1).

The entry states Aquinas's question precisely — can an incorruptible substance be the form of a corruptible body and constitute one substantial being with it? — citing ***Contra Gentiles* II, c.56** directly (the exact chapter this vault ingested earlier today, see [[contra-gentiles-libro-secondo]]) for the difficulty, and *Summa Theologiae* I q.51 a.1 ("appartiene all'anima umana unirsi al corpo") and I q.75 a.6 for the incorruptibility argument. Three of Aquinas's own emphases are drawn out: (a) the soul is form of the body by its own essence, not (per Avicenna) via separate potencies; (b) the human soul is the **single** form of the body — vegetative, sensitive, and rational at once, by one act of being, against any "plurality of forms" view; (c) the soul has metaphysical, not chronological, priority over the body.

The entry then traces the doctrine's contested reception: **Council of Vienne (1312)** officially taught the human soul is "*vere, per se et essentialiter*" the body's form — explicitly against Olivi's pluriform theory, and grounded, the entry notes, in **Christological** concerns (the unity of Christ's humanity) rather than philosophical psychology alone; the Paduan Averroists' single-common-intellect view and Pomponazzi's mortalism are named as the doctrine's later opponents. The article continues past Aquinas into Descartes (substance dualism, pineal-gland interaction), Malebranche (occasionalism), Spinoza (psychophysical parallelism, one substance under two modes), Leibniz (monadic pre-established harmony), Kant (soul as postulate of practical reason, not theoretically demonstrable), Hume (the self as "bundle of perceptions"), James, Russell, and Freud/Jung/Adler's depth psychology — a genuinely useful one-article survey of the whole soul/body debate this vault has so far only pieced together source by source.

## LEGGI NATURALI (pp.~776-807): from lex aeterna to physical law

Opens directly onto Aquinas (p.784): eternal law as *"ratio divinae gubernationis"* (*S.Th.* I-II q.93) and natural law as the created participation of rational creatures in that eternal law (*S.Th.* I-II q.94) — matching, nearly verbatim, this vault's own [[somma-teologica-trattato-legge]] summary of the same two questions, independently arrived at from the primary text earlier the same day. The entry adds a precise technical point not previously on file here: the analogy between divine "legislator" and human lawgiver is explicitly an **analogy of proportionality**, not a metaphor — cross-referencing its own ANALOGIA entry (§II.2) — meaning "law" is predicated of divine governance and human legislation according to a genuinely shared (if not univocal) ratio, not merely a figure of speech.

The entry then pivots to the **modern scientific sense of "law"**: a stable, verifiable, typically mathematically-formalized connection between observables. It draws a sharp methodological distinction between **linear** equations (e.g. Newton's second law, whose solution sets are closed under addition, giving full time-reversibility) and **nonlinear** ones (e.g. much of fluid dynamics, where predictability is far more sensitive to initial conditions), and notes that once thermodynamics' second law (an intrinsically time-asymmetric "arrow of time") enters the picture — extending well beyond thermodynamics proper into chemical and biological irreversibility — the resulting worldview is not a static, equilibrium cosmos but one with a genuine history. This is a useful explicit bridge between the classical *lex naturalis* (a normative, teleological notion) and the modern physical sense of "law" (a descriptive, mathematical regularity) that this vault has not previously had to characterize.

## FINALITÀ (pp.~650-671): teleology recast in systems language

Rather than opening with Aristotle's *causa finalis* by name (not found in the pages sampled — flagged for a closer read of the entry's opening sections, not done in this pass), the entry develops a **three-tier systematic vocabulary** for natural teleology: **direzionalità** (directionality — general tendencies whose actualization depends on circumstance), **cooperatività** (cooperativity — how entities and processes integrate into unified outcomes at every level of natural organization), and **funzionalità** (functionality — components mutually enabling each other's and the whole's activity, evident in organisms and extensible to nature as a whole relative to human life). These are explicitly presented as *"modi di agire che manifestano i rispettivi modi di essere"* (ways of acting that manifest their respective ways of being) — a formula that keeps faith with the classical *agere sequitur esse* principle while avoiding traditional Aristotelian vocabulary. The entry is explicit that this systematic account only *describes* natural finality, leaving finality's "*ultimate explanation*" to metaphysics and natural theology (cross-referencing its own METAFISICA entry) — i.e., the dictionary deliberately brackets the classical debate rather than adjudicating it. Section IV then surveys where contemporary cosmology (fine-tuning, the anthropic principle — Whitrow 1955, Dicke 1957) and evolutionary biology test or confirm this account of natural teleology.

## What remains unread

The bulk of both entries (ANIMA's own bibliography and remaining sections; FINALITÀ's opening sections I-III, its self-organization material, and its full anthropic-principle discussion; LEGGI NATURALI's remaining sections on the epistemology of physical law, flagged explicitly in the text itself as "torneremo più avanti, vedi infra, VI"), all 106 other thematic entries (Parte Prima), the ~90 author-biography entries (Parte Seconda, e.g. covering Aquinas himself, Aristotle, and any other cited philosopher/theologian as an individual entry), and Parte Terza's magisterial-document anthology. Given this vault's focus, **ANALOGIA** (cross-referenced twice above, and cited by both [[Gerarchia degli Esseri e Analogia]] and this session's Somma Teologica q.13 material) and the Parte Seconda entry on **Tommaso d'Aquino himself** (if one exists, not yet checked) are the highest-priority remaining targets.

## Raw File

`.raw/Dizionario Interdisciplinare di Scienza e Fede (NP).pdf` — no text layer, readable only via OCR. Front-matter index: p.7 (general index), p.27-29 (entry list), p.30-31 (subject classification). Entries found this session: ANIMA p.~84-101, FINALITÀ p.~650-671, LEGGI NATURALI p.~776-807.
