# Canvas Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/canvas/design.md`
- Preview card: `bold-template-pack/templates/canvas/preview.md`

## Selection Metadata

- Slug: `canvas`
- Tagline: Monochrome editorial frame interrupted by oversized full-bleed pastel color-block slides; Pretendard Korean-first sans, pill-only CTAs, zero shadows.
- Mood: fresh, confident, playful-editorial, design-led
- Tone: clean, modern, joyful, considered
- Formality: medium
- Density: medium
- Scheme: light (with pastel + navy accents)
- Best for: Anything that should feel modern, design-led, and a little joyful — product launches, design/creative reviews, startup pitches, brand and systems decks, Korean-language decks that want a clean editorial voice with pops of color. Also a strong unexpected pick for tech, research, or internal reviews that want to read as tasteful rather than corporate.
- Avoid for: Contexts needing traditional institutional gravity, dark-mode-heavy decks, or a quiet single-accent restraint — the pastel color blocks commit to a bright, expressive rhythm.

## Visual Snapshot

A confident monochrome editorial deck interrupted by oversized hand-cut pastel color-block slides. The system core is rigorously black-and-white — Pretendard variable sans, pure white canvas, pure black ink, pill-shaped tags — while every section beat drops the whole slide into a saturated lime, lavender, cream, mint, pink, or deep navy panel that reads like a giant sticky note placed on a clean desk. Weight, not color, carries hierarchy on body copy; a condensed JetBrains Mono runs every eyebrow, kicker, and page number. Korean-first: Pretendard sets both Latin and Hangul as one voice.

The signature move at deck scale: a color block **is** a whole slide (full bleed, edge to edge), not an accent inside one. Content, lists, and comparisons live on white canvas; section breaks, statements, quotes, and hero stats live on full-slide pastel or navy grounds. White canvas always returns between two differently-colored blocks so each reads as deliberate.

## Preview Ingredients

- Palette: ink #000000; canvas #ffffff; block-lime #dceeb1; block-lilac #c5b0f4; block-cream #f4ecd6; block-mint #c8e6cd; block-pink #efd4d4; block-coral #f3c9b6; block-navy #1f1d3d; accent-magenta #ff3d8b (single-shot)
- Typography: Pretendard Variable (headlines + body, Korean-first, fine weights 300/400/600/700); JetBrains Mono (eyebrows, captions, page numbers, uppercase + tracked, Latin only)
- Signature move: A full-bleed pastel color block IS a slide, never an accent inside one — like a giant sticky note filling the stage.
- Signature move: Weight, not color, carries hierarchy — body is always black; emphasis is a 400→700 weight jump, never italic or color.
- Signature move: Pill is the only tag/CTA shape (999px radius); zero shadows, zero gradients — the color-block surface change is the depth.
- Signature move: Oversized weight-300 statistic numerals in the surface's text color (black on white/pastel, white on navy) — scale carries the stat, never color.
- Signature move: Return to white canvas between two differently-colored blocks so each pastel reads as deliberate.

## Fonts / Loading

- Only Pretendard and JetBrains Mono — no other font, no `system-ui` fallback, ever.
- Prefer self-hosted base64 `@font-face` using the files in `reference/fonts/` (Pretendard 300/400/600/700 woff2, JetBrains Mono 400/700 ttf) so decks work fully offline; CDN links (Pretendard via jsDelivr, JetBrains Mono via Google Fonts) are for online-only decks. See `design.md` → Fonts & Loading for the full policy.

## International / Korean Preview Note

- Canvas is Korean-first. Keep Hangul letter-spacing at 0 (drop the negative display tracking on Korean runs), loosen Korean line-height to ~1.55–1.7, and never uppercase-transform Hangul.
- Keep mono eyebrows/captions/page numbers in Latin words or numerals (`SECTION 01`, `2026`); a Korean eyebrow goes in Pretendard at eyebrow size, not mono.
- Use the full `design.md` CJK section after selection for exact adjustments.

## Preview Rules

- Build exactly one title slide at 1920x1080 inside the fixed-stage model.
- Preserve the palette, type roles, surface rhythm, pill shapes, and zero-shadow depth described above.
- For a cover, use a white canvas with a mono eyebrow, a huge black Pretendard display headline, one supporting line, and an outlined pill tag — OR a single full-bleed pastel block (e.g., lilac) with the headline in black. Do not mix two block colors on one slide.
- Use the user's real title/subtitle/context; do not copy demo slide content.
- The rendered preview must look like a real first slide, not a template-selection card.
- Never place internal workflow text on the slide: no `preview`, `generated from`, `preview.md`, `template`, `preset`, `style option`, `Option A/B/C`, file names, paths, or source-doc labels.
- Never place the template name or slug on the slide itself; mention it only in the chat message.
- Never place user requirement notes such as desired vibe, audience, or internal-use labels on the slide unless the user explicitly wants those exact words in the deck.
- Use only real deck content for visible chrome: deck title, real section title, date, author, company, page number, or genuine content phrases from the user material.
- Do not read `template.html` for preview generation.
- Do not read other templates' `design.md` files.
- After the user picks this template for the full deck, read the full design doc before generating final slides.
