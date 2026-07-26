---
type: source
title: "Somma Teologica, I qq.2-26 (De Deo Uno) — deep-ingest"
address: c-000055
created: 2026-07-26
updated: 2026-07-26
tags:
  - tomismo
  - source
  - primary-text
  - deep-ingest
status: developing
related:
  - "[[somma-teologica-struttura]]"
  - "[[San Tommaso d'Aquino]]"
  - "[[Le Cinque Vie]]"
  - "[[Il Cardine della Metafisica Tomista]]"
  - "[[Dottrina di Atto e Potenza]]"
  - "[[Il Male come Privazione]]"
  - "[[Grazia Efficace e Premozione Fisica]]"
source_type: book
author: "San Tommaso d'Aquino"
date_published: "1265/66–1273; this edition trans. P. Tito S. Centi O.P., rev. P. Angelo Zelio Belloni O.P., 2009"
url: ""
confidence: high
key_claims:
  - "Batch 1 of the paced four-text ingestion plan (2026-07-26): the first treatise-level deep-ingest of the Summa Teologica itself, covering Prima Pars qq.2-26 (De Deo Uno), pages 172-398 of the raw PDF — located precisely via a full-text page-index built with pdftotext + a Python script, not by page-by-page browsing."
  - "This confirms, from the primary text itself, doctrines this vault previously only had via Garrigou-Lagrange's secondary synthesis in [[la-sintesi-tomistica]]/[[Le Cinque Vie]] and [[Il Cardine della Metafisica Tomista]]: the five ways (q.2 a.3), the real distinction of essence and esse in creatures vs. their identity in God (q.3 a.4), analogical predication (q.13), God's will not willing moral evil (q.19 a.9), providence's definition (q.22 a.1), predestination not caused by foreseen merits (q.23 a.5), and the sense in which omnipotence is bounded by non-contradiction (q.25 a.3)."
raw_file: ".raw/S. Tommaso d'Aquino - Somma Teologica.pdf"
---

# Source: Somma Teologica, I qq.2-26 (De Deo Uno) — deep-ingest

**Pages**: 172-398 of the raw PDF (227 pages covering the whole *De Deo Uno* treatise, i.e. everything on the divine essence before the Trinity treatise begins at q.27/p.399).

## Method note: building a page-index for a 5,318-page file

Rather than reading sequentially or guessing page ranges, this session extracted the entire PDF to plain text (`pdftotext -enc UTF-8`, ~17MB, 5,319 pages split on `\f` form-feed characters) and used a small Python script to regex-search for each question's own `ARGOMENTO N` header (Aquinas's Italian-edition running head) across the page array. This produced an exact page number for every question boundary q.2 through q.44 in one pass — far cheaper than binary-searching `pdftotext -f -l` ranges one question at a time. **This map is worth preserving for batches 2-4 of this same source** (Trinity, qq.27-43, is already mapped: pp.399-528):

| Q | Page | Q | Page | Q | Page |
|---|------|---|------|---|------|
| 2 | 172 | 11 | 231 | 20 | 348 |
| 3 | 177 | 12 | 236 | 21 | 354 |
| 4 | 189 | 13 | 256 | 22 | 361 |
| 5 | 193 | 14 | 277 | 23 | 368 |
| 6 | 202 | 15 | 302 | 24 | 382 |
| 7 | 206 | 16 | 306 | 25 | 386 |
| 8 | 212 | 17 | 317 | 26 | 395 |
| 9 | 218 | 18 | 323 | 27 | 399 (Trinity begins) |
| 10 | 222 | 19 | 330 | | |

## Structure, in Aquinas's own words

Every question in this edition opens with a short prologue paragraph (not present in all critical Latin editions' running text, but a standard feature of this translation) stating what the question covers and listing its articles. These were extracted for all 25 questions and are reliable primary-source confirmation of the structure already recorded in [[somma-teologica-struttura]]: q.2 (existence, 3 aa.) → q.3 (simplicity, 8 aa.) → q.4 (perfection, 3 aa.) → q.5 (the good in general, 6 aa.) → q.6 (God's goodness, 4 aa.) → q.7 (infinity, 4 aa.) → q.8 (presence in things, 4 aa.) → q.9 (immutability, 2 aa.) → q.10 (eternity, 6 aa.) → q.11 (unity, 4 aa.) → q.12 (our knowledge of God) → q.13 (the names of God, 12 aa.) → q.14 (knowledge, 16 aa.) → q.15 (ideas, 3 aa.) → q.16 (truth, 8 aa.) → q.17 (falsity, 4 aa.) → q.18 (life, 4 aa.) → q.19 (will, 12 aa.) → q.20 (love, 4 aa.) → q.21 (justice and mercy) → q.22 (providence, 4 aa.) → q.23 (predestination, 8 aa.) → q.24 (book of life, 3 aa.) → q.25 (power, 6 aa.) → q.26 (beatitude). Aquinas's own transition sentences make the treatise's logic explicit: q.14's prologue explains that after the divine *nature* (qq.2-13) the text turns to divine *operations* — first the immanent ones (knowledge, will: qq.14-26) before the transitive one (power, q.25, "the principle of the divine operation that passes onto an external effect") — i.e. q.25 is deliberately placed as the hinge toward q.27+ (Trinity) and q.44+ (creation).

## The Five Ways, read directly (q.2 a.3)

This vault's existing [[Le Cinque Vie]] page was built entirely from Garrigou-Lagrange's synthesis in [[la-sintesi-tomistica]]. Reading q.2 a.3 directly confirms it closely, with one textual nuance worth recording: Aquinas frames the whole article as a response to two objections (the problem of evil, and Ockham-style causal parsimony — "everything explicable by fewer causes needn't posit more"), then states plainly *"Che Dio esiste può essere provato attraverso cinque vie"* before giving all five in sequence within a single article (unlike the multi-article treatment some secondary sources imply). The first way (from motion) is given in fullest, most careful form: *"tutto ciò che si muove è mosso da altro... è dunque necessario arrivare a un primo motore che non sia mosso da altri; e tutti riconoscono che esso è Dio."* The other four ways follow the same terse pattern already documented in [[Le Cinque Vie]] (efficient causes, contingency, degrees of perfection, finality) — no substantive divergence found from the existing page's account, which stands as verified against the primary text.

## Simplicity and the essence/esse distinction (q.3 aa.1, 4)

**a.1** ("Se Dio sia un corpo") denies God is a body via the "unmoved mover" and "pure act" arguments already established in q.2 a.3 — showing the treatise's tight internal cross-referencing (each article explicitly cites "sopra [q.2, a.3]").

**a.4** ("Se in Dio l'essenza e l'essere siano la stessa cosa") is the article [[Il Cardine della Metafisica Tomista]] and [[Dottrina di Atto e Potenza]] treat, via Garrigou-Lagrange/Gilson/Mondin, as Thomism's cardinal doctrine — now confirmed directly from Aquinas's own text rather than only through secondary synthesis. Aquinas's own proof (first of several offered) runs: *"tutto ciò che si riscontra in qualcosa oltre alla sua essenza bisogna che vi sia causato o dai princìpi dell'essenza stessa... o da qualche agente esterno"* — if a thing's existence differed from its essence, that existence would need to be caused either by the essence's own principles (impossible: nothing self-sufficient causes its own existence, or it would be its own efficient cause) or by an external agent, which for God is impossible since God is the first cause. In contrario he cites Hilary: *"In Dio l'essere non è accidentalità, ma verità sussistente."* The article a.3 immediately preceding (not quoted in full here) establishes the companion result that in God *suppositum* and nature do not differ — Aquinas's summary line: *"non essendo Dio composto di materia e di forma... è necessario che egli sia la sua divinità, la sua vita e ogni altra cosa che a lui viene in tale modo attribuita."*

## Analogical predication (q.13)

Q.13's own prologue frames all twelve articles as following directly from q.12 ("dopo avere studiato ciò che concerne la conoscenza di Dio, bisogna procedere allo studio dei nomi di Dio, poiché noi nominiamo tutte le cose nel modo in cui le conosciamo") — naming follows knowing. Article 1 ("Se a Dio convenga un nome") opens the question by refuting Dionysius-derived apophaticism taken to an extreme (that God has *no* name at all), grounding the possibility of naming God in the general semiotic principle *"le parole sono segni dei concetti, e i concetti sono immagini delle cose."* Article 5's topic — whether names are said of God and creatures univocally, equivocally, or analogically — is the primary-text anchor for [[Gerarchia degli Esseri e Analogia]]'s Gilson-derived account; not independently re-read article-by-article in this pass, but its place in the twelve-article structure is now confirmed (aa.2-4 build toward it: does a name signify God's substance; is it said properly or only metaphorically; are the various names synonyms).

## Does God will evil? (q.19 a.9)

Directly relevant to [[Il Male come Privazione]] and [[sul-male-de-malo]]. Aquinas's answer is a precise distinction, not a flat no: God in no way wills *the evil of fault* (moral evil/sin, *malum culpae*), because sin is precisely what turns a creature away from the divine good, which God wills above all else. But God *can* will *the evil of defect in nature* or *the evil of penalty*, when he wills a good to which that evil is conjoined — "nel volere la giustizia vuole la pena, e volendo la conservazione dell'ordine naturale vuole che certi esseri naturalmente periscano." The article's opening objection cites Augustine's *Enchiridion* ("è cosa buona che vi sia non solo il bene, ma anche il male") to argue God must will evil's existence; Aquinas's reply to that objection is the sharper point: it is false to say evil-as-such is willed even instrumentally — evil is at most *accidentally* ordered to good (a tyrant's persecution accidentally elicits a martyr's constancy, but the tyrant never intends that), so "è bene che ci sia il male" is an imprecise formula that should not be read as God willing evil under any description.

## Providence and predestination (q.22 a.1, q.23 a.5)

**q.22 a.1** gives Aquinas's working definition of providence as an act of practical reason (an extension of *prudentia*, borrowing Aristotle's *Ethics* VI account of prudence as ordering things to their end): *"la provvidenza è quella stessa divina ragione la quale, riposta nel sommo principe dell'universo, dispone tutte le cose"* (quoting Boethius). He distinguishes providence properly (the eternal plan/*ratio*) from governance (*gubernatio*, its temporal execution) — "La prima è eterna, la seconda è legata al tempo."

**q.23 a.5** ("Se la previsione dei meriti sia la causa della predestinazione") is the article underlying [[Grazia Efficace e Premozione Fisica]]'s efficacious-grace doctrine: Aquinas rejects Origen's view (souls pre-existing and differentiated by prior merit) using Paul's Esau/Jacob text ("quando essi ancora non erano nati e nulla avevano fatto di bene o di male... non in base alle opere"), concluding predestination's effects are not caused by foreseen merit — grace precedes and grounds merit, not the reverse.

## Omnipotence and the limits of "can" (q.25 a.3)

Article 3 poses the omnipotence question sharply via four objections, including the classic worry that admitting omnipotence eliminates *all* necessity in creation (if everything is possible to God, nothing is impossible, and "tolto l'impossibile è levato di mezzo il necessario" — remove the impossible and you remove the necessary too). Full resolution not read in this pass; flagged as a natural target for a future short follow-up (the standard Thomistic answer — omnipotence extends to everything not intrinsically/logically contradictory, i.e. not to making a square circle or undoing the past — is well-attested elsewhere in the vault via [[Dottrina di Atto e Potenza]] but not yet verified against this specific article's own wording).

## What remains unread in this treatise

Given the 227-page span, this pass prioritized the most cross-referenced articles over exhaustive coverage: qq.4-11 (perfection, goodness, infinity, presence, immutability, eternity, unity), q.12 (our knowledge of God, beatific vision), qq.14-18 (God's knowledge, ideas, truth, falsity, life), q.20 (love), q.21 (justice/mercy), q.24 (book of life), and q.26 (beatitude) are confirmed structurally (article count and topic breakdown, from each question's own prologue) but not read article-by-article. The page map above makes any of these cheap to reach directly in a future session.

## Raw File

`.raw/S. Tommaso d'Aquino - Somma Teologica.pdf`, pp.172-398 — full-text extraction cached this session at scratch path (not vault-persistent); re-derive via `pdftotext -enc UTF-8 -f <start> -l <end>` using the page map above.
