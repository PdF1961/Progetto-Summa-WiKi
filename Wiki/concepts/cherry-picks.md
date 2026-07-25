---
type: concept
title: "cherry-picks"
created: 2026-04-08
updated: 2026-07-25
tags:
  - ecosystem
  - competitive-analysis
  - claude-obsidian
  - roadmap
status: developing
complexity: intermediate
domain: "claude-obsidian plugin roadmap"
related:
  - "[[claude-obsidian-ecosystem]]"
  - "[[claude-obsidian-ecosystem-research]]"
  - "[[Ar9av-obsidian-wiki]]"
  - "[[ballred-obsidian-claude-pkm]]"
  - "[[kepano-obsidian-skills]]"
  - "[[rvk7895-llm-knowledge-bases]]"
  - "[[Nexus-claudesidian-mcp]]"
sources:
  - "[[claude-obsidian-ecosystem-research]]"
---

# cherry-picks

Prioritized feature backlog for `claude-obsidian`, distilled from the 2026-04-08 ecosystem sweep of 16+ Claude+Obsidian projects (see [[claude-obsidian-ecosystem]] for the full feature matrix and [[claude-obsidian-ecosystem-research]] for the raw research). Each item names the source project it was cherry-picked from, what that project does well, and an implementation note for adapting it into `claude-obsidian`.

Ordered roughly by impact (see "Top 5 gaps by impact" in [[claude-obsidian-ecosystem]]), not by project.

---

## 1. URL Ingestion in /wiki-ingest

**From**: [[kepano-obsidian-skills]] (`defuddle`), also present in `llm-wiki` and `obsidian-wiki`.
**Gap**: `claude-obsidian`'s `/wiki-ingest` only reads local files — no URL support, forcing manual copy-paste from the web.
**Implementation note**: Pair with the `defuddle` skill (item 3) so `/wiki-ingest <url>` fetches, cleans, and ingests in one step. Highest-impact single gap identified in the research.

## 2. Auto-Commit PostToolUse Hook

**From**: [[ballred-obsidian-claude-pkm]] — best-in-class implementation in the ecosystem.
**What it does**: Every `Write`/`Edit` tool call triggers `git add -A && git commit` automatically, so the vault is always versioned without the user remembering to commit.
**Implementation note**: Add as an opt-in PostToolUse hook, scoped to the vault directory only. Needs a guard against committing secrets accidentally staged alongside legitimate wiki edits.

## 3. defuddle Web Cleaning Skill

**From**: [[kepano-obsidian-skills]] — wraps `defuddle-cli`.
**What it does**: Strips ads, navigation, and footers from web pages before ingest; reduces token usage ~40-60% on typical pages and produces cleaner Markdown.
**Implementation note**: Direct cherry-pick — install as its own skill, invoked automatically whenever `/wiki-ingest` is given a URL (see item 1).

## 4. Delta Tracking Manifest

**From**: [[Ar9av-obsidian-wiki]] — best-in-class implementation in the ecosystem.
**What it does**: `.manifest.json` tracks every ingested source (path, hash, timestamp, which wiki pages it produced) so re-ingesting only processes new or changed files instead of reprocessing everything.
**Implementation note**: **Already adopted** — `.raw/.manifest.json` was added to this vault during the 2026-07-25 Thomism batch ingest, extended with a DragonScale `address_map`. See [[la-sintesi-tomistica]] for a manifest entry in active use.

## 5. Multi-Depth Query Modes

**From**: [[rvk7895-llm-knowledge-bases]] — best-in-class implementation in the ecosystem (3 tiers: quick / standard / deep).
**What it does**: Lets a query choose its own cost — quick answers from indexes/summaries only, standard cross-references the full wiki plus web search, deep runs a multi-agent parallel research pipeline.
**Implementation note**: `/wiki-query` currently has one mode. Adding a depth flag would let cheap questions stay cheap while still supporting deep research when asked.

## 6. /wiki-ingest Vision Support

**From**: [[Ar9av-obsidian-wiki]] — best-in-class implementation in the ecosystem.
**What it does**: Ingests images, screenshots, and whiteboard photos with a vision-capable model; each resulting page gets a 1-2 sentence `summary:` frontmatter field for preview without opening the file.
**Implementation note**: `claude-obsidian` can already read images via its Read tool in-session, but there's no dedicated ingest path or the `summary:` frontmatter convention. Worth adding to the frontmatter schema (see `skills/wiki/references/frontmatter.md`).

## 7. /adopt — Import Existing Vault

**From**: [[ballred-obsidian-claude-pkm]] — best-in-class implementation in the ecosystem.
**What it does**: Scans an existing Obsidian vault, detects its organization method (PARA, Zettelkasten, LYT, plain folders), and interactively maps folders to the target system's layers — non-destructively.
**Implementation note**: Would lower the adoption barrier for users with an existing vault who don't want to restart from an empty `wiki/` folder.

## 8. Productivity Wrapper (Daily/Weekly Reviews)

**From**: [[ballred-obsidian-claude-pkm]] — best-in-class implementation in the ecosystem.
**What it does**: A goal cascade (3-year vision → yearly goals → projects → monthly goals → weekly review → daily tasks) with a dedicated skill per layer, plus a "productivity coach" output style.
**Implementation note**: Out of scope for `claude-obsidian`'s core knowledge-base mission, but the `wiki/goals/`, `wiki/journal/`, and `wiki/lessons/` stub sections already in this vault's index suggest a lighter-weight version (review prompts, not a full goal-cascade system) could fit.

## 9. Multi-Agent Compatibility (Cursor, Windsurf, Codex)

**From**: [[Ar9av-obsidian-wiki]] — best-in-class implementation in the ecosystem (`setup.sh` deploys skills to 7 agents at once: Claude Code, Cursor, Windsurf, Codex, Gemini/Antigravity, OpenClaw, GitHub Copilot). [[kepano-obsidian-skills]] independently validates the same direction — the Agent Skills format it uses is already multi-platform (Claude Code, Codex CLI, OpenCode) with no changes needed.
**What it does**: One bootstrap script/format instead of a Claude-Code-only install, so the same skill set works across agents.
**Implementation note**: Since `claude-obsidian`'s skills are already plain Markdown+YAML (the Agent Skills format kepano validates), the main missing piece is per-agent bootstrap files (`.cursor/rules/`, `.windsurf/rules/`, `AGENTS.md`, etc.) rather than a skill rewrite.

## 10. Marp Presentation Output

**From**: [[rvk7895-llm-knowledge-bases]] — best-in-class implementation in the ecosystem.
**What it does**: Generates Marp slide decks (and matplotlib charts) as an output format alongside Markdown, filed back into the wiki or saved to `output/`.
**Implementation note**: Would extend `/wiki-query` or `/save` with a "presentation" output mode for sharing synthesis outside Obsidian.

## 11. obsidian-memory-mcp Integration

**From**: the `obsidian-memory-mcp` MCP server (see the MCP Servers table in [[claude-obsidian-ecosystem]] — "AI memories as Markdown in graph view"); [[Nexus-claudesidian-mcp]]'s workspace memory (persistent JSONL context across sessions, auto-included in Obsidian Sync) is a different implementation of the same underlying concept.
**What it does**: Represents an AI agent's accumulated memory as first-class Markdown notes that show up in Obsidian's graph view, rather than as an opaque cache file.
**Implementation note**: `claude-obsidian` already has `wiki/hot.md` as a lightweight session-memory mechanism; this item is about whether richer, structured memory (e.g. per-entity or per-topic memory notes) should also be graph-visible rather than living only in `hot.md`'s prose summary.

## 12. obsidian-bases Skill (from kepano)

**From**: [[kepano-obsidian-skills]] — official skill from the Obsidian creator.
**What it does**: Teaches Claude to build and query Obsidian Bases (`.base` files: views, filters, formulas, summaries) — a core Obsidian feature (shipped v1.9.10) that no other AI project in the ecosystem sweep supported yet.
**Implementation note**: **Partially adopted** — `wiki/meta/dashboard.md` already embeds a `dashboard.base` file using this pattern (currently a placeholder; see the 2026-07-25 lint report's remaining open items). Installing the `obsidian-bases` skill itself (not just hand-writing one `.base` file) would let Claude generate and edit Bases views generally, not just the one dashboard.

## 13. Schema-Emergent Vault Mode

**From**: [[Ar9av-obsidian-wiki]]'s 4-stage pipeline (Ingest → Extract → Resolve → Schema), where vault structure emerges from what sources actually contain rather than being predefined up front.
**What it does**: Instead of fixing folder/type categories in advance, the wiki's schema (what page types and sections exist) grows organically as sources are ingested and patterns repeat.
**Implementation note**: `claude-obsidian`'s current schema (`wiki/sources|entities|concepts|comparisons/`) is predefined and has worked fine for both the demo ecosystem-research domain and the Thomism domain so far. This item is a "watch for it" rather than an active gap: if a future domain doesn't fit the four existing types well, this is the alternative model to reach for instead of forcing a mismatched type.

---

## See also

- [[claude-obsidian-ecosystem]] — the feature matrix these items were drawn from
- [[claude-obsidian-ecosystem-research]] — the raw research session
- [[Wiki Map]] — visual map including this page
