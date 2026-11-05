# Stage 1: Planning the deck (PPTX version)

Act as the art director and information designer. The output is a DECK STYLE GUIDE plus one
SLIDE SPEC per slide. Each spec becomes one slide built from editable PowerPoint objects (native
text, shapes, charts, tables) over text-free art. A spec must be complete enough that the slide can
be built from it alone, without guessing.

Steps 1 and 2a–2c are the same as the image version of this skill. Step 2d (typography, imagery,
component kit) and step 3 (the spec format) differ, because the result has to work as a real,
editable PPTX.

## Step 1: Angle, structure and content (Checkpoint 1)

**1a. Read everything** in the conversation and every uploaded file. Inventory the user's assets
(photos, logos, charts, data tables, diagrams) and decide which slide each one serves. Real assets
beat invented imagery when they carry the argument. Data in a table or spreadsheet should become a
native chart or table, not a picture of one.

**1b. Pick the angle.** Don't summarize everything. Choose one focused thread with a point of
view that the sources support strongly, and state it as a reframe, e.g. "Holmes's stories as an
applied analytical framework", "the Revolution's women as an intelligence network", "freedom asked
of six philosophers". If the material is broad, offer 2–3 candidate angles in Checkpoint 1 and
recommend one. If the user gave a focus, use theirs.

**1c. Identify the deck's intent and genre**, because they decide density and the ending:
- *Explain a story/history/literature* → narrative arc, evidence quotes, closing quote or emblem.
- *Explain ideas/compare thinkers or options* → a question asked across the series, a synthesis
  timeline or matrix, closing reflective questions.
- *Teach how to do something* → numbered steps with claim titles, a diagnostic table, closing
  action checklist.
- *Brief technical/research results* → paradigm shift → system → results with real numbers →
  future work, optional appendix with data tables/charts.

**1d. Choose a series formula** for the middle of the deck: "Step 1–N", "Case File 01–N", "___ is
___.", "System Function: ___", one profile per person. Every member uses the same title pattern
and layout skeleton. Where depth matters, pair a "who/what" slide with a "how" slide (case file →
map, cross-section, schematic or timeline).

**1e. Plan 10–15 slides** (or the user's count): Cover → framing → series/sections → synthesis
(matrix, timeline, ripple diagram, two-lens summary) → intent-matched closing.

Output for Checkpoint 1: the angle (and alternatives if any), thesis, asset map, and a TOC with
number, working title, purpose, and key content per slide.

## Step 2: Design the master theme from scratch (Checkpoint 2)
There are no presets. Invent an art direction for this deck only.

**2a. Mine the content for visual raw material.** Write down, briefly:
- Subject, domain, and the genre of the sources (letters, journalism, fiction, academic book,
  research paper, interviews, internal docs).
- Era and place, if any.
- The physical "stuff" of the angle: its documents, tools, instruments, materials, environments
  (ledgers, wax seals, circuit boards, sea charts, lab glassware, X-rays, graph paper…).
- Tone the audience should feel (urgent, reverent, playful, forensic, optimistic) and the setting
  (boardroom, classroom, conference keynote, self-study).
- Any brand constraints from the user (colors, logo, fonts, a company template). These override
  everything else.

**2b. Pick the theme family** that fits the intent and genre:
- *Immersive world* (story, history, literature): a physical world with props that the deck lives
  in, such as a case board, a spy dossier, a manuscript or a ship's log. In PPTX the world lives in
  the art layer (backgrounds, props, portraits); cards, quotes and labels are native on top.
- *Field/specimen editorial* (popular science, nature, products): photoreal subjects with thin
  technical annotation. The photo is art; leader lines, callout dots and labels are native.
- *Genre-native editorial* (business, how-to, strategy): flat crisp vector diagrams, grid or
  plain paper, full-sentence claim titles, one bold accent (e.g. a highlighter mark). This family
  is almost entirely native shapes, which suits PPTX best.
- *Source-native technical* (research, engineering, data): the visual language of the field's own
  figures, with real native charts and color that encodes data consistently (e.g. baseline vs new).
- *Per-section shift* (modifier): when the deck compares distinct worlds, eras or thinkers, each
  section can take its subject's visual language. Then lock the layout skeleton, the title/body
  fonts, and the signature device so it still reads as one deck.

**2c. Generate 2–3 distinct directions** within or across families. Make them genuinely different
(light vs dark, photographic vs illustrated vs flat, period vs contemporary). Avoid generic
corporate looks and themes you've used before. Pick the one that best makes the angle visible.
Say for each direction how much depends on generated art: a direction that needs a picture on
every slide is riskier if image generation is unavailable.

**2d. Write the DECK STYLE GUIDE** for the chosen direction:
1. **CONCEPT**: one or two sentences naming the family, the world/metaphor, and the mood.
2. **PALETTE**: 5–7 colors with HEX and a role each: ground, surface (cards), ink, muted ink,
   rule (hairlines), accents with meaning (one color per pillar, red = threat, blue = baseline vs
   orange = new). Give a chart series order (which color is series 1, 2, 3). Check text/ground
   contrast (≥ 4.5:1 for body text), including text on dark panels and on photos.
3. **TYPOGRAPHY**: the fonts must render on the viewer's computer, because PPTX doesn't carry
   them. Choose from fonts installed with Office/Windows/macOS (Georgia, Cambria, Palatino
   Linotype/Book Antiqua, Garamond, Baskerville Old Face, Bodoni MT, Rockwell, Calibri, Arial, Segoe UI,
   Franklin Gothic, Gill Sans MT, Century Gothic, Consolas, Courier New…). For each face also name
   a fallback, and describe its character ("high-contrast transitional serif"). If the user can
   install fonts, a Google font is fine; say so and give the fallback. For Chinese/Japanese/Korean,
   give a separate East Asian font (e.g. Microsoft YaHei / PingFang SC / Noto Sans SC; SimSun or
   Noto Serif SC for a serif mood). Give **point sizes** on a 13.33 × 7.5 in slide for every role:
   kicker, title (≈ 28–40 pt), subtitle, body (≈ 14–18 pt, never < 12), quote, label, caption
   (≈ 10–12 pt), big stat. Give line spacing, letter-spacing for caps, and bold/italic rules.
   Two families plus at most one utility face.
4. **BACKGROUND & TEXTURE**: the ground per slide type (cover, content, divider): a solid fill, or a
   text-free texture image (paper grain, faint grid, topo lines, blueprint drawings), or a darkened
   photo. Textures stay low-contrast so text on them stays readable.
5. **IMAGERY (art layer)**: one picture style (or one per section for per-section shifts): e.g.
   "engraved portraits on parchment, cut out on a transparent background", "photoreal specimens on
   warm white with soft shadow", "none: flat native vector only". All generated art is **text-free**
   (`pptx-translation.md` §3). Say how the user's own photos are treated (crop, duotone, frame).
6. **SIGNATURE DEVICE**: the one element on every slide, described precisely as native objects
   with exact position and size in % of the slide (e.g. "a crimson #9E2B25 circle, 6% wide, its
   top-left at x 88%, y 82%, with a gold 'N' in Georgia 20 pt centered"; "a 0.6% wide accent bar
   down the left edge of every quote card"; "right sidebar, 26% wide, surface fill, titled 'The
   Freedom Test'"). If it is an image (a wax seal, an emblem), make it once and reuse the same file
   at the same position on every slide.
7. **COMPONENT KIT**: each component written as a buildable recipe: shape type, fill, outline color
   and weight, corner radius, shadow (usually none), inner padding, and the text roles inside.
   Cover at least: content card, quote box (and attribution format), callout/label with leader
   line, section divider, table (header fill, row rules, zebra or not), chart (series colors,
   gridlines, data labels, legend position, fonts), diagram node and connector (line weight,
   arrowheads, dashed for weak links), big-stat block, and the series card (e.g. the case-file
   field list).
8. **GRID**: margins (≈ 5–6% of width left/right, ≈ 7–8% top/bottom), the column grid (e.g. 12
   columns with 2% gutters), the title zone (same position on every content slide), and the
   footer zone if any.
9. **RECURRING MOTIFS** (optional): 1–2 secondary threads (bookend image, color tab per pillar).

## Step 3: Write one SLIDE SPEC per slide (Checkpoint 3), in exactly this format

Positions are **% of slide width/height**: `x, y, w, h`, measured from the top-left. List layers
from back to front.

```
SLIDE {n}/{N} — {ARCHETYPE}
PURPOSE: one line on what the viewer should understand.
BACKGROUND: solid {color role} | texture "{name}" | art image A{n}-bg (full bleed, with a
  {color} {opacity}% overlay so text stays readable)
ART: (only if the slide needs a picture) for each image:
  A{n}-{k}: what it shows, style, framing, transparent or rectangular, where its empty space is
  (text-free; see pptx-translation.md §3). Placed at x, y, w, h, crop "fill".
ELEMENTS (back to front):
  {id} {type} @ x, y, w, h: {style from the kit} — "{exact text}" (role)
  ...
  types: text | card | quote | callout | stat | node | connector | chart | table | image | icon | device
CHART/TABLE/DIAGRAM DATA: (when present) every category, series value, label, axis title, legend
  entry and color; every table cell; every node label and every connection (from → to, label, style).
NOTES: speaker notes for this slide (2–4 sentences, sources for numbers and quotes).
```

Example of the ELEMENTS block:

```
  t1 text @ 6, 8, 42, 5: kicker — "Profile 01"
  t2 text @ 6, 14, 42, 16: title — "James Madison: The Architect of Checks"
  t3 text @ 6, 34, 40, 26: body — "Madison arrived in Philadelphia with a plan already drafted…"
  q1 quote @ 6, 64, 40, 22: quote box — "Ambition must be made to counteract ambition."
     attribution "— James Madison, Federalist No. 51, 1788"
  i1 image @ 52, 0, 48, 100: A2-1 engraved portrait, crop fill
  d1 device @ 88, 82, 6, 10.7: seal
```

## Rules for the specs
- **Titles**: a hook ("Hook: Clarifier"), a series formula ("Case File 02: The Disguised
  Interceptors"), or, for how-to and argument decks, a full-sentence claim that states the takeaway.
  Every content slide puts its title in the same title zone.
- **Density by intent**: narrative decks get ONE paragraph of 30–70 words; how-to decks a claim
  title + 1–2 quotes + a diagram; technical decks a 1–3-sentence subtitle + chart/stats. Bullets max
  4, each ≤ 25 words. Total on-slide text ≤ 110 words (≤ 140 for technical/appendix slides;
  cover ≤ 25, divider ≤ 50). Extra detail goes into NOTES, not onto the slide.
- **Boxes must fit their text** at the role's point size. Rough check: one line of Latin text holds
  about `box width in pt ÷ (0.5 × font size)` characters (CJK: `÷ font size`); the slide is 960 ×
  540 pt. If it doesn't fit, cut words before shrinking type below the kit's sizes.
- **Quotes**: real, verbatim from the sources, always attributed ("— Name, Month Year" or "— Name,
  Title, Company"). Never invent quotes, numbers or names. A closing line that isn't a real quote
  must not be set in quotation marks.
- **Data goes native**: numbers become a native chart or table with every value written in the
  spec. Diagrams become native nodes and connectors with every label written in the spec. Never
  plan a chart, table, diagram or label as part of a generated image.
- **Hero visual still argues the point** (design-dna §4). Build it as a native diagram when it is
  a mechanism, process, comparison or structure; use art only when it is a person, place, object,
  specimen or scene, and annotate it natively.
- **Series slides** reuse the same element ids, positions and roles exactly ("Same layout as Slide
  3; only text and A{n} change"). Restate the font roles in each series spec so they don't drift.
- **Each string appears once.** No spec words (role names, font names, hex codes) in the quoted
  text. If a component needs a visible heading, write that heading as a quoted string on purpose.
- Vary the archetype outside the series; don't use the same layout three times in a row otherwise.
- Use the user's language for on-slide text if they write in another language, but keep the spec
  labels in English.
