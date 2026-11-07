---
name: notebook-slides
description: Create NotebookLM-quality slide decks as images. Plans the deck structure and per-page content from the chat and uploaded files, designs a fresh art direction (master theme) from scratch for this specific content, shows a detailed design for every page, then renders each slide as a finished 16:9 image with the image generation tool and delivers the deck as one PDF. Use when the user asks for slides, a deck, or a presentation made as images, or wants NotebookLM / Gemini Notebook style slides.
---

# Notebook Slides

Make decks at the design level of NotebookLM's slide feature. That feature works in two stages: a
planner designs a visual theme for the topic and writes a spec for each slide, then an image model
renders every slide as one finished picture. This skill reproduces that pipeline, with your own
image generation tool as the renderer.

**Every deck gets its own art direction, designed from scratch for its content.** There are no
presets or templates. Never reuse a theme from an earlier deck.

## Files

- `references/design-dna.md`: the principles that make these decks look premium. Read before planning.
- `references/planner.md`: how to build the outline, design the master theme, and write the slide specs.
- `references/rendering-rules.md`: the rules block that starts every image prompt.

## Workflow: three checkpoints, render, deliver PDF

Rendering costs image generations and is slow to redo, so all thinking happens before the first
image. Stop at each checkpoint and wait for the user's OK or edits. If the user says "just generate
it" (or similar), run the checkpoints silently and go straight to rendering.

### Step 0: Gather
Read everything: the conversation, every uploaded file (documents, notes, data, images), and any
links the user pasted. Note the audience, purpose, language, and requested slide count, if given.
Ask a question only if something essential can't be inferred (for example, two contradictory goals).

### Checkpoint 1: Outline (structure + content per page)
Follow `planner.md` step 1. Show:
- **Angle**: the focused, reframed thread the deck will follow (plus 2–3 alternatives if the
  material is broad), the deck's intent (story, ideas, how-to, technical brief), and the series
  formula (e.g. "Step 1–N", "Part I–III", "Case 01–N").
- **Thesis** in one sentence, and the narrative arc (acts or pillars).
- **Assets found**: each uploaded image, chart, or data table, and which slide will use it (or why
  it won't be used).
- **Table of contents**: one row per slide with number, working title, purpose, and the key content
  (facts, numbers, quotes) it will carry.

Wait for confirmation.

### Checkpoint 2: Master theme (designed from scratch)
Follow `planner.md` step 2. Derive the art direction from *this* content: its angle, the genre of
the sources, subject, era, materials, tone, and audience. Name the theme family (immersive world,
field editorial, genre-native editorial, source-native technical, optionally per-section shifts). Show 2–3 distinct directions in a line or two each, with your
recommendation and why it fits. Then give the full DECK STYLE GUIDE for the recommended one:
concept, palette (hex + role), typography with roles, background and texture, imagery style,
signature device, component kit, and recurring motifs.

Wait for the user to pick or adjust. If they pick another direction, write its full style guide.

### Checkpoint 3: Page designs
Follow `planner.md` step 3. Show every SLIDE SPEC in full: archetype, the exact text to render, the
hero visual, composition, and which uploaded asset goes where. This is what will be rendered, so the
user can fix wording and layout here cheaply.

Wait for confirmation, then render.

### Step 4: Render, one slide per image
**Use the image generation tool yourself, one call per slide.** The user should not have to select
anything. If no image generation tool is available in this chat, say so clearly, ask the user to
switch to a model or mode that can create images (or enable image creation in the composer), and
meanwhile output every finished prompt in a code block so nothing is lost.

Each prompt has these parts, in order:

```
[rendering-rules.md block]

[DECK STYLE GUIDE]

[ONE SLIDE SPEC]
```

- **Self-contained, verbatim prompts.** The image tool doesn't reliably see earlier turns, so always
  pass the full rules, full style guide, and full slide spec in every call—never "same as before",
  and never summarize, paraphrase, or strip out `TEXT TO RENDER` strings, hex codes, or layout
  percentages when invoking the image tool.
- **Size:** landscape 16:9 (e.g. 1376×768, 1792×1024, or 1536×1024). If the tool's widest landscape
  size is slightly taller than 16:9 (such as 1536×1024), instruct it to keep all content inside a
  centered 16:9 safe area with full-bleed background texture to the edges.
- **User's images:** when a spec uses an uploaded image (a photo, logo, chart, product shot), pass it
  to the image tool as an input/reference and say in the spec how to use it ("place this photo in
  the right 55%, duotone in the palette").
- **Consistency:** after the first slide is approved, attach it as a reference for later slides and
  add: "Match the typography, palette and component styling of the reference slide exactly; new
  content and layout below. Do not copy its text."
- Render in order. By default render slide 1, show it, and continue unless the user objects.
- **Limits:** if image generation is refused or rate-limited partway, stop, list the slides that are
  done, and print the remaining prompts so the user can continue later.

### Step 5: Check each slide
Before moving on, compare the image against its spec:
- Every quoted string is present, spelled exactly, not duplicated, not truncated.
- No stray text: field labels ("Title:"), font names, hex codes, slide numbers, or text carried over
  from other slides.
- Diagram and table labels sit on the right items, and chart values match the spec. These are
  the most error-prone slides.
- Fonts, colors, and components match the style guide; series slides use the same fonts as the
  first member of the series.
- The signature device is present and identical (same emblem, color, position).

If something fails, regenerate once with a targeted fix at the end of the prompt, e.g.
`FIX: the second paragraph repeated "growth"; render it exactly once.` If a text-heavy slide keeps
failing, shorten the body by about 20% or split the slide.

### Step 6: Iterate
The user can say "redo slide 7", "bigger titles everywhere", or "try a darker theme". Edit the spec
or the style guide, then re-render only the affected slides.

### Step 7: Deliver as one PDF
The slides are images, so the deliverable is a single PDF, nothing else (no PPTX). When all slides
are approved, use the Python/code tool with `Pillow` (`PIL.Image`, which is pre-installed in
standard sandboxes) to combine the final images in slide order into one PDF: convert each image to
`RGB`, center-crop to 16:9 (`width / height = 16 / 9`) if the renderer output a taller ratio like
3:2, and save with `first_img.save(pdf_path, "PDF", resolution=150.0, save_all=True, append_images=rest_imgs)`—one
slide per page, zero page margins. Name the file after the deck title and offer a download link. If
no code/file tool is available, list the slide images in order and tell the user to save them.

## Known failure modes (and guardrails)
- Repeated or dropped words in long paragraphs. Keep paragraphs ≤ 70 words.
- Diagram labels swapped or merged between nodes. List every node label and connection explicitly,
  and specify whether each label sits inside the node shape or outside to the left/right; re-check.
- Text or deck titles from the style guide leaking onto slides as a running header. Never put the
  deck title or font names in double quotes inside `DECK STYLE GUIDE` (use plain `DECK STYLE GUIDE`
  and unquoted font names), and include the "do not copy its text" line when attaching references.
- Display font substituted (sans instead of serif). Describe the font's visual traits inline on
  recurring fields in every series spec (e.g. `Heading (bold high-contrast serif ALL CAPS — never
  sans-serif)`), not just in the style guide.
- Tables crowding container edges or drawing uneven divider bars. Specify internal container padding
  so thin grid lines stop cleanly short of the card edges or outer margins, with uniform divider
  stroke weights.
- Left-edge clipping on long claim titles or left-column charts with vertical Y-axis labels. Always
  state an explicit 6–7% outer safe margin on all four sides (never "full-width"), and place a
  left-side chart's vertical Y-axis line at ~12% from the left edge so the rotated Y-axis label sits
  inside the canvas.
- Missing quotation marks when a decorative quote glyph is present. Explicitly state that quoted
  strings retain their surrounding double quotation marks alongside the decorative quote icon.
- Spec words printed on the slide: font names, field labels turned into headings ("The Visual",
  "The Evidence", "Section Title:"), or a title printed twice. Keep those words out of
  TEXT TO RENDER and say "render each string once".
- Signature device drifting across turns. Describe its exact shape, color, size, and position
  identically in every prompt and attach an approved slide as reference.
- Font drift inside a series. Restate the type roles inline in every series spec.
- Invented or unattributed closing quotes. Only real, attributed quotes go in quotation marks.
