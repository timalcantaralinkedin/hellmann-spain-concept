---
name: design-review
description: Audit and improve the visual design, layout, and aesthetics of any finished or draft artifact — PDFs, Canva designs, web pages / HTML, slide decks (PPTX/Keynote), posters, social graphics, or exported images. Use this skill whenever the user wants design feedback, says something "looks off / amateur / unbalanced / cluttered / cramped", asks to "make it look better / more premium / more polished / cleaner", wants a design critique, or hands over a file and asks you to elevate its layout, typography, spacing, color, or overall craft. Diagnose specific problems first, then fix them — never restyle blindly.
license: Apache-2.0
---

# Design Review & Polish

A method for turning "this looks a bit off" into a concrete, fixable list — and then fixing it so the result reads as the work of a senior designer, not a template.

## Core principle: look before you touch

You cannot improve a design you have not actually seen rendered. Text source (HTML, a `.pptx` XML, a reportlab script) is not the design — the *rendered pixels* are. Always get eyes on the real output first.

- **PDF** → render pages to PNG and read them: `pdftoppm -png -r 150 file.pdf page` (or `pdf2image` in Python). View every page.
- **Web / HTML** → open in a real browser and screenshot at desktop **and** mobile widths. A layout that works at 1440px often breaks at 375px.
- **Canva** → use the Canva MCP tools: `get-design`, `get-design-pages`, and `get-design-content` to read structure, and `get-design-thumbnail` / `export-design` to see the actual rendering. Critique the export, not your assumption of it.
- **Slides (PPTX)** → render to images (LibreOffice `soffice --headless --convert-to pdf`, then `pdftoppm`) and review each slide.
- **Images** → read the file directly.

If you genuinely cannot render it, say so explicitly rather than guessing — a design verdict made blind is worthless.

## The audit: diagnose before you prescribe

Go through these seven lenses **in order**. For each, write down *specific* problems with locations ("the H2 on page 2 sits 4px from the image above it"), not vague verdicts ("typography could be better"). Specificity is the whole game — a designer's value is in naming the exact thing that's wrong.

1. **Hierarchy & focal point** — Within 3 seconds, is it obvious what to look at first, second, third? Is there exactly one clear focal point per view, or do five elements shout at once? Weak hierarchy is the #1 reason work reads as amateur.

2. **Typography** — Count the typefaces (2 is ideal, 3 is the ceiling). Check the type scale: sizes should step in a clear ratio (e.g. 1.25×–1.5×), not drift by 1–2px. Line length 45–75 characters for body. Line-height ~1.4–1.6 for body, tighter for big headlines. Hunt for orphans, widows, awkward mid-line wraps, and letter-spacing that's too loose on body or too tight on caps.

3. **Spacing & rhythm** — Is spacing on a consistent scale (4 / 8 / 16 / 24 / 32…), or arbitrary? Related things should be close, unrelated things far apart (proximity = grouping). Generous, *consistent* whitespace is the cheapest way to look premium. Cramped or random gaps are the cheapest way to look cheap.

4. **Alignment & grid** — Does everything snap to a shared grid and a small set of edges? Ragged left edges and "almost-aligned" elements are subconsciously read as sloppy. Optical alignment beats mathematical when they disagree (e.g. punctuation, icons).

5. **Color & contrast** — Is there a deliberate palette (one dominant, one or two accents, neutrals) or a random assortment? Accent color used sparingly for emphasis reads as confident; used everywhere it reads as noise. Verify text/background contrast meets **WCAG AA** (4.5:1 body, 3:1 large text) — this is correctness, not taste.

6. **Consistency** — Do buttons, cards, corner radii, shadows, icon weights, and capitalization follow one system, or does each instance reinvent itself? Inconsistency is the tell that no system exists underneath.

7. **Craft details** — The last 10% that separates good from premium: pixel-snapped borders, no overlapping elements, nothing clipped at the page edge, consistent image treatment (same aspect ratios / corner radii / overlays), real punctuation (curly quotes ' ' " ", en/em dashes – —, × not x), and aligned baselines. Sweat these.

## The fix: improve, don't redecorate

- **Fix root causes, not symptoms.** If three gaps are wrong, introduce a spacing scale and apply it — don't nudge three numbers.
- **Subtract before you add.** Most amateur designs are *too busy*. Removing a competing element, a third font, or a decorative flourish usually improves a piece more than adding anything. When tempted to add a graphic, first ask whether refining what's there gets you further.
- **Make one decision and propagate it.** Pick the type scale, the spacing unit, the radius, the accent — then apply each *everywhere*. Cohesion comes from repetition.
- **Preserve content and intent.** Don't rewrite copy or change meaning while improving layout unless asked. Don't swap the brand's identity for your taste.
- **Commit to a point of view.** Refined-minimal and bold-maximal both work; timid middle-ground doesn't. Decide which the artifact wants to be and execute it fully.

## Per-format handoff

After auditing, pick the right tool to actually produce the improved artifact:

- **Web / HTML / React / landing pages, posters as web** → read `../frontend-design/SKILL.md` for distinctive, non-generic implementation guidance, then edit the real code and re-screenshot to confirm.
- **Standalone visual art, single-page design-forward posters/covers, PNG or PDF art objects** → read `../canvas-design/SKILL.md` and use its philosophy + the bundled `canvas-fonts`.
- **PDF documents** (reports, brochures, multi-page) → build/edit with Python (`reportlab` for generation, `pypdf` for manipulation). The environment also ships a proprietary `pdf` skill — consult it in place if available. Always re-render the result to PNG and re-audit.
- **Canva designs** → use the Canva MCP `perform-editing-operations` (wrapped in `start-editing-transaction` / `commit-editing-transaction`) to change the live design, then re-export and re-audit. Use `comment-on-design` if the user wants feedback left in-place rather than edits made.
- **Slides (PPTX)** → use `python-pptx`; the environment ships a proprietary `pptx` skill — consult it in place if available.

## Output format

Lead with the diagnosis, then the changes. Use this structure:

```
## Design audit: [artifact]
**Overall read:** [one honest sentence — what it currently communicates]

### Top issues (most impactful first)
1. [Lens] — [specific problem + location] → [the fix]
2. ...

### What's already working
- [genuine strengths worth preserving]
```

Then make the fixes, re-render, and show the before/after. Cap the issue list at the ~5–8 that actually matter — a critique that flags everything flags nothing. Rank by impact on the viewer, not by ease of fixing.

## Brand fidelity

When the artifact belongs to a brand, the brand's existing tokens win over generic best practice. Before restyling, extract the brand's real colors, fonts, logo treatment, and tone from the source files and hold to them. If no brand system exists, propose a small one (palette + two fonts + spacing scale) and apply it consistently rather than improvising per element.
