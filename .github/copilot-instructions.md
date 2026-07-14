# Copilot Instructions for yschoi-marketplace

## What this repo is

A **Claude Code plugin marketplace**, not a traditional application. There is no
build, lint, or test pipeline. The real "product" is the `frontend-slides`
skill, which Claude Code uses to generate self-contained HTML slide decks (not
code that runs in this repo).

Install/distribution flow: user runs `/plugin marketplace add nyschoi/yschoi-marketplace`,
then `/plugin install presentation-maker@youngsoochoi-marketplace`, restarts
Claude Code, and the skill appears under `/skills` as
`presentation-maker:frontend-slides`.

## Identity layers (do not confuse these)

Three names live at three different layers. If you rename one, you must keep
the others consistent:

| Name | Defined in | Purpose |
| --- | --- | --- |
| `youngsoochoi-marketplace` | `.claude-plugin/marketplace.json` (`name`) | Marketplace id (the `@suffix` in install command) |
| `presentation-maker` | `plugins/.claude-plugin/plugin.json` (`name`) + `marketplace.json` `plugins[].name` | Plugin id (install target) |
| `frontend-slides` | `plugins/skills/frontend-slides/SKILL.md` frontmatter `name` | Skill id (`/presentation-maker:frontend-slides`) |
| `nyschoi/yschoi-marketplace` | git remote / GitHub path | Argument to `marketplace add` |

`marketplace.json`'s `plugins[].source` points at `./plugins` — if the plugin
directory ever moves, update that field too.

## Architecture: the frontend-slides skill

Located at `plugins/skills/frontend-slides/`. It's a fork/customization of
[zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides).

`SKILL.md` orchestrates a **phase-based workflow** and lazy-loads supporting
files only when needed — do not read every file up front:

- Phase 0: mode detection
- Phase 1: content
- Phase 2: style selection → reads `STYLE_PRESETS.md` (12 presets) and
  `bold-template-pack/selection-index.json` (compact metadata) → then only the
  shortlisted templates' `preview.md` (lightweight cards)
- Phase 3: generation → reads the **one** selected template's full
  `design.md`, plus `viewport-base.css`, `html-template.md`,
  `animation-patterns.md`
- Phase 4: PPTX conversion → `scripts/extract-pptx.py`
- Phase 5: delivery
- Phase 6: sharing/export → `scripts/deploy.sh`, `scripts/export-pdf.sh`

The "Supporting Files" table at the bottom of `SKILL.md` is the single source
of truth for which file is read in which phase — check it before adding or
touching reference files.

`bold-template-pack/` contains many design-system templates (each with a
`design.md` + lightweight `preview.md`). **Never bulk-read every
`design.md`** — use `selection-index.json` to shortlist candidates by
`mood`/`tone`/`best_for`/`avoid_for`/`formality`/`density`/`scheme`, then load
`preview.md` for shortlisted candidates, then the full `design.md` only for
the one the user picks.

## Invariants the skill enforces (do not violate when editing skill docs)

- **Fixed 16:9 stage**: every deck is authored at 1920×1080 and scaled as a
  whole to the viewport via a wrapper. No responsive reflow, even on mobile.
  Slide visibility toggles via `.active`/`.visible` classes
  (`visibility`/`opacity`/`pointer-events`), never `display: none/block` for
  slide switching.
- **No system-font fallback**: fonts come from the chosen preset/template only.

### `canvas` template (this repo's custom addition)

`bold-template-pack/templates/canvas/design.md` is the single source of truth.
Company-standard policy:

- **Exactly 2 fonts**: Pretendard (Korean/English body & headline) + JetBrains
  Mono (eyebrow/caption/page numbers). No third font, no `system-ui` fallback
  — a font failing to load is a bug to fix by embedding, not something to
  paper over with a generic fallback.
- **Offline-embedded fonts**: fonts from `reference/fonts/` are embedded via
  `@font-face { src: url(data:font/...;base64,...) }` directly in `<style>`.
- **16px floor**: no text under 16px anywhere in the deck (including ad-hoc
  labels, badges, captions, footnotes). Fix via layout, not smaller text.
- **Video is native `<video>`**: no poster-image substitution. Video files are
  referenced by relative path (`src="demo.mp4"`) next to the HTML, not
  base64-inlined. `showSlide()` must `.pause()` `<video>` elements on inactive
  slides.
- **Custom cursor**: magenta dot (white on navy slides), `position: fixed` so
  it tracks across letterbox margins. Touch/coarse pointers keep the native
  cursor. Do not use `mix-blend-mode: difference`.

## Scripts (`plugins/skills/frontend-slides/scripts/`)

```bash
# HTML deck -> PDF (spins up a local server, captures each slide at 1920x1080 via Playwright, merges)
bash scripts/export-pdf.sh <path-to-html> [output.pdf] [--compact]

# Deck -> public Vercel URL (guides Vercel CLI install/login if missing)
bash scripts/deploy.sh <path-to-slide-folder-or-html>

# Existing PPTX -> JSON+images extraction (input for conversion workflow); requires `pip install python-pptx`
python scripts/extract-pptx.py <input.pptx> [output_dir]
```

## MCP servers

Defined in `.mcp.json`: `atlassian-ktspace`, `atlassian-ktdevspace` (Confluence/Jira
reading), `playwright` (PDF export / slide screenshots). Must be enabled in
Claude Code to work.

## What not to commit

`.gitignore` excludes `inbox/` (source materials for decks), `output/`
(generated decks), `.claude/settings.local.json`, `.claude/skills/` (local
symlink), `.DS_Store`. These are workspace artifacts, not marketplace content
— don't add them back or treat their absence as a bug.
