---
version: alpha
name: Canvas
description: "A confident monochrome editorial deck interrupted by oversized hand-cut pastel color-block slides. The system core is rigorously black-and-white — Pretendard variable sans, pure white canvas, pure black ink, pill-shaped tags — while every section beat drops the whole slide into a saturated lime, lavender, cream, mint, pink, or deep navy panel that reads like a giant sticky note placed on a clean desk. Weight, not color, carries hierarchy on body copy; a condensed mono runs every eyebrow, kicker, and page number. Korean-first: Pretendard sets both Latin and Hangul as one voice. The result feels technical and joyful at once — a serious tool made by people who like color."

colors:
  ink: "#000000"
  canvas: "#ffffff"
  inverse-canvas: "#000000"
  inverse-ink: "#ffffff"
  surface-soft: "#f7f7f5"
  hairline: "#e6e6e6"
  hairline-soft: "#f1f1f1"
  block-lime: "#dceeb1"
  block-lilac: "#c5b0f4"
  block-cream: "#f4ecd6"
  block-pink: "#efd4d4"
  block-mint: "#c8e6cd"
  block-coral: "#f3c9b6"
  block-navy: "#1f1d3d"
  on-block: "#000000"
  on-navy: "#ffffff"
  accent-magenta: "#ff3d8b"
  semantic-success: "#1ea64a"

typography:
  display:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 150px
    fontWeight: 300
    lineHeight: 1.0
    letterSpacing: -3px
  h1:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 104px
    fontWeight: 300
    lineHeight: 1.05
    letterSpacing: -2px
  headline:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 60px
    fontWeight: 600
    lineHeight: 1.15
    letterSpacing: -1px
  subhead:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 44px
    fontWeight: 300
    lineHeight: 1.3
    letterSpacing: -0.5px
  card-title:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 34px
    fontWeight: 700
    lineHeight: 1.3
    letterSpacing: -0.3px
  body-lg:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 32px
    fontWeight: 400
    lineHeight: 1.4
    letterSpacing: -0.2px
  body:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 26px
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: -0.2px
  body-sm:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 22px
    fontWeight: 400
    lineHeight: 1.45
    letterSpacing: -0.1px
  button:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 26px
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: -0.1px
  stat-value:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 220px
    fontWeight: 300
    lineHeight: 0.9
    letterSpacing: -6px
  quote-text:
    fontFamily: "Pretendard Variable, Pretendard, system-ui, sans-serif"
    fontSize: 76px
    fontWeight: 300
    lineHeight: 1.2
    letterSpacing: -1.5px
  eyebrow:
    fontFamily: "JetBrains Mono, ui-monospace, monospace"
    fontSize: 24px
    fontWeight: 500
    lineHeight: 1.3
    letterSpacing: 1.6px
    textTransform: uppercase
  caption:
    fontFamily: "JetBrains Mono, ui-monospace, monospace"
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.2
    letterSpacing: 1.2px
    textTransform: uppercase

rounded:
  xs: 3px
  sm: 10px
  md: 14px
  lg: 40px
  xl: 56px
  pill: 999px
  full: 9999px

spacing:
  slide-pad-x: 140px
  slide-pad-y: 100px
  block-pad: 96px
  gap-lg: 64px
  gap-md: 36px
  gap-sm: 18px
  hair: 2px

canvas:
  width: 1920px
  height: 1080px

components:
  eyebrow-label:
    color: "{colors.ink}"
    typography: "{typography.eyebrow}"
    description: "Mono uppercase kicker in black, sits above a headline with generous tracking. Flags taxonomy without competing with display type."
  pill-tag:
    border: "2px solid {colors.ink}"
    color: "{colors.ink}"
    padding: "10px 26px"
    rounded: "{rounded.pill}"
    typography: "{typography.button}"
    description: "Outlined black pill enclosing a short label. The only tag shape in the system; never square."
  pill-solid:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.inverse-ink}"
    rounded: "{rounded.pill}"
    padding: "16px 34px"
    typography: "{typography.button}"
    description: "Solid black CTA pill used on closing / call-to-action slides. Inverts to white pill on navy surfaces."
  color-block-slide:
    backgroundColor: "{colors.block-lime}"
    textColor: "{colors.on-block}"
    padding: "{spacing.slide-pad-x}"
    description: "A whole slide dropped into one saturated pastel ground (lime, lilac, cream, mint, pink, coral). The signature surface — a giant sticky note. No rounded corners at slide scale (full bleed); the 40px radius returns only when a block sits inside a white slide as a card."
  color-block-navy:
    backgroundColor: "{colors.block-navy}"
    textColor: "{colors.on-navy}"
    padding: "{spacing.slide-pad-x}"
    description: "Deep indigo full-slide ground — the only dark surface in the system besides pure-black closing slides. Used for weighty section breaks and closings."
  inset-block-card:
    backgroundColor: "{colors.block-lilac}"
    textColor: "{colors.on-block}"
    rounded: "{rounded.lg}"
    padding: "{spacing.block-pad}"
    description: "A pastel block used as a card INSIDE a white canvas slide (rather than as the whole slide). This is the only place the {rounded.lg} 40px radius appears."
  stat-numeral:
    color: "{colors.ink}"
    typography: "{typography.stat-value}"
    description: "Oversized black numeral. Hierarchy comes from scale + weight, never from color — stats are ink-black on white, or on-block-black on pastel, or white on navy."
  hairline-divider:
    height: "{spacing.hair}"
    background: "{colors.hairline}"
    description: "2px hairline rule separating regions on white canvas. On pastel surfaces, use a darker mix of the block color instead."
  chrome-footer:
    color: "#ffffff"
    blendMode: "difference"
    typography: "{typography.caption}"
    position: "position: absolute inside #deckStage (a DOM sibling of the .slide sections, appended after them), authored directly in stage-pixel coordinates — e.g. bottom: 34px, left: 60px for the label and bottom: 34px, right: 60px for the counter. Carried along for free by the stage's own transform; never position: fixed, never recomputed in JS on resize."
    description: "Bottom chrome row: mono deck label bottom-left, mono page counter bottom-right (e.g. '03 / 12', JS-updates its text content on every showSlide() call so it can never drift or go missing). Always visible on every slide, including cover, chapter, statement, quote, and closing — it does not compete with a slide's poster-like emptiness because it renders on top, not because it lives outside the stage. Uses mix-blend-mode: difference so it self-adapts to any surface without per-surface color rules (see Presentation Chrome for the exact DOM-nesting requirement this depends on)."
  magenta-promo:
    backgroundColor: "{colors.accent-magenta}"
    textColor: "{colors.inverse-ink}"
    rounded: "{rounded.pill}"
    padding: "12px 28px"
    typography: "{typography.button}"
    description: "Single-shot saturated pink pill. At most one per deck, reserved for the one moment that must pop against an already-colored panel. Not a section color."
  shot-frame:
    backgroundColor: "{colors.surface-soft}"
    border: "2px solid {colors.hairline}"
    rounded: "{rounded.md}"
    padding: "18px"
    description: "The frame for a single piece of visual evidence — a screenshot, diagram, or embedded video — inside a white content slide. One `shot-frame` per image/video; group 2-4 side by side in a `.shot-row` grid with a mono `caption` label centered beneath each. This is Canvas's only image/video container; do not invent a second framing style."
  video-evidence:
    element: "real <video> tag, not a poster-image + play-icon substitute"
    attributes: "controls preload=\"metadata\" playsinline muted"
    src: "relative file path alongside the deck HTML (e.g. src=\"demo.mp4\"), never a base64 data URI"
    badge: "a small solid-magenta pill (`.video-badge`, `{colors.accent-magenta}` background, white text, `{typography.caption}`, reading '동영상' or 'VIDEO') pinned to the top-left corner of the shot-frame — this is one of the deck's permitted single-shot magenta accents, independent of the in-slide `magenta-promo` pill budget, since it is functional labeling rather than a CTA"
    playbackControl: "JS pauses any `<video>` on a slide that is not the current slide (on every `showSlide()` call, iterate slides and call `.pause()` on non-active slides' videos) so audio/playback never continues in the background after navigating away"
    description: "Canvas embeds video natively with a real HTML5 `<video>` element inside a `shot-frame.has-video`, sized and framed exactly like a screenshot — never as a poster-frame image standing in for the video. Keep the video file as a sibling file next to the deck HTML and reference it with a relative `src`; do not inline it as base64 (this bloats the single-file deck by the video's full size for no benefit, since the file must ship alongside the HTML for offline use regardless — unlike fonts/images, base64 buys nothing here). `muted` is required for autoplay-safety even though this template does not autoplay video; `playsinline` prevents iOS from forcing fullscreen; `preload=\"metadata\"` keeps initial load light. Never fabricate a click-to-play static-image mockup when a real video file is available — always embed the actual `<video>` element."
  dot-nav:
    background: "#ffffff"
    blendMode: "difference"
    activeBackground: "{colors.accent-magenta}"
    activeBlendMode: "normal"
    activeGlow: "0 0 0 4px rgba(255,61,139,0.18)"
    dotSize: "8px (10px active); 24px click target (8px visible dot + 8px padding, content-box)"
    position: "position: absolute inside #deckStage (right: 40px), each dot's top set once in stage-pixel coordinates so the column is vertically centered across the 1080px stage height — carried along for free by the stage's own transform; never position: fixed, never recomputed in JS on resize"
    description: "One dot per slide, stacked vertically near the stage's right edge, sitting on top of the actual slide content. The active slide's dot is always solid {colors.accent-magenta} (mix-blend-mode: normal — never inverted, so it reads as the deck's one interactive signal color regardless of surface). Inactive dots are white with mix-blend-mode: difference, so they self-adapt to whatever surface sits directly beneath them (dark on white/pastel, light on navy/black) without any per-surface color rule. Clicking a dot jumps to that slide."
    implementationNote: "mix-blend-mode only blends against the true slide content when the blended element sits exactly one level below the stage root in the render tree. The wrapping nav element must use `display: contents` (removing its own box entirely) so each dot button becomes a direct rendering child of the stage; each button is independently `position: absolute` with its own `mix-blend-mode`. ANY intermediate positioned wrapper — including a plain flex-centering div, or drawing the dot on a button's `::before` pseudo-element instead of the button's own background — silently isolates the blend to that local box, so the 'white' dot renders as flat opaque white and becomes invisible on white canvas. This has been verified empirically; do not reintroduce a wrapper div or pseudo-element for the dot mark."
  cursor-ring:
    fill: "solid {colors.accent-magenta} (border + interior) at rest on light/pastel slides; solid #ffffff (border + interior) at rest on {colors.block-navy}"
    blendMode: "none — explicit per-slide branching, not mix-blend-mode (see below)"
    size: "20px default, 36px on hover (2/3 scale of the original 30px/54px ring)"
    hoverFill: "{colors.accent-magenta} (solid, on any surface)"
    description: "Replaces the system pointer with a small solid dot that tracks the mouse — not a hollow outline ring. Unlike dot-nav and chrome-footer, it does NOT use mix-blend-mode: difference — on a white/pastel canvas that blend mode inverts a white ring to solid black, which reads as a harsh, un-brand-like dot rather than a deliberate pointer. Instead, JS toggles an `on-dark` class on the cursor whenever the active slide carries `{colors.block-navy}` (Canvas's only dark surface): resting fill is solid {colors.accent-magenta} on every light/pastel slide, and solid white on navy/closing slides — a bright, legible color that reads clearly against the dark ground without competing with magenta's role as the deck's signal color. Hovering any pill, dot, or editable element enlarges the dot from 20px to 36px and (on navy slides) switches its fill to {colors.accent-magenta} — on light slides the color stays magenta throughout, so hover reads as a pure size-growth cue; on navy it is also a color change from white to magenta, doubling as the interactive cue. Pointer-fine input only — hidden on touch, and swapped for the native cursor while inline-editing text."
    implementation: "A single `position: fixed` div (e.g. `#cursorRing`), z-index above all slide content, `pointer-events: none`, positioned every `mousemove` via `style.left/top = e.clientX/clientY` with `transform: translate(-50%, -50%)` fixed in CSS to center the dot on the cursor point — track raw viewport coordinates, not stage-relative ones, so the ring still follows the mouse into the letterboxed margin. Hide the real system cursor with `cursor: none` on `body`, scoped inside `@media (hover: hover) and (pointer: fine)` so touch/coarse-pointer devices keep their native cursor untouched; the ring element itself is also hidden via `@media (hover: none), (pointer: coarse)`. Hover state is driven by a single delegated `mouseover`/`mouseout` pair on `document` checking `e.target.closest('.pill-tag, .pill-solid, .dot-nav button, [contenteditable=\"true\"]')` rather than per-element listeners. While inline-edit mode is active (`body.editing`), hide the ring and let the native cursor return so users can place a text caret normally."
---

## Frontend Slides Fixed-Stage Policy

When this design system is used by the `frontend-slides` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

All measurements in this document are authored directly at 1920×1080 stage coordinates in pixels — use them as-is inside the fixed stage. This policy has higher priority than any responsive breakpoint behavior inherited from the source website system that inspired this template. The source was a scrolling marketing site; this template is a slide deck. Treat the source's "scrolling color-block sections" as the direct ancestor of this template's "full-bleed pastel color-block slides."

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Fonts & Loading

**Canvas uses exactly two font families, always: Pretendard and JetBrains Mono. No third family, and no substitute for either, is ever acceptable.** Pretendard sets every Latin and Hangul character as a single variable voice (display, headline, body, card-title, eyebrow labels set in Korean, stat numerals); JetBrains Mono handles only mono eyebrows, captions, and page numbers (Latin/numeral taxonomy labels — keep mono labels in Latin/numerals, not Hangul). Do not fall back to `system-ui`, `ui-monospace`, or any other stack as a silent substitute — if a font fails to load, that is a bug to fix (embed it), not a gap to shrug off with a generic fallback. Do not reuse Pretendard-at-some-weight to stand in for JetBrains Mono either — the sans/mono contrast is a load-bearing part of this system's identity, not a decorative flourish.

**Prefer self-hosted, base64-embedded fonts over CDN links whenever the deck must work offline or the network cannot be guaranteed** (the common case for `frontend-slides` output, which is meant to be a single self-contained file). Use the font files bundled with this skill at `reference/fonts/`:

- `Pretendard-Light.woff2` / `-Regular.woff2` / `-SemiBold.woff2` / `-Bold.woff2` → weights 300 / 400 / 600 / 700
- `JetBrainsMono-Regular.ttf` / `-Bold.ttf` → weights 400 / 700 (JetBrains Mono is only ever used at these two weights — eyebrow/caption text is not variable-weight)

Embed each as a `@font-face` with `src: url(data:font/woff2;base64,...)` (or `font/ttf` for the JetBrains Mono `.ttf` files) directly in the deck's `<style>` block, one `@font-face` rule per weight:

```css
@font-face { font-family: 'Pretendard'; font-weight: 300; src: url(data:font/woff2;base64,...) format('woff2'); font-display: swap; }
@font-face { font-family: 'Pretendard'; font-weight: 400; src: url(data:font/woff2;base64,...) format('woff2'); font-display: swap; }
@font-face { font-family: 'Pretendard'; font-weight: 600; src: url(data:font/woff2;base64,...) format('woff2'); font-display: swap; }
@font-face { font-family: 'Pretendard'; font-weight: 700; src: url(data:font/woff2;base64,...) format('woff2'); font-display: swap; }
@font-face { font-family: 'JetBrains Mono'; font-weight: 400; src: url(data:font/ttf;base64,...) format('truetype'); font-display: swap; }
@font-face { font-family: 'JetBrains Mono'; font-weight: 700; src: url(data:font/ttf;base64,...) format('truetype'); font-display: swap; }
```

Only when a deck is guaranteed to always be viewed online (e.g. deployed to a URL, never distributed as a standalone file) is it acceptable to load from CDN instead:

```html
<!-- Pretendard variable (fine weight axis) -->
<link rel="stylesheet" as="style" crossorigin
      href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/variable/pretendardvariable.min.css">
<!-- JetBrains Mono for eyebrows / captions / page numbers -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
```

Pretendard's variable axis lets weight carry hierarchy at fine increments. Where this document specifies weight 300 vs 400 vs 600 vs 700, honor the exact value — the near-invisible weight steps are how Canvas expresses emphasis without changing size or color.

## Overview

Canvas is a **monochrome-plus-pastel** presentation system. At the system level it is an editor-clean black-and-white frame: white canvas, black ink, Pretendard body copy hovering around weight 300–400, oversized display headlines with aggressive negative tracking, and small mono eyebrows marking each section. Every tag and CTA is a pill; there is not a single square button in the system.

What makes Canvas distinctive is what happens **between** the monochrome slides: the deck repeatedly drops a whole slide into an oversized pastel **color block** — lime, lavender, cream, mint, pink, coral, or a deep navy — that fills the entire 1920×1080 stage edge to edge, like a designer arranging giant sticky notes on a clean wall. These are not accents tucked into a card; a color block **is** the slide. Section breaks, statements, quotes, and hero stats live on color blocks; content, lists, comparisons, and dense reads live on white canvas.

This is a system built on contrast and rhythm: the monochrome slides make the color blocks feel intentional rather than decorative, and the color blocks make the monochrome slides feel like editorial paper rather than enterprise SaaS. The deck never reaches for shadows or gradients to do work that color blocks and confident typography already do.

**Density philosophy: generous and confident.** Body copy is always black; weight (not opacity, not color) carries hierarchy. Line-heights run tight on display sizes (1.0–1.05) and open on body (1.4–1.5). Color-block slides are the sparsest — one headline, generous side margins, poster-like breathing room. White content slides can carry more structure (columns, cards, stat rows) but never crowd edge to edge.

**Key Characteristics:**
- Monochrome core: `{colors.canvas}` white and `{colors.ink}` black carry every content slide, every body line, every pill, every page number.
- Oversized full-bleed pastel **color-block slides** (`{colors.block-lime}`, `{colors.block-lilac}`, `{colors.block-cream}`, `{colors.block-mint}`, `{colors.block-pink}`, `{colors.block-coral}`, `{colors.block-navy}`) define the section rhythm of the deck.
- Pill is the only tag/CTA shape — `{rounded.pill}`. Never a square button.
- Pretendard variable at fine weights (300, 400, 600, 700) reads as one voice that flexes rather than a stepped weight family. Korean-first.
- Tight negative letter-spacing on display sizes (−3px at 150px) creates a confident editorial cadence.
- `JetBrains Mono` reserved for eyebrows, captions, and page numbers — always uppercase, positive tracking — to flag taxonomy without competing with display type.
- Zero shadows. The change from white slide to pastel slide **is** the depth device.
- Weight, not color, carries body hierarchy. There is no mid-gray text role.
- Deck chrome outside the stage — a right-edge `{components.dot-nav}` and a custom `{components.cursor-ring}` — both reuse `{colors.accent-magenta}` as the one consistent interactive signal, independent of the in-slide single-shot promo-pill rule.

## Colors

### System Core
- **Ink** (`{colors.ink}` — #000000): Every headline, every body line, every page number, every pill outline on white and pastel surfaces. Also the fill of solid CTA pills and pure-black closing slides.
- **Canvas** (`{colors.canvas}` — #ffffff): Default slide background and the ground of every content slide.
- **Surface Soft** (`{colors.surface-soft}` — #f7f7f5): Off-white tile background for small cards, template thumbnails, or icon chips that sit on the white canvas. Barely distinct from canvas — a whisper, not a panel.
- **Hairline** (`{colors.hairline}` — #e6e6e6): 2px region dividers and card borders on white surfaces. **Hairline Soft** (`{colors.hairline-soft}` — #f1f1f1): even subtler row separators.

### Color Blocks (signature)
Each is a full-slide pastel ground. Text on the six pastels is always `{colors.on-block}` black; text on navy is `{colors.on-navy}` white.
- **Lime** (`{colors.block-lime}` — #dceeb1): The signature block — systems, agenda, FAQ, opening statements.
- **Lilac** (`{colors.block-lilac}` — #c5b0f4): Hero / highlight sections, feature reveals.
- **Cream** (`{colors.block-cream}` — #f4ecd6): Soft warm ground — quotes, warm section breaks.
- **Mint** (`{colors.block-mint}` — #c8e6cd): Calm section beats, process steps.
- **Pink** (`{colors.block-pink}` — #efd4d4): Warm human sections, testimonials.
- **Coral** (`{colors.block-coral}` — #f3c9b6): Energetic story blocks, "what's next".
- **Navy** (`{colors.block-navy}` — #1f1d3d): The only dark pastel — weighty section breaks, big-stat slides, and pre-closing beats. Uses white text.

### Accent & Semantic
- **Magenta Promo** (`{colors.accent-magenta}` — #ff3d8b): A single saturated CTA pink. At most **one** per deck, on the one moment that must pop against an already-colored panel. Never a section color. (This single-shot rule governs in-slide content only; magenta is also reused, independently, as the deck's interactive-chrome color for the progress bar, dot-nav active state, and cursor-ring hover — see Presentation Chrome under Layout.)
- **Success Green** (`{colors.semantic-success}` — #1ea64a): Checkmark glyph fill in comparison layouts. Used as a glyph, never a surface.

There is deliberately **no mid-gray text role**. Body hierarchy comes from Pretendard weight (300 vs 400 vs 600), not from opacity or gray. If a line needs to recede, drop its weight — do not gray it.

## Typography

### Font Ladder
Two families in strictly separated roles:
- **Pretendard** (`{typography.display.fontFamily}`) — variable Korean-and-Latin sans. Carries every headline, every paragraph, every stat, every pill label. The variable axis is exercised at fine increments (300 for display and body, 400 for lead, 600 for headlines/labels, 700 for card titles). The system reads as a single voice modulating rather than a stepped weight family.
- **JetBrains Mono** (`{typography.eyebrow.fontFamily}`) — mono, used exclusively for eyebrows, captions, and page numbers. Always uppercase with positive letter-spacing. Latin and numerals only — never set Hangul in mono.

### Type Scale

| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `{typography.display}` | 150px | 300 | 1.0 | −3px | Cover hero headline |
| `{typography.h1}` | 104px | 300 | 1.05 | −2px | Chapter / section opener on color blocks |
| `{typography.stat-value}` | 220px | 300 | 0.9 | −6px | Oversized statistic numeral |
| `{typography.quote-text}` | 76px | 300 | 1.2 | −1.5px | Pull-quote body |
| `{typography.headline}` | 60px | 600 | 1.15 | −1px | Primary slide headline (content slides) |
| `{typography.subhead}` | 44px | 300 | 1.3 | −0.5px | Intro paragraph at near-headline scale |
| `{typography.card-title}` | 34px | 700 | 1.3 | −0.3px | Column / card titles |
| `{typography.body-lg}` | 32px | 400 | 1.4 | −0.2px | Lead body, hero supporting line |
| `{typography.body}` | 26px | 400 | 1.5 | −0.2px | Default body, list items |
| `{typography.body-sm}` | 22px | 400 | 1.45 | −0.1px | Card body, footnote |
| `{typography.button}` | 26px | 600 | 1.0 | −0.1px | Pill labels |
| `{typography.eyebrow}` | 24px | 500 | 1.3 | +1.6px | Mono uppercase kicker |
| `{typography.caption}` | 18px | 400 | 1.2 | +1.2px | Mono uppercase caption, page number |

### Principles
- **Weight, not size, carries hierarchy on body copy.** A 32px lead at weight 400 sits next to a 60px headline at weight 600 — the eye reads emphasis from the weight jump as much as the size. Within a paragraph, emphasize by switching weight (400 → 700), never by color or italic.
- **Negative letter-spacing scales with size.** Display pulls −3px; body stays near-zero. Editorial-feeling display type without sacrificing readability at body size.
- **Mono is taxonomy, not body.** JetBrains Mono is only eyebrows, captions, and page numbers — never a paragraph, never Hangul.
- **Tight line-heights on display, generous on body.** Display 1.0–1.05; body 1.4–1.5. Headlines are graphics; body copy is for reading.
- **16px is the floor. No text anywhere in the deck renders below 16px, with no exceptions.** This applies to every improvised label too — video badges, image captions, footnotes, status notes, legal disclaimers — not just the tokens named in the Type Scale table. If a piece of chrome feels like it "needs" to be smaller than `{typography.caption}` (18px) to fit, that is a layout problem to solve (more space, a shorter label, a second line) — never a font-size problem to solve by dropping under 16px.

### Signature Treatments
These are non-optional whenever the element type appears:
- **Every eyebrow is JetBrains Mono, uppercase, black, tracked ≥1.6px.** An eyebrow that is Pretendard, lowercase, or gray is not an eyebrow.
- **Every statistic is oversized Pretendard weight 300 in the surface's primary text color (black on white/pastel, white on navy) — never a colored numeral.** Scale and weight carry the stat; color never does.
- **In-paragraph emphasis is a weight jump (400 → 700) in the same black.** No italic, no underline, no color for emphasis.
- **The page-counter/deck-label footer (`{components.chrome-footer}`) is mono, uppercase, bottom corners, and always present on every slide.** It lives outside the 1920×1080 stage as deck-level chrome (see Presentation Chrome), so it never competes with a slide's own poster-like emptiness — there is no per-archetype "chrome on/off" distinction anymore.

## Layout

### Slide Archetypes
Canvas is composed from a small set of slide archetypes. The single most consequential decision for any slide is **which surface it sits on** — white canvas or one pastel color block.

Every archetype below sits under the same universal, always-on `{components.chrome-footer}` (page counter + deck label, outside the stage — see Presentation Chrome). None of the descriptions below add further in-slide chrome on top of that.

- **Cover** (white canvas): Mono eyebrow top-left, huge `{typography.display}` headline in black, one `{typography.body-lg}` supporting line, an outlined `pill-tag` with date/author. *Alternative:* a full color-block cover (e.g., lilac) with the headline in black — use when the deck wants to open loud.
- **Chapter / Section break** (color block, full bleed): A pastel or navy fills the whole stage. A big mono section number ("01"), a `{typography.h1}` title, generous margins. This is the primary use of color blocks — the surface change *is* the section break.
- **Statement** (color block or white): One sentence at `{typography.h1}`/`{typography.quote-text}` scale, weight-emphasis on the key phrase. Poster-like, one idea.
- **Content** (white canvas): Mono eyebrow, `{typography.headline}` title, then a single editorial column or a 2–3 column grid of `{typography.card-title}` + `{typography.body}`. May place one `inset-block-card` (rounded 40px pastel card) as a focal element.
- **Stat** (navy or white): One to three oversized `stat-numeral` figures with a small mono caption beneath each. On navy the numerals are white; on white they are black. Weight 300, never colored.
- **Quote** (cream or lilac block): A `{typography.quote-text}` pull-quote in black, an attribution line in mono below. Generous margins.
- **Comparison** (white canvas): Two columns separated by a single `hairline-divider`, each headed by a `pill-tag`. Success checkmarks in `{colors.semantic-success}`.
- **Closing** (navy or pure-black): White headline, a solid white CTA pill (or the one `magenta-promo` pill if a single hot moment is warranted).

### Padding & Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.slide-pad-x}` | 140px | Horizontal slide margin on content slides |
| `{spacing.slide-pad-y}` | 100px | Vertical slide margin |
| `{spacing.block-pad}` | 96px | Interior padding of inset block cards |
| `{spacing.gap-lg}` | 64px | Between major regions |
| `{spacing.gap-md}` | 36px | Between related elements |
| `{spacing.gap-sm}` | 18px | Between tightly coupled elements |

Color-block statement / chapter slides give the type extra breathing room — often more than a quarter of the stage width as side margin — so the panel reads as a poster, not a wall of copy.

### Rhythm Rule (non-negotiable)
Between any two **different** color-block slides, return to a white canvas slide — never place two differently-colored blocks back to back. Consecutive color-block slides are allowed only when they share the same color (a multi-part section on one ground). White canvas is what makes each color block read as deliberate. This is the deck-level translation of the source system's "return to white between every two blocks."

### Presentation Chrome

Three pieces of deck-level chrome — `{components.dot-nav}`, `{components.chrome-footer}`, and `{components.cursor-ring}` — are Canvas's specific answer to the generic "optional enhancements" the Frontend Slides skill allows any template to adopt when they match its style. They split into two different placement strategies; do not conflate them.

**`dot-nav` and `chrome-footer` live INSIDE `#deckStage`, not outside it — this is a hard requirement, not a style choice.** Render both as ordinary `position: absolute` elements authored directly in 1920×1080 stage-pixel coordinates (e.g. `bottom: 34px; left: 60px`), placed as DOM children of `#deckStage` itself (siblings of the `.slide` sections, appended after them). Because `#deckStage` is the element that receives the single `transform: translate(...) scale(...)`, anything positioned inside it is carried along by that same transform automatically — it never needs its own resize listener, live-transform read, or recomputed pixel math. An earlier iteration of this template kept these two pieces `position: fixed` on the viewport and recalculated their pixel offsets in JS from the stage's live scale/offset on every resize; that approach works but is strictly more code for an identical visual result, and it is easy to get the recomputation subtly wrong (drift into the letterbox margin, stale values after a resize). Prefer the simpler stage-embedded approach.

**Self-adapting contrast via `mix-blend-mode: difference` — for `dot-nav` and `chrome-footer` only — requires each blended element to be a direct rendering child of `#deckStage`, with zero intermediate wrapper.** This is the load-bearing implementation detail: `mix-blend-mode` only blends against the true slide content when the blended element sits exactly one level below `#deckStage` in the render tree. Any extra positioned wrapper in between — even a plain flex-centering `<div>`, even drawing the mark on a `::before` pseudo-element instead of the element's own background — silently isolates the blend to that local box, and the "white" mark renders as flat opaque white instead of self-adapting (invisible on white canvas). Concretely: give `.dot-nav` itself `display: contents` so it contributes no box of its own and each dot button becomes a true sibling of the `.chrome-footer-*` elements and the `.slide` sections; give each dot button its own `position: absolute` + `mix-blend-mode: difference` (never a shared wrapper's blend-mode). Do the same for chrome-footer: the deck label and page counter are each their own absolutely-positioned, independently-blended element — not two children of one blended footer `<div>`. The resting/inactive state of both is drawn in white with `mix-blend-mode: difference`, which the browser computes per-pixel against whatever is directly beneath it — automatically dark on white/pastel, automatically light on navy/black, with no per-surface rule to maintain. The one deliberate exception is `{colors.accent-magenta}` itself: the dot-nav's active-dot state switches `mix-blend-mode` back to `normal` so it renders as true, unblended brand magenta rather than an inverted color.

**`{components.cursor-ring}` is the one piece of chrome that stays `position: fixed` on the real viewport, and the one piece that deliberately opts out of the blend-mode trick.** It must track the raw mouse position everywhere, including into the letterboxed/pillarboxed margin outside the scaled stage — a stage-embedded element cannot do that, since it is clipped to the 1920×1080 stage bounds. `mix-blend-mode: difference` against a white/pastel canvas also inverts a white shape to solid, opaque black — at cursor scale this reads as a harsh black dot, not a deliberate pointer. Instead, JS toggles an `on-dark` class on the cursor based on whether the active slide carries `{colors.block-navy}` (Canvas's only dark surface): resting fill is solid `{colors.accent-magenta}` (a small 20px filled dot, not a hollow ring) on every light/pastel slide, and solid white at rest on navy/closing slides. Since Canvas has exactly one dark surface, this two-state branch does not carry the "silently breaks on an unanticipated surface" risk that rules out per-surface classes for dot-nav/chrome-footer.

- **`{components.dot-nav}`** — a vertical column of one dot per slide, positioned `right: 40px` with each dot's `top` set once in stage-pixel coordinates (e.g. evenly spaced, vertically centered across the 1080px stage height: `startTop = (1080 - totalColumnHeight) / 2`, then `startTop + i * pitch` per dot) — computed once at build time, never recomputed on resize. This is Canvas's progress indicator. Clicking a dot jumps to that slide.
- **`{components.chrome-footer}`** — a mono deck label (`left: 60px`) and a page counter (`right: 60px`, JS-updates its text content on every `showSlide()`, e.g. `03 / 12`), both `bottom: 34px` in stage-pixel coordinates. Always visible on every slide, including cover, chapter, statement, quote, and closing.
- **`{components.cursor-ring}`** — a custom circular cursor that replaces the system pointer on pointer-fine devices, tracking the raw mouse position via `position: fixed` on the viewport (not stage-anchored, since it must follow the cursor everywhere, including the letterboxed margin). Resting color branches light/dark per current slide (see above) instead of using mix-blend-mode.

**Magenta-as-interactive-chrome exception:** the "single-shot" rule for `{colors.accent-magenta}` (see Accent & Semantic) governs in-slide content — at most one `magenta-promo` pill burned into the 1920×1080 canvas per deck. It does not restrict deck-level chrome: the dot-nav's active dot and the cursor-ring (resting on every light/pastel slide, plus its hover fill on any slide) both reuse `{colors.accent-magenta}` continuously as the deck's one consistent "interactive" signal color. Using magenta for chrome does not spend the deck's one in-content promo pill — the two uses are independent.

## Depth & Elevation

Canvas is **shadow-light by design**. The change from white slide to pastel slide is the primary depth device. Where most decks use a shadowed card to draw attention, Canvas uses a saturated full-slide ground. This makes the rare actual shadow feel like an exception worth noticing.

| Level | Treatment | Use |
|---|---|---|
| 0 (flat) | No shadow, no border | Color-block slides, covers, closings, statements |
| 1 (hairline) | 2px `{colors.hairline}` border on `{colors.canvas}` | Comparison cells, small cards, thumbnail tiles |
| 2 (rare soft) | `0 8px 32px rgba(0,0,0,0.06)` | A single floating tile hovering over a pastel block — used at most once per deck |

Do not add drop shadows to color-block slides. Do not add gradients — the system has none. Regions on white separate via 2px hairlines; regions on pastel separate via a slightly darker mix of the block color, never a shadow.

## Shapes & Treatment

### Border Radius

| Token | Value | Use |
|---|---|---|
| `{rounded.xs}` | 3px | Small chip / link decoration corners |
| `{rounded.sm}` | 10px | Sub-labels, small tags |
| `{rounded.md}` | 14px | Image frames, thumbnail tiles, list-item cards |
| `{rounded.lg}` | 40px | `inset-block-card` — a pastel block used as a card inside a white slide |
| `{rounded.pill}` | 999px | Every tag and CTA |

Full-bleed color-block **slides** have no rounded corners (they fill the stage edge to edge). The 40px radius appears only when a pastel block sits *inside* a white slide as a card. Image frames use 14px — friendly but editorial. No avatar circles; the system avoids personification.

### Decorative Vocabulary
- **Pill tag** — outlined black pill (2px border, 999px radius) around a mono or Pretendard label. The system's atomic tag. On navy/closing it inverts to a white outline.
- **Solid pill** — filled black CTA pill; inverts to solid white on dark surfaces. The one hot variant is `magenta-promo`, capped at one per deck.
- **Hairline divider** — 2px `{colors.hairline}` rule on white; a darker block-color mix on pastel.
- **Section numeral** — oversized mono number ("01", "02") pinned to a chapter slide's corner.
- **Inset block card** — a 40px-radius pastel rectangle placed on a white slide to hold a focal stat or callout; the only rounded pastel in the deck.

## Media & Video

Screenshots, diagrams, and video all share one container — `{components.shot-frame}` — so evidence reads as one consistent system rather than a mix of ad-hoc image treatments. Group 2–4 `shot-frame`s in a `.shot-row` grid (`cols-2` / `cols-3` / `cols-4`), each with a centered mono `{typography.caption}` label beneath it.

**Video is a real `<video>` element, framed like any other screenshot — never a static poster image with a fake play button standing in for it.** Concretely:

- `<video src="relative-file.mp4" controls preload="metadata" playsinline muted></video>` inside a `shot-frame.has-video`.
- The source file ships as a **sibling file next to the deck HTML**, referenced by relative path — do not inline video as a base64 data URI. Unlike fonts and images, embedding buys nothing here: the file still has to travel with the deck for offline use either way, and base64 only inflates the single HTML file by the video's full size (often the single largest asset in the deck) with no offline-capability benefit in return.
- A small solid-magenta `{components.magenta-promo}`-styled badge (pill, `{typography.caption}`, reading "동영상" or "VIDEO") pins to the top-left corner of the frame to flag it as playable before the user interacts with it. This badge is exempt from the deck's one-`magenta-promo`-per-deck budget — it is functional labeling, not a call-to-action.
- JS must pause any slide's `<video>` the moment that slide stops being the active one (inside the same `showSlide()` step that toggles `.active`/`.visible`), so navigating away never leaves audio or playback running in the background.
- If a poster/preview frame is genuinely needed for a slow-loading or very large video, use the browser's native `poster` attribute on the `<video>` tag itself — do not build a separate `<img>` + custom play-icon overlay as a replacement for the real player.

## Do's and Don'ts

### Do
- Decide **first** which surface a slide sits on — white canvas or one `{colors.block-*}` ground. It is the most consequential choice.
- Let a color block take the **whole slide**, full bleed, edge to edge. A color block is a slide, not an accent inside one.
- Return to white canvas between two differently-colored blocks so each reads as deliberate.
- Keep type in Pretendard at 300 / 400 / 600 / 700. Express hierarchy through the weight jump, not color.
- Reserve `{colors.ink}` black fill for genuine CTA pills and pure-black closings — not as a decorative accent.
- Use JetBrains Mono only for eyebrows, captions, and page numbers — always uppercase, tracked, Latin/numerals only.
- Compose every tag and CTA as a pill (`{rounded.pill}`). No square buttons anywhere.
- Color every statistic with the surface's primary text color (black or white) at weight 300 — let scale carry it.
- Keep Korean copy in Pretendard with letter-spacing at 0 and slightly looser line-height (see CJK section).
- Embed video as a real `<video>` element with a sibling file next to the deck HTML, framed in `{components.shot-frame}` like any other piece of evidence.

### Don't
- Don't introduce mid-gray text. Body hierarchy comes from Pretendard weight, not opacity.
- Don't add drop shadows or gradients to color-block slides — the color is the depth.
- Don't place two differently-colored blocks back to back, or two color blocks visible at once.
- Don't square off CTAs. Square buttons read as a different system.
- Don't color a statistic (no green/blue numerals). Scale and weight carry stats; color never does.
- Don't set Hangul in JetBrains Mono, and don't set a paragraph in mono — mono is taxonomy only.
- Don't introduce a new accent outside the documented `{colors.block-*}` palette and the single `{colors.accent-magenta}`.
- Don't emphasize in-paragraph text with italic, underline, or color — use a weight jump (400 → 700) in the same black.
- Don't crowd a color-block statement slide edge to edge; the poster breathing room is the register.
- **Don't use any font besides Pretendard and JetBrains Mono, ever — not as a temporary placeholder, not as a CDN-blocked fallback, not `system-ui`, not a third accent typeface.** If a font fails to load, fix the loading (embed it), don't let the browser silently substitute.
- **Don't render any text below 16px, anywhere** — including badges, captions, footnotes, and other small chrome that didn't make it into the Type Scale table. Solve tight space with layout, not with shrinking text under the floor.
- **Don't fake video with a poster image and a CSS play-icon overlay when the real video file is available.** Embed the actual `<video>` element (see Media & Video); a static mockup is a regression, not a simplification.
- **Don't inline a video file as base64.** Ship it as a sibling file with a relative `src` — see Media & Video for why base64 has no offline-capability benefit for video the way it does for fonts and images.

## CJK & Korean Content

Canvas is **Korean-first** — Pretendard was chosen precisely because it renders Hangul and Latin as one coherent variable voice, so the whole system works natively in Korean with no font switching.

### Universal Korean / CJK Adjustments
- **Letter-spacing drops to 0 on Hangul.** The negative tracking specified for display sizes (−3px, −2px) is a Latin-display convention that breaks Hangul rendering. Keep it on Latin runs; zero it on Korean runs. A mixed line can keep the Latin half tracked and the Hangul half at 0.
- **Line-height opens on Korean body.** Where Latin body runs 1.4–1.5, Korean body should run 1.55–1.7 — Hangul fills its em-box and needs vertical breathing.
- **No uppercase transform on Hangul.** Uppercase is a Latin convention; the mono eyebrow's `text-transform: uppercase` applies only to Latin/numeral eyebrows. Korean eyebrows stay as-is and rely on mono + small size + tracking to read as taxonomy.
- **Mono is Latin-only.** Keep eyebrows, captions, and page numbers in JetBrains Mono with Latin words or numerals (e.g., `SECTION 01`, `2026`). Do not set a Korean eyebrow in mono — set it in Pretendard at eyebrow size with `{colors.ink}` and tracking instead.
- **Statistics stay in Latin numerals.** Use Western numerals for stats (the universal editorial-statistical convention). Don't substitute Korean numerals.
- **Weight-based emphasis translates perfectly.** The 400 → 700 weight jump for in-line emphasis works identically in Hangul; there is no italic dependency to lose.
- **Pangu spacing** — insert a thin space between Hangul and adjacent Latin/numerals (`Claude 사용` not `Claude사용`) for legibility at display scale.
- **No period on display headlines.**

### Known Korean Gap
- Pretendard's variable weight axis renders fine increments beautifully on modern browsers; if the variable CSS fails to load (network/ad-block), the static Pretendard fallback snaps to the nearest 100-step weight (300/400/600/700 map cleanly, so the loss is minimal). If Pretendard fails entirely, `system-ui` carries Korean legibly but loses the deck's tuned weight rhythm.

## Iteration Guide

1. For any new slide, decide **first** which surface it sits on — white canvas or one `{colors.block-*}` ground. Everything else follows from that.
2. Reference components by their `components:` token name (e.g., `{components.pill-tag}`, `{components.color-block-slide}`, `{components.stat-numeral}`).
3. Default body type to `{typography.body}`; reach for `{typography.headline}` or `{typography.subhead}` for a slide's main statement. Reach for `{typography.display}`/`{typography.h1}` only on covers and chapter slides.
4. Keep `{colors.ink}` black scarce as a fill — one solid pill per CTA slide, not two. If two solid black pills appear on one slide, neutralize one to an outlined `pill-tag`.
5. Treat `{colors.accent-magenta}` as a single-shot color: one promo pill in the entire deck, never two.
6. Every new tag or CTA is a pill. Every new statistic is oversized weight-300 in the surface's text color. Every new eyebrow is mono uppercase Latin.
7. Maintain the rhythm rule: white canvas separates two differently-colored blocks. If a section needs several color-block slides in a row, keep them all on the same color.
8. For emphasis inside a paragraph, jump weight (400 → 700) — never add a second color or italic.
9. Run `npx @google/design.md lint design.md` after edits — `broken-ref`, `contrast-ratio`, and `orphaned-tokens` warnings flag issues automatically.
10. Deck-level chrome (progress bar, `{components.dot-nav}`, `{components.chrome-footer}`, `{components.cursor-ring}`) lives outside the stage — reuse these tokens rather than inventing new chrome per deck, and remember the magenta-as-interactive-chrome exception described under Presentation Chrome.
11. Any stage-anchored chrome (dot-nav, chrome-footer) must be positioned from the live stage transform (scale + offset), recomputed on resize — never with a CSS position fixed to the viewport corner, or it drifts into the letterbox margin on non-16:9 windows.
12. Any resting/inactive **dot-nav or chrome-footer** color should default to white with `mix-blend-mode: difference` rather than a hardcoded per-surface color — it self-adapts to any current or future slide background. Reserve `mix-blend-mode: normal` for the deliberate `{colors.accent-magenta}` active/interactive states, which must always render as true, unblended magenta. **`cursor-ring` is the exception**: branch its resting color explicitly (`{colors.accent-magenta}` on light/pastel, white on `{colors.block-navy}`) via an `on-dark` class rather than mix-blend-mode — see Presentation Chrome.

## Known Gaps
- The pastel `{colors.block-*}` hex values are derived from the source Figma marketing analysis (screenshot-approximated); treat them as faithful approximations, tunable per deck.
- The system ships no light-on-light or low-contrast state; the only dark surfaces are `{colors.block-navy}` and pure-black closings. A deck that needs many dark slides in a row should reconsider whether Canvas is the right system — its register is bright and editorial.
- Default to self-hosted base64 fonts from `reference/fonts/` (see Fonts & Loading) so decks work with no network at all; use the CDN links only for decks guaranteed to always be viewed online. Never let this fall back to `system-ui` / `ui-monospace` — Pretendard and JetBrains Mono are the only two fonts this system ever renders.
- The single soft shadow (level 2) is intentionally undertokened — it exists as a once-per-deck exception, not a reusable elevation primitive.
- `{components.cursor-ring}` only applies on pointer-fine input; touch and coarse-pointer devices fall back to the native cursor, and inline text-editing mode also temporarily restores the native cursor so users can place a text caret normally.
- Stage-anchored chrome (`{components.dot-nav}`, `{components.chrome-footer}`) relies on JS reading the stage's live transform on every resize; if a future implementation changes how the stage is scaled/positioned, this positioning logic must be updated in lockstep or the chrome will silently drift back into the letterbox margin.
- `mix-blend-mode: difference` is broadly supported in modern browsers but has no graceful fallback — on an unsupported/very old browser, resting-state dot-nav and footer text would render as flat opaque white rather than self-adapting, which stays legible on navy/black but is low-contrast on white canvas. (`cursor-ring` is unaffected — it no longer depends on mix-blend-mode.)
