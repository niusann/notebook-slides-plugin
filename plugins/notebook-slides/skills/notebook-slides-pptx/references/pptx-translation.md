# From design to a real PPTX

NotebookLM decks are flat images. Here the same design must survive as an editable PowerPoint
file: the user can click any word and change it, recolor a chart, move a card. This file says how
each design idea becomes PowerPoint objects, how to prompt for the art, and what to check.

Use whatever PPTX library your code tool has (python-pptx, PptxGenJS, …). These rules don't
depend on the library.

## 1. The layer model

Every slide is built from back to front:

1. **Ground**: the slide background as a solid fill, or one full-bleed texture/art image.
2. **Art**: text-free pictures (portraits, specimens, scenes, props, emblems), placed and cropped.
   Optional dark/light overlay rectangles (with transparency) to keep text readable over photos.
3. **Structure**: native shapes: panels, cards, bands, rules, frames, diagram nodes, connectors.
4. **Data**: native charts and tables.
5. **Text**: native text boxes, every string from the spec, styled by role.
6. **Signature device**: the same objects (or the same image file) at the same position on every slide.

**Native first.** If it's text, a number, a line, a box, a chart, a table, an arrow or a simple
icon, it is a native object. Only things that need painting or photography (people, places,
objects, textures, scenes, emblems) are images. If an image would need words on it, the words are
a native text box on top.

## 2. Translating the design DNA

| Design idea | Build it as |
|---|---|
| Hero visual: mechanism, process, comparison, structure | Native diagram: shapes as nodes (each label inside its shape), connectors with arrowheads, grouped |
| Hero visual: person, place, object, specimen, scene | Art image, cropped to fill its box, plus native annotation |
| Callouts / leader lines / zoom circles on an image | Native thin lines (0.75–1.25 pt), small circles or dots, label text boxes; a zoom circle is a circular-cropped copy of the image with a native ring |
| Content card | Rectangle or rounded rectangle, surface fill, hairline outline in the rule color or none, **no shadow** unless the kit says so; padding ≈ 1.5–2% of slide width |
| Quote box | Card + accent bar (thin rectangle) on one edge or large native quote marks; italic quote text; attribution as a separate smaller text box |
| Big stat | One large number text box (≈ 54–80 pt, display face, accent color) + a short label under it |
| Chart | Native chart with data written in the spec; series colors from the palette in the guide's order; no 3D, no default gradients, light or no gridlines, direct data labels when there are ≤ 8 values |
| Table | Native table with the default table style overridden: header fill from the palette, header text on-dark color, thin bottom rules only (no box grid), optional zebra in the surface color |
| Timeline | A native rule with dots/ticks, date labels and short event text boxes; the accent marks the turning point |
| Annotated map | Map as art (text-free), native pins, arrows and place labels on top |
| Section divider | Full-bleed ground or art + one large native title + short native intro line |
| Signature device | The same native shapes or the same image file, same size and position on every slide (copy it, never redraw it differently) |
| Texture (paper, grid, topo, blueprint) | One full-bleed text-free image used as background, kept low-contrast; or a native pattern (thin lines) if no images are available |
| Mixed media | Art layer + native annotation layer, never text baked into the art |

## 3. Art prompts (for the image generation tool)

Start every art prompt with this block, then the style guide's IMAGERY and PALETTE lines, then the
ART entry from the spec:

```text
You create ONE image to be placed inside a presentation slide. Editable text and diagrams will be
added on top later, so the image itself must contain NO text of any kind: no letters, words,
numbers, labels, captions, signage, logos, watermarks, signatures, or text-like scribbles. Paper
props (letters, maps, ledgers) may show only blurred, illegible marks.
- Follow the IMAGERY style and PALETTE exactly; keep colors within the palette's hues.
- Composition: {framing}. Leave clean, low-detail empty space at {where}, because text will sit there.
- Aspect ratio {w:h} to match its box on the slide ({full-bleed 16:9 | portrait | square}).
- Background: {transparent / plain {color} for easy cutout | full scene}.
- Premium editorial quality: one clear subject, controlled lighting, no clip-art, no stock-photo
  look, no frames or borders unless asked, no UI chrome.
```

- Generate each picture at the aspect ratio of its box so cropping stays small.
- Keep the deck's picture style identical: after the first approved art image, attach it as a style
  reference for the rest ("match this rendering style and palette; new subject").
- The user's own images are always preferred over generated ones when they show the real thing.
- **If the generated images can't be used in the code tool** (no file access to them), don't stall:
  build the slide with its art box as a placeholder (a rectangle in the surface color with a
  hairline outline and, if possible, a native icon), put the art prompt in the speaker notes, and
  tell the user which slides need a picture inserted. Ask them to upload the images if they want
  you to place them.

## 4. Build rules

Learned from test builds. Each one fixes a common way generated PPTX files look cheap or break.

**Canvas**
- 16:9 at 13.333 × 7.5 in (12192000 × 6858000 EMU). Start from the blank layout; no empty
  placeholders left on any slide ("Click to add title" boxes are a defect).
- Positions come from the spec in % of the slide. Keep everything inside the margins except
  full-bleed grounds, art and bands that are meant to touch the edge.

**Text**
- Set font name, size, color, bold/italic **on every run** explicitly; don't rely on theme
  defaults. For CJK text also set the East Asian font of the run (`<a:ea typeface=…>`), or the
  characters fall back to a random system font.
- Text box insets 0 (or the kit's padding inside cards), word wrap on.
- **Don't count on auto-fit.** "Shrink text on overflow" isn't recalculated when the file opens,
  so text that's too long just spills out. Size each box for its text at the kit's point size (the
  fit check in `planner.md`), and cut words if it doesn't fit.
- All-caps kickers via the font's caps setting with letter-spacing, so the source text stays normal.
- Bullets as real paragraph bullets or a hanging-indent glyph, ≤ 4 per box, with space after each.
- Text on a dark fill or photo uses the palette's light color. Check every node, header and band
  for this; dark-on-dark labels are a common miss.
- One string per text box per role; title, body, quote and attribution are separate boxes so each
  stays editable and positioned.

**Shapes**
- New shapes inherit the theme's style: a blue fill, a dark outline and often a **drop shadow**.
  Set fill and outline explicitly on every shape and remove the inherited shadow/style, unless the
  kit asks for one.
- Corner radius is small and consistent (the kit's value); don't mix sharp and rounded cards.
- Connectors: set color, weight and arrowhead explicitly; dashed for weak or indirect links.
- Group the parts of one diagram or one card so they move together.

**Charts**
- Native chart type that fits the data: bar for ranking, column for few categories over time, line
  for trends, stacked only for parts of a whole, doughnut only for ≤ 5 parts.
- Set every series/point color from the palette, the chart font to the body/caption face, legend
  at bottom or removed when there is one series, axis lines hairline or off.
- Horizontal bar charts draw categories bottom-up by default. Reverse the category axis so they read
  top-down in the order written in the spec.
- Number format matches the spec (%, thousands separators, units).

**Tables**
- The default table style (blue header, banded rows) never ships. Override header fill, banding,
  borders and every cell's font.
- Column widths set on purpose (labels narrow, descriptions wide); row height fits one or two lines.

**Images**
- Crop to fill the box. Never stretch. Circular crops for portraits/zoom circles if the kit says so.
- Overlays for readability: a rectangle in the ground or ink color at 40–70% opacity between photo and text.
- Alt text on every picture (what it shows).

**Deck**
- Speaker notes from each spec's NOTES (sources for quotes and numbers go here).
- Slide numbers only if the style guide includes them, in the footer zone.
- File name = deck title, `.pptx`.

## 5. Check before delivering

Render the finished file to images if the code tool can (e.g. LibreOffice headless → PDF →
PNG) and look at every slide; LibreOffice substitutes missing fonts, so judge layout, not exact
typefaces. Also check the file programmatically. For each slide:

- Every string from the spec is present once, spelled exactly; no spec words (role names, font
  names, hex codes) appear.
- No text spills out of its box or card, overlaps another element, or runs off the slide.
- Text contrast is fine everywhere, including labels on dark nodes and text over photos.
- No leftover placeholders, default blue shapes, theme shadows or default table styling.
- Chart values and labels match the spec; bar order reads top-down; diagram labels sit on the right
  nodes and arrows point the right way.
- The signature device is identical in shape, size and position on every slide; title zone and
  margins are the same on every content slide; series slides share one layout.
- Every object is still editable: no slide is one flattened picture, no text inside images.

Fix what fails, rebuild, and re-check only the affected slides. Mention what you couldn't check
(e.g. no renderer available) when you deliver.
