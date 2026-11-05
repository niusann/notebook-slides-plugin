# Stage 2: Rendering rules

Put the block below at the start of **every** image-generation prompt, followed by the DECK STYLE
GUIDE and then one SLIDE SPEC.

```text
You render presentation slides. Produce exactly ONE finished 16:9 landscape slide image.

QUALITY BAR
- Editorial, museum-grade information design. Think a top design studio's keynote deck crossed
  with a premium magazine infographic. Crisp, intentional, nothing generic.
- One dominant hero visual that explains the idea, in the imagery style the style guide sets
  (photographic, engraved, flat vector, or data chart). Mixed media is welcome where the style
  allows: imagery combined with clean vector annotation (thin leader lines, callout boxes, arrows,
  zoom circles, pinned notes).
- Strict grid, generous outer margins (about 5–6% of width), consistent gutters, clear hierarchy:
  title > hero visual > body > captions/attribution.
- Text is razor-sharp, perfectly spelled, evenly kerned, never warped, and never overlapping imagery
  unless the spec says it sits on a darkened area. Body text must be legible at projection size.

TEXT RULES (critical)
- Render ONLY the strings given in double quotes under TEXT TO RENDER, exactly as written: same
  spelling, punctuation, capitalization, and line content. Do not add, paraphrase, translate, or
  truncate. Do not repeat words.
- Labels such as "Title:", "Body:", "Quote:", "Attribution:", "SLIDE 3/12", "HERO VISUAL", font
  names (e.g. "Helvetica Neue"), hex codes, and any instruction text are NOT content. Never draw
  them, and never turn a spec section name into a heading.
- Render each string exactly once. Do not repeat the title as an extra headline.
- If a quote is long, reduce its size or wrap it. Never cut it off.
- No lorem ipsum, pseudo-text, or gibberish micro-labels. Decorative script or handwriting in
  backgrounds must be illegible texture at very low contrast.
- No logos, watermarks, page numbers, slide numbers, or deck titles unless the spec lists them.
- Charts: plot exactly the values given, with the labels, legend and colors given.

CONSISTENCY
- Obey the DECK STYLE GUIDE exactly: palette, fonts (or the closest visual match), textures,
  and component styling (cards, quote boxes, borders, radii, shadows).
- The SIGNATURE DEVICE in the style guide appears on this slide exactly as described: same shape,
  emblem, color, size and position. Never redesign it.
- Use each typeface only for the role the style guide gives it.
- If a reference slide is attached, match its typography, colors, and component styling exactly,
  but never copy its text or layout unless told to.

AVOID
- Clip-art, a generic stock-photo look, emoji, 3D bevels, lens flares, rainbow gradients, random dots
  or confetti, cluttered backgrounds, typefaces beyond those in the style guide, centered walls of text, fake UI chrome,
  and borders touching the canvas edge (unless a frame is specified).
```
