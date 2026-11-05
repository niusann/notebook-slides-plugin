---
name: notebook-slides-pptx
description: Create NotebookLM-quality slide decks as a real, editable PowerPoint (.pptx). Plans the deck structure and per-page content from the chat and uploaded files, designs a fresh art direction (master theme) from scratch for this specific content, shows a detailed layered layout for every page, then builds each slide from native text, shapes, charts and tables over text-free generated art, and delivers one .pptx. Use when the user asks for a PowerPoint, a .pptx, editable slides, or NotebookLM / Gemini Notebook style slides they can edit.
---

# Notebook Slides (PPTX)

Make decks at the design level of NotebookLM's slide feature, delivered as a real PowerPoint file
the user can edit. NotebookLM plans a visual theme and a spec for each slide, then renders every
slide as one finished picture. This skill keeps the same planning and design method. Instead of a
picture per slide it builds each slide from **editable layers**: native text, shapes, charts and
tables on top of **text-free** generated art and textures.

**Every deck gets its own art direction, designed from scratch for its content.** There are no
presets or templates. Never reuse a theme from an earlier deck or from the examples mentioned in
the references; they only illustrate the method. A plain office-template look is a failure: the
deck must look designed, the way NotebookLM's do.

## Files

- `references/design-dna.md`: the principles that make these decks look premium. Read before planning.
- `references/planner.md`: how to build the outline, design the master theme, and write the
  layered slide specs.
- `references/pptx-translation.md`: how each design idea becomes PowerPoint objects, the
  text-free art prompt block, build rules and the final check. Read before building.

## Workflow: three checkpoints, art, build, deliver PPTX

Rebuilding is cheap but generating art is slow, so all design thinking happens before the first
image or build. Stop at each checkpoint and wait for the user's OK or edits. If the user says "just
generate it" (or similar), run the checkpoints silently and go straight to building.

### Step 0: Gather
Read everything: the conversation, every uploaded file (documents, notes, data, images,
spreadsheets, an existing .pptx or brand template), and any links the user pasted. Note the
audience, purpose, language, and requested slide count, if given. If the user gives a brand
template or brand fonts/colors, they override the theme design. Ask a question only if something
essential can't be inferred.
If there are no sources (just a topic), research it: use web search if available, otherwise your
own knowledge. Use only well-established facts, numbers and quotes you are confident are real, and
put where they come from in the speaker notes.

### Checkpoint 1: Outline (structure + content per page)
Follow `planner.md` step 1. Show:
- **Angle**: the focused, reframed thread the deck will follow (plus 2–3 alternatives if the
  material is broad), the deck's intent (story, ideas, how-to, technical brief), and the series
  formula (e.g. "Step 1–5", "Case File 01–04").
- **Thesis** in one sentence, and the narrative arc (acts or pillars).
- **Assets found**: each uploaded image, chart, or data table, and which slide will use it (data
  becomes native charts/tables), or why it won't be used.
- **Table of contents**: one row per slide with number, working title, purpose, and the key content
  (facts, numbers, quotes) it will carry.

Wait for confirmation.

### Checkpoint 2: Master theme (designed from scratch)
Follow `planner.md` step 2. Derive the art direction from *this* content: its angle, the genre of
the sources, subject, era, materials, tone, and audience. Name the theme family. Show 2–3 distinct
directions in a line or two each, with your recommendation and why it fits. Then give the full DECK
STYLE GUIDE for the recommended one: concept, palette (hex + role + chart series order),
typography with installed fonts, fallbacks and point sizes, backgrounds and textures, imagery
style for the art layer, signature device (as exact objects and position), component kit (as
buildable recipes), and grid.

Wait for the user to pick or adjust. If they pick another direction, write its full style guide.

### Checkpoint 3: Page designs
Follow `planner.md` step 3. Show every SLIDE SPEC in full: archetype, background, art images,
the element list with positions and exact text, chart/table/diagram data, and speaker notes.
This is what will be built, so the user can fix wording and layout here cheaply.

Wait for confirmation, then make the art and build.

### Step 4: Make the art (text-free)
List every ART entry across the specs (backgrounds, textures, portraits, scenes, props, the
signature emblem if it's an image). Generate them with the image generation tool yourself, one call
per image, using the art prompt block in `pptx-translation.md` §3. **No text in any image.**
- Reuse one image when the specs share it (a deck texture, the emblem), so it's identical everywhere.
- Use the user's uploaded images where the specs say so, cropped and treated as the guide says.
- Show the art briefly (a few at a time) so the user can veto a picture before it's placed.
- If image generation is unavailable, refused or can't reach the code tool, follow the fallback
  in `pptx-translation.md` §3 (placeholders + prompts in speaker notes) and say so. Genre-native
  and technical decks need little or no art; prefer native diagrams there anyway.

### Step 5: Build the PPTX
Use the code/file tool to write the .pptx, slide by slide from the specs, following
`pptx-translation.md` §1–§4: layer order, native objects for all text, data and diagrams,
explicit fonts/colors on every element, the signature device identical on every slide, speaker
notes from NOTES. Define the palette, fonts and component recipes once in your code and reuse them
for every slide so nothing drifts.

### Step 6: Check
Run the checklist in `pptx-translation.md` §5. Render the slides to images if the tool can and
look at each one; at least check overflow, contrast, leftovers and data programmatically. Fix and
rebuild until it passes. Show the user preview images of the slides (or a contact sheet) if you
could render them.

### Step 7: Iterate
The user can say "redo slide 7", "bigger titles everywhere", or "try a darker theme". Edit the
spec or the style guide, regenerate only the art that changed, and rebuild.

### Step 8: Deliver
Offer the .pptx as a download, named after the deck title. Say which fonts it uses and their
fallbacks (and that any non-standard font must be installed to look as designed). If any
slide still has an art placeholder, list those slides. Offer a PDF export too if the tool can make one.

## Known failure modes
- Generic template look (white slide, title + bullets, blue default shapes). Every slide needs
  its ground, its hero visual, the component kit and the signature device.
- Text baked into generated images (garbled labels, fake captions). Art is text-free; every word
  is a native text box.
- Text spilling out of boxes, because auto-fit doesn't apply until the file is edited. Size boxes
  for their text and cut words.
- Default theme styling leaking in: drop shadows on cards, blue table styles, dark outlines. Set
  every style explicitly.
- Dark text on dark fills (diagram nodes, table headers, bands over photos).
- Fonts that don't exist on the viewer's machine silently replaced. Pick installed fonts and name
  fallbacks; set the East Asian font for CJK text.
- Bar charts in reverse order; series colors not matching the guide.
- Signature device drifting (position, size, emblem). Define it once, place it identically.
- Font drift inside a series. Reuse the same role definitions for every series slide.
- Invented or unattributed closing quotes. Only real, attributed quotes go in quotation marks.
- Whole slides inserted as one picture. That defeats the point of a PPTX; only the art layer is images.
