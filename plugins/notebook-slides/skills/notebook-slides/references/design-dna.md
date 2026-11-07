# Design DNA: why NotebookLM decks look premium

Core design principles behind editorial-grade, image-rendered slide decks. Every deck must invent
its own art direction from scratch for its specific content (see `planner.md` step 2).

1. **One focused, reframed angle.** A deck is a narrow selection with a point of view, never a
   summary of everything: isolating one core mechanism from a large research corpus, reframing
   narrative material as an applied decision framework, or asking one recurring question across
   competing perspectives. The title states the reframe.
2. **The art direction comes from the angle and the genre of the content.** Four theme families
   define the visual grammar (invent a fresh, topic-native color palette, surface texture, and
   motif set for every deck while following these structural and media grammars):
   - *Immersive world* (history, literature, biography, narrative): a physical world with period or
     contextual props (archival dossier, illuminated manuscript, investigation board, situation-room
     briefing, cultural artifact). Grammar: choose either a **dark atmospheric polarity** (a deep,
     low-luminance ground drawn from the subject's world paired with warm or crisp high-luminance
     floating cards with `10–12px` radius, soft shadow, `~4%` internal padding, and low-opacity
     `~10–15%` geometric/network lines or architectural panels in the margins) OR a **tactile
     substrate polarity** (full-bleed aged paper, vellum, parchment, or fabric canvas with dark
     period ink and ornate or ruled frames). Render portraits and historical/narrative artifacts as
     ground-tinted monochrome/duotone engravings or period illustrations blending softly into the
     background (or set in framed panels), paired with fine metallic or ink line-engravings for
     emblems/seals. Pair a high-contrast transitional or old-style display serif (titles and huge
     ALL-CAPS profile names) with a clean neutral sans-serif (dossier bullets) and italic serif/sans
     for quotes preceded by a large accent open-quote glyph (`“`).
   - *Field/specimen editorial* (popular science, nature, hardware, product anatomy): airy warm
     field-journal or laboratory-clean ground with faint (`~10–15%`) topographic, contour, or
     schematic line art; crisp surface cards with soft shadows and a solid colored top tab bar
     encoding each thematic pillar or category. Combine macro photoreal subjects or 3D cutaway
     illustrations with thin technical vector overlays (dashed leader lines ending in dots,
     thin-bordered callout boxes, zoom circles) and small pen-and-ink or technical engravings in
     tables/cards. Book or editorial serif for centered `Hook: Clarifier` titles; neutral sans for
     lead paragraphs and bold run-in lead-ins (`The Mechanism:`, `The Evidence:`).
   - *Genre-native editorial* (business, leadership, strategy, how-to, playbooks): tactile
     architectural, newsprint, or studio paper ground (such as warm drafting stock covered
     edge-to-edge with a subtle uniform `1px` square engineering graph-paper grid or fine editorial
     ruling). Strictly flat 2D vector information graphics (funnels, exponential activation curves,
     seesaws, floor-plan schematics, concentric circles) using a 4-role editorial palette derived
     from the topic: deep primary ink + bold structural accent + neutral structural grey + a
     high-luminance marker/highlighter tint — zero stock photos or 3D shading. Heavy high-contrast
     editorial serif for left-aligned full-sentence claim titles and italic pull quotes; geometric
     sans-serif for bold ALL-CAPS diagram labels and attributions; high-contrast marker/highlighter
     swipes behind the decisive 3–6 words of each quote or output badge.
   - *Source-native technical* (research papers, benchmarks, engineering, clinical/AI/data): clean
     publication-grade canvas (warm scientific paper or crisp technical off-white) with delicate,
     low-opacity (`~15–18%`) domain-derived background linework in the corners (flowing
     neural/branch pathways, circuit traces, molecular lattices, or wave contours). One geometric
     sans-serif family across all weights: left-aligned bold title (`~5.5%` height) + 1–3-sentence
     regular subtitle (`~2.8%` height) stating the quantitative takeaway. Strict semantic color
     encoding across all charts and callouts (a high-salience focal accent for the proposed
     system/finding vs. a muted contrasting tone for prior SOTA/baseline), pairing crisp rounded
     chart cards (`10px` radius, `1px` border, direct bold value labels above bars) with stacked
     metric callout cards led by huge bold accent stats.
   - Modifier: *per-section style shifts* when the deck compares distinct worlds, eras or schools
     of thought. Each section borrows its subject's visual language while a locked layout skeleton
     and typography keep it one cohesive deck.
3. **One signature device on every slide.** A recurring visual anchor—such as a continuous connector
   line, a corner emblem, a fixed evaluative sidebar, a highlighter swipe, or subtle schematic
   contours—defined once with exact shape, color, and placement, and kept identical everywhere.
4. **Every content slide has one hero visual that *is* the argument.** Never decorative stock
   art: a balance scale for leverage, a seesaw for shifting trade-offs, a cross-section for a
   physical or operational mechanism, a funnel for filtering, or a fault line for structural tension.
5. **Mixed media where the family allows it.** Photoreal or engraved imagery combined with crisp
   vector annotation on top (leader lines, callout boxes, zoom circles, trajectory arrows, pinned notes).
6. **Reading deck, not keynote.** Title (a two-part hook, a series formula title, or a full-sentence
   claim) + a concise narrative paragraph + hero visual + one evidence component (attributed primary
   quote, chart with real numbers, comparison table, or structured callouts). Technical decks run
   denser; how-to decks use short claims paired with quotes or diagrams.
7. **A series formula drives the middle.** "Step 1–N", "Case 01–N", "<Concept> is ___.",
   "Mechanism: ___", or structured profiles. Every member of the series shares the same title
   pattern and layout skeleton. Pair "who/what" slides with "how" slides (profile/case → map,
   cross-section, schematic, or timeline) to build depth without repetition.
8. **A small, strict component kit.** Quote box, content card, callout, section divider, table,
   chart, and diagram nodes—using the exact same border weight, corner radius, shadow, padding, and
   type roles every time.
9. **Two typefaces, plus at most one utility face with a single job** (e.g. monospace for primary
   evidence or condensed caps for display labels). Italic for quotes.
10. **Restrained, topic-native palette with semantic meaning.** Invent a fresh palette from the
    subject's physical materials, era, or domain for every deck—never reuse default colors across
    topics. Define one ground, one card surface (with strong luminance contrast against the ground),
    one primary ink, one muted secondary ink, and 1–3 accents that encode meaning consistently (e.g.
    alert/conflict vs. alliance, baseline vs. proposed system, a luminous highlighter tint for key
    phrases, or one distinct accent per thematic pillar), and lock them to explicit HEX codes in the
    style guide.
11. **Generous outer safe margins (~6–7% of width), a clear grid, high contrast, one focal point per slide.**
12. **Narrative arc with an intent-matched ending.** Cover → framing → series/sections →
    synthesis (comparison matrix, timeline, concentric ripple diagram, or two-lens summary) →
    closing matched to the deck's intent: quote or emblem (narrative/history), reflective questions
    (ideas/philosophy), action checklist (how-to/strategy), or future directions + appendix (technical).
13. **The layout changes almost every slide; the visual language never does** (except deliberate
    per-section shifts, which lock the layout skeleton instead).

## Layout archetypes
Cover · framing question · roster grid · profile split (portrait + dossier card) · structured case card
(field list + focal illustration) · two-column compare / old-vs-new paradigm · comparison matrix ·
relationship/network diagram · process steps / cycle · step slide (claim title + diagram + quotes)
· annotated map · cross-section · schematic/floor plan · timeline · data chart + metric callouts ·
anatomy/zoom-callout figure · ripple/concentric diagram · section divider · full-bleed scene with
caption · triptych · action checklist · reflective questions · appendix table/chart · closing quote/emblem.
