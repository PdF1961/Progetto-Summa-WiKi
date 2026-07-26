---
type: source
title: "Summa contro i Gentili, Libro I (l'esistenza di Dio) — deep-ingest"
address: c-000059
created: 2026-07-26
updated: 2026-07-26
tags:
  - tomismo
  - source
  - primary-text
  - deep-ingest
status: developing
related:
  - "[[somma-contro-i-gentili-struttura]]"
  - "[[somma-teologica-de-deo-uno]]"
  - "[[Le Cinque Vie]]"
  - "[[San Tommaso d'Aquino]]"
  - "[[le-thomisme-gilson]]"
source_type: book
author: "San Tommaso d'Aquino"
date_published: "1259-1264/65; this edition trans. P. Tito S. Centi O.P., UTET Torino, 1975"
url: ""
confidence: high
key_claims:
  - "Batch 5 of the extended ingestion plan (2026-07-26, continuing after the 4-batch Somma Teologica plan): deep-ingest of Contra Gentiles Libro I ch.13, the chapter giving Aristotle's own philosophical proofs of God's existence — the primary-text counterpart to the Summa Teologica's Five Ways, argued at far greater length and using purely Aristotelian premises (no revelation) since this work addresses readers who don't share Christian premises."
  - "OCR quality note: this PDF's OCR frequently garbles 'CAPITOLO' as 'CaritoLo' or similar, and accented vowels often render as the replacement character. Chapter numbers in Roman numerals following that garbled word are still reliable; systematic chapter-header regex search is less reliable here than it was for the (non-OCR'd) Summa Teologica text, so this batch used targeted keyword search rather than building an exhaustive chapter-to-page index."
  - "Confirms Book I ch.13 gives exactly two proofs (both from motion, 'per due vie a partire dal moto'), not five — both drawn from Aristotle's Physics and Metaphysics, with an extended defense of each premise and an explicit handling of two objections (the eternity of the world; whether the first heavenly sphere is self-moved/animate) that the Summa Teologica's compressed First Way omits entirely."
raw_file: ".raw/S. Tommaso d'Aquino. - Somma contro i Gentili [ocr] [1975].pdf"
---

# Source: Summa contro i Gentili, Libro I — deep-ingest (ch.13, the proofs of God's existence)

**Pages**: Libro I runs approximately pp.54-265 of the raw PDF (confirmed by the "LIBRO PRIMO" running header, first appearing p.54, with "LIBRO SECONDO" first appearing p.266). Chapter 13 itself — the chapter read closely in this batch — runs roughly pp.80-90.

## Method note: this OCR is noisier than the Summa Teologica's

Unlike the Summa Teologica PDF (a clean digital text, not scanned), this Contra Gentiles file is genuinely OCR'd from a printed 1975 UTET edition, and the OCR has real error rates: "CAPITOLO" frequently comes out as "CaritoLo," accented vowels (è, à, ù) often render as the Unicode replacement character, and some words are corrupted mid-string (e.g. "ammaestrare" → "ammaestrare" is fine but "però" → "per�", "quest'ultima" garbled variously). This makes the page-index-via-regex technique used for the Summa Teologica (see [[somma-teologica-de-deo-uno]]) less reliable here — a search for `CAPITOLO I\b` would miss most chapter-1 headers. This batch instead used **content keyword search** (e.g. "motore immobile", "Averroè", "forma sostanziale del corpo") to locate specific doctrines directly, which worked well despite the header noise. Future batches on this source should do the same rather than trust a clean chapter-header index.

## Chapter 13: Aristotle's proofs of God's existence

Chapters 10-12 (not read in this pass) first establish that God's existence, while not self-evident to us (contra Anselm-style *per se nota* views) and not a matter of unaided faith alone (contra fideists), **is** demonstrable by reason from sensible effects — the same *a posteriori* methodological framing later compressed into *S.Th.* I q.2. Chapter 13's own opening states the plan explicitly: *"passiamo a riferire gli argomenti con i quali i filosofi e i Dottori della Chiesa Cattolica hanno dimostrato l'esistenza di Dio. Prima riferiamo gli argomenti di cui si serve Aristotele... cercando di farlo per due vie a partire dal moto."*

**First way** (from *Physics* VII): *"Tutto ciò che è in moto è mosso da altri... Ma [il motore] o è esso stesso in moto, oppure è immobile... Perciò, o si procede così all'infinito, oppure si deve arrivare a un primo motore immobile. Ma non si può procedere così all'infinito. Dunque è necessario ammettere un primo motore immobile."* Aquinas then spends several pages proving each of the argument's two load-bearing premises in turn (that whatever moves is moved by another; that an infinite regress of movers is impossible) via Aristotle's own arguments from *Physics* VI and VIII — far more elaborated than the Summa Teologica's terse parallel statement of the same proof.

**Second way** (from *Physics* VIII, the self-mover argument): explores the alternative Aristotelian route — that the first mover might itself be self-moved — and shows this still requires distinguishing, within any self-mover, a moving part and a moved part, so that *"si deve concludere che chi muove se stesso ha una parte che muove e una parte che è mossa"* and the same conclusion (an unmoved first mover) follows regardless.

**Two objections handled explicitly** (absent from the Summa's parallel treatment): (1) both proofs presuppose the Aristotelian thesis that motion is eternal, which Catholics hold false — Aquinas's reply: the argument works even *more* easily if the world had a temporal beginning, since then a cause of that beginning is needed regardless; eternity of motion is the *harder* case Aristotle chose deliberately, not a premise Aquinas himself endorses. (2) The proofs presuppose the outermost heavenly sphere moves itself (i.e., is animate) — Aquinas's reply: if one denies this, the sphere must instead be moved directly by the wholly immobile first mover, so the conclusion (God's existence) survives either way. The chapter closes: *"deve esserci un primo motore del tutto immobile, che è Dio."*

## Comparison with the Summa Teologica's Five Ways

Read alongside [[Le Cinque Vie]] and [[somma-teologica-de-deo-uno]] (S.Th. I q.2 a.3), the contrast is instructive: the *Contra Gentiles* devotes an entire chapter (with sub-arguments, premise-proofs, and objection-handling) to what becomes just the *first* of the Summa's five compressed ways — reflecting the different genres (a sustained philosophical treatise for readers without Christian premises, vs. a compact theological textbook). The *Contra Gentiles* passage gives **only** arguments from motion in ch.13 itself; the efficient-causality, contingency, degrees-of-perfection, and finality arguments appear in later chapters of Book I (not mapped precisely in this pass — flagged for follow-up) rather than being bundled into one article as in the Summa. This confirms and sharpens (rather than contradicts) [[Le Cinque Vie]]'s existing account.

## What remains unread

Chapters 1-12 (methodology: the sapiential task, philosophy vs. revelation in theology, the demonstrability debate) and chapters 14-102 (the divine attributes: simplicity, perfection, goodness, infinity, immutability, eternity, unity, God's self-knowledge, will — the structure already recorded at a high level in [[somma-contro-i-gentili-struttura]]) were not read article-by-article in this pass. Given this vault's existing coverage via the Summa Teologica batches, the highest-value future target here would be the chapters unique to the Contra Gentiles' more argumentative style — particularly any chapter engaging Avicenna or Averroes directly on divine attributes, given how central that engagement turns out to be in Libro II (see [[contra-gentiles-libro-secondo]]).

## Raw File

`.raw/S. Tommaso d'Aquino. - Somma contro i Gentili [ocr] [1975].pdf`, Libro I ≈ pp.54-265, ch.13 ≈ pp.80-90.
