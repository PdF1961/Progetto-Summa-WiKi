---
type: meta
title: Operation Log
updated: null
tags:
  - meta
  - log
status: evergreen
related:
  - "[[index]]"
  - "[[hot]]"
  - "[[overview]]"
  - "[[Wiki/sources/_index]]"
---

# Operation Log

Navigation: [[index]] | [[hot]] | [[overview]]

Append-only. New entries go at the TOP. Never edit past entries.

---

## 2026-07-26 | OCR ingest | De Veritate + Dizionario Interdisciplinare (final front of the 4-text plan)

- Sources: `.raw/S. Tommaso d'Aquino - Sulla Verità.pdf` (1,152pp, large-format scan) and `.raw/Dizionario Interdisciplinare di Scienza e Fede (NP).pdf` (2,339pp, 668MB print-to-PDF) — both previously logged as fully unreadable (no text layer, exceed the 100MB direct-viewing limit). This closes the last remaining front of the four-text paced ingestion plan from 2026-07-25/26.
- Method: PyMuPDF (`fitz`) in-process rasterization instead of repeated `pdftoppm` subprocess calls — ~0.35s/page on De Veritate's oversized scan pages, ~0.1s/page on the Dizionario's normal A4 pages (vs. ~5s/page for `pdftoppm` on either) — then `tesseract -l ita+lat` OCR. No embedded PDF outline/bookmarks in either file (`doc.get_toc()` empty); question/entry boundaries found via sparse-sample content search anchored on proportional estimates, and (for the Dizionario) a genuine front-matter index plus running headers that name the current entry directly.
- Discovery: De Veritate is a parallel Latin-Italian critical edition (Fernando Fiorentino, 2011) — an initial low-resolution OCR pass misread it as Latin-only because two-column layouts interleave into garbled mixed lines at low resolution; re-rendering at 3x zoom and using `tesseract --psm 6` resolved this for the passages quoted.
- Pages created: [[de-veritate-qq-1-16-17-24]] (c-000061: qq.1 triple definition of truth, 16 synderesis, 17 conscience, 24 free will), [[dizionario-anima-finalita-leggi-naturali]] (c-000062: voci Anima, Finalità, Leggi Naturali)
- Pages updated: [[sulla-verita-de-veritate]] and [[dizionario-interdisciplinare-scienza-fede]] (both flipped from "unreadable" to structural-entry-plus-deep-ingest), [[essenza-e-attualita-del-tomismo]] (De Veritate q.1's three-way truth-definition taxonomy), [[god-philosophy-universities]] (De Veritate q.16's fuller synderesis treatment), [[sul-male-de-malo]] (cross-link only), [[somma-teologica-trattato-legge]] and [[Angeli e Anima Umana (Sintesi Tomistica)]] (independent third-source convergence — the Dizionario cites the *same* Contra Gentiles/Summa passages this vault ingested from primary text earlier the same day), [[Gerarchia degli Esseri e Analogia]] (analogy of proportionality applied to divine legislation)
- Key insight: the Dizionario's ANIMA and LEGGI NATURALI entries, written independently by specialist contributors in 2002 with no connection to this vault, cite the *exact same* primary-text passages (Contra Gentiles II c.56, S.Th. I q.51 a.1, S.Th. I-II qq.93-94) this vault had already ingested directly from the primary sources the same day — strong independent confirmation that this session's primary-text batches located the genuinely load-bearing passages, not incidental ones.
- Still open: 25 of 29 De Veritate questions, ~106 of 109 Dizionario thematic entries plus all of Parte Seconda/Terza — see each new page's "What remains unread" section.

---

## 2026-07-26 | lint pass | post-6-batch health check

- Trigger: routine lint after this session's 6 new deep-ingest pages (see the two batch-ingest entries below), per the "every 10-15 ingests" cadence in the vault's CLAUDE.md.
- Full report: [[lint-report-2026-07-26]]
- Fixed: (1) address counter desync — 6 addresses were assigned by hand rather than via the allocator, leaving `.vault-meta/address-counter.txt` stale; rebuilt via `--rebuild`. (2) `.raw/.manifest.json` address_map and both Summa PDFs' source entries hadn't been updated to reflect this session's new pages; fixed. (3) one real dead link in `wiki/hot.md` (pointed at a Claude Code memory file, not a vault page). (4) [[Wiki Map]]'s canvas was missing 7 pages (this session's 6 plus a pre-existing gap, [[cherry-picks]], from 2026-07-25) — regenerated with all 59 current content pages. (5) 8 pages had stale `updated:` frontmatter from substantive edits; bumped. (6) `wiki/index.md`'s summary header was stale.
- No orphans, no frontmatter gaps, no filename collisions, no duplicate addresses.

---

## 2026-07-26 | batch ingest | Summa contro i Gentili, 2 deep-ingests (batches 5-6, same-day follow-up)

- Source: `.raw/S. Tommaso d'Aquino. - Somma contro i Gentili [ocr] [1975].pdf` (1,374 pp.), continuing the extended plan after the Somma Teologica's 4 batches
- Method note: this file is genuinely OCR'd (unlike the Summa Teologica's clean digital text) and has real error rates ("CAPITOLO" often garbles to "CaritoLo," accents often render as replacement characters) — the clean regex chapter-index technique built for the Summa Teologica did not transfer well; used targeted content-keyword search instead (e.g. "motore immobile", "Averroè", "forma sostanziale del corpo") to locate doctrines directly.
- Pages created: [[contra-gentiles-libro-primo]] (c-000059, Libro I ch.13 — Aristotle's two proofs of God's existence from motion, at far greater length than the Summa's compressed First Way, including objection-handling absent from the Summa entirely), [[contra-gentiles-libro-secondo]] (c-000060, Libro II ch.56-59, 79 — soul as substantial form refuting Plato's "pilot in a ship" model, an extended anti-Averroist polemic against a single shared intellect for all humans, and the soul's immortality)
- Pages updated: [[somma-contro-i-gentili-struttura]] (batches logged, OCR-quality note added), [[Le Cinque Vie]] (compared against the Contra Gentiles' fuller philosophical argument), [[god-philosophy-universities]] (primary-text location found for the Averroist threat ch.9 alludes to but doesn't quote), [[Angeli e Anima Umana (Sintesi Tomistica)]] (primary-text verification of soul-as-form doctrine and its rival theories)
- Key insight: the Contra Gentiles' anti-Averroist chapter (II.59, part of a ~20-chapter polemic) gives this vault its first primary-text location for why Aquinas thinks personal identity is at stake in the soul/body question — on Averroes's view, "I" would never actually think at all, only be known by a separate cosmic intellect using my phantasms as raw material. [[god-philosophy-universities]] ch.9 discusses the personal-identity stakes but never quotes this passage directly.

---

## 2026-07-26 | batch ingest | Somma Teologica, 4 treatise-level deep-ingests (planned batches 1-4)

- Source: `.raw/S. Tommaso d'Aquino - Somma Teologica.pdf` (5,318 pp.), following the paced ingestion plan agreed 2026-07-25 (see memory `ingestion-schedule-four-texts`)
- Method: extracted the entire PDF to plain text once (`pdftotext -enc UTF-8`, ~17MB, 5,319 pages split on form-feed), then used a Python script to regex-locate every question's `ARGOMENTO N` header, building an exact page-index per Part far cheaper than binary-searching page ranges one question at a time. **Trap found and documented**: question numbers reset at each Part (I, I-II, II-II, III), so e.g. Prima Pars qq.90-108 and Prima Secundae qq.90-108 are entirely different treatises sharing the same numbers — cost real time in Batch 3 before being caught and written up.
- Pages created: [[somma-teologica-de-deo-uno]] (c-000055, I qq.2-26 — five ways, essence/esse, analogy, providence/predestination, omnipotence), [[somma-teologica-trinita]] (c-000056, I qq.27-43 — processions, relations, persons, notional acts), [[somma-teologica-trattato-legge]] (c-000057, I-II qq.90-108 — eternal/natural/human law, natural-inclinations hierarchy, Old/New Law), [[somma-teologica-sacramenti]] (c-000058, III qq.60-83 — sacraments as instrumental causes of grace, transubstantiation)
- Pages updated: [[somma-teologica-struttura]] (all four batches logged in its follow-up section), [[Le Cinque Vie]] and [[Il Cardine della Metafisica Tomista]] (primary-text verification of the five ways and essence/esse), [[La Santissima Trinità (Sintesi Tomistica)]] (primary-text verification of processions/person-definition/circularity resolution), [[god-philosophy-universities]] (primary-text verification of natural law's three-tier inclinations), [[I Sacramenti nella Sintesi Tomistica]] (primary-text verification of instrumental causality and transubstantiation)
- Key insight: every doctrine this vault previously held only via Garrigou-Lagrange's secondary synthesis in [[la-sintesi-tomistica]] now has a primary-text citation directly from the Summa itself, with no divergence found anywhere checked. Also discovered this PDF is a parallel Latin-Italian edition (each question opens with the original Latin prooemium).
- Still open: Tertia Pars qq.1-59 (the Incarnation itself, not yet deep-ingested from primary text), qq.84-90 (Penance, where Aquinas's own writing breaks off), and numerous structurally-confirmed-but-unread questions within each of the four batches (see each page's "What remains unread" section).

---

## 2026-07-25 | deep-dive | La Sintesi Tomistica Parti II-VII (same-day follow-up)

- Source: `.raw/R. Garrigou-Lagrange - La Sintesi Tomistica.epub` (previously only Intro + Parte I + Parte VIII cap. I read; user requested "deep-dive la-sintesi-tomistica parti II-VII")
- Summary: read all of Parte Seconda through Parte Settima in full (De Deo Uno; SS. Trinità; Angeli e Uomo; Incarnazione; Sacramenti; Teologia Morale) from a pandoc-converted plaintext (29,132 lines) processed sequentially in chunks. Only Parte Ottava chs. II, III, V remain unread.
- Pages created: [[Le Cinque Vie]] (c-000044), [[Grazia Efficace e Premozione Fisica]] (c-000045), [[La Santissima Trinità (Sintesi Tomistica)]] (c-000047), [[Angeli e Anima Umana (Sintesi Tomistica)]] (c-000048), [[Incarnazione, Unione Ipostatica e Mariologia]] (c-000049), [[I Sacramenti nella Sintesi Tomistica]] (c-000050), [[Teologia Morale nella Sintesi Tomistica]] (c-000051)
- Pages updated: [[la-sintesi-tomistica]] (marked Parti II-VII read, scope note rewritten), [[Gerarchia degli Esseri e Analogia]] (added Garrigou-Lagrange's *formaliter eminenter* parallel to Gilson's analogy account), [[Persona (Tomismo)]] (resolved the ontological-personality gap via Cajetan's formula, now covered in the Incarnation page), [[Il Cardine della Metafisica Tomista]] (added confirmation section: essence/esse recurs as the root of the Trinity's, Christ's, and angelology's disputes too, not just the opening metaphysics)
- Key insight: Garrigou-Lagrange's "one root principle" claim about his own book holds up with unusual consistency once the whole text is read — the Trinity's *unum esse*, Christ's *unum esse*, and obediential potency across angelology/grace/Mariology are all explicitly traced back to the same essence/esse distinction, with Suárez's denial of it as the recurring point of departure for his rival positions on all of them.
- Note: address `c-000046` was allocated (anticipating a 3rd concept page at that point in the session) but never used — a harmless planning miscount, not corruption. Next free address is c-000052.

---

## 2026-07-25 | batch ingest | 13 Thomism sources (.raw/ Aquinas + secondary literature)

- Source: `.raw/R. Garrigou-Lagrange - Essenza e attualità del Tomismo.epub`
- Summary: [[essenza-e-attualita-del-tomismo]] (full read)
- Pages created: [[Réginald Garrigou-Lagrange]], [[San Tommaso d'Aquino]], [[Tomismo]], [[Dottrina di Atto e Potenza]], [[XXIV Tesi Tomiste]]
- Key insight: Act/potency real distinction is Garrigou-Lagrange's proposed keystone of Thomism; Suárez is the recurring polemical target.

- Source: `.raw/R. Garrigou-Lagrange - La Sintesi Tomistica.epub`
- Summary: [[la-sintesi-tomistica]] (Intro + Parte I + Parte VIII cap. I read in full of 8 parts; ~245k words total)
- Pages updated: [[Dottrina di Atto e Potenza]], [[XXIV Tesi Tomiste]] (corrected 1914 vs 1925 origin date), [[Réginald Garrigou-Lagrange]]
- Key insight: The XXIV Tesi were approved 1914 by Pius X motu proprio, not 1925 (1925 = Garrigou-Lagrange's Rome Congress paper).

- Source: `.raw/A. MacIntyre - Dopo la Virtù.pdf`
- Summary: [[dopo-la-virtu]] (prefaces + ch.14 read in full of 19 chapters)
- Pages created: [[Alasdair MacIntyre]], [[Pratica e Beni Interni]], [[Unità Narrativa della Vita e Tradizione]]
- Key insight: MacIntyre's 2006 preface explains his post-1981 turn to Thomism via three specific points (metaphysics of the good, biological grounding, misericordia).

- Source: `.raw/A. MacIntyre - God, Philosophy, Universities.pdf`
- Summary: [[god-philosophy-universities]] (chs. 9-11 read in full of 19 chapters)
- Pages updated: [[San Tommaso d'Aquino]], [[Alasdair MacIntyre]]
- Key insight: MacIntyre's independent English-language framing of essence/esse lands closest to Garrigou-Lagrange's, not Gilson's or Mondin's — see [[Il Cardine della Metafisica Tomista]].

- Source: `.raw/B. Mondin - Dizionario Enciclopedico del Pensiero di S.Tommaso d'Aquino.pdf`
- Summary: [[mondin-dizionario-tommaso]] (3 of 39 entries read: Accidente, Essenza, Persona)
- Pages created: [[Battista Mondin]], [[Persona (Tomismo)]]
- Pages updated: [[Dottrina di Atto e Potenza]]
- Key insight: Mondin proposes "esse conceived intensively," not the real essence/esse distinction itself, as Thomism's true keystone — disagreeing explicitly with Gilson/Maritain/Fabro.

- Source: `.raw/E. Gilson - Le Thomisme. Introduction au Système de Saint Thomas D'aquin.pdf`
- Summary: [[le-thomisme-gilson]] (chs. I and XV read in full of 15 chapters)
- Pages created: [[Étienne Gilson]], [[Gerarchia degli Esseri e Analogia]]
- Key insight: Gilson explicitly refutes reading Aquinas's hierarchy of being as Neo-Platonic — "the world is an ordered discontinuity," not Plotinian emanation.

- Source: `.raw/S. Tommaso d'Aquino - Opuscoli.pdf`
- Summary: [[opuscoli-tommaso]] (historical intro + Credo's introduction read)
- Key insight: Rare pastoral/vernacular-register Aquinas primary text — his last Lenten preaching cycle, Naples 1273.

- Source: `.raw/S. Tommaso d'Aquino - Principi non Negoziabili sulla Società e sulla Politica.epub`
- Summary: [[principi-non-negoziabili-de-regimine]] (Book I chs. 1-4 read of 76 total chapters)
- Key insight: Modern retitling of the authentic *De regimine principum*; only Bk. I + Bk. II chs.1-4 are genuinely Aquinas's (rest by Ptolemy of Lucca).

- Source: `.raw/S. Tommaso d'Aquino - Sul Male.pdf`
- Summary: [[sul-male-de-malo]] (Qq. 1-6 of 16 read via analytic summary; ~300k words total)
- Pages created: [[Il Male come Privazione]]
- Key insight: Evil as privation (*privatio boni*) directly extends the potency/act framework to ethics.

- Source: `.raw/S. Tommaso d'Aquino - Somma Teologica.pdf`, `.raw/S. Tommaso d'Aquino. - Somma contro i Gentili [ocr] [1975].pdf`, `.raw/S. Tommaso d'Aquino - Sulla Verità.pdf`, `.raw/Dizionario Interdisciplinare di Scienza e Fede (NP).pdf`
- Summary: [[somma-teologica-struttura]], [[somma-contro-i-gentili-struttura]], [[sulla-verita-de-veritate]], [[dizionario-interdisciplinare-scienza-fede]] — structural/bibliographic entries only (5,318pp / 1,374pp / 1,152pp image-scan / 2,339pp image-scan respectively)
- Key insight: The latter two files have **no OCR text layer and one exceeds the 100MB image-viewing limit** — genuinely unreadable with current tools, not merely deferred.

- Cross-reference pass: created [[Il Cardine della Metafisica Tomista]] comparing Garrigou-Lagrange's, Gilson's, and Mondin's rival "keystone" framings of Thomistic metaphysics.
- Updated: [[index]], [[hot]], [[Wiki/sources/_index]], [[Wiki/entities/_index]], [[Wiki/concepts/_index]]. Created `.raw/.manifest.json` (first use this session). Patched `scripts/allocate-address.sh` to skip `flock` when unavailable (Windows Git Bash has no `flock` binary) — falls back to unlocked single-writer mode.
