# Blog Writing Standard

This directory is the staging ground for blog posts before publishing. Primary platform is **Ground Truth**, a self-hosted MkDocs + Material site (`mkdocs.yml`, `docs/`, deployed to GitHub Pages via GitHub Actions) — canonical, full control over Markdown/images with no lossy web-editor round-trip. Cross-post to **dev.to** with its canonical URL field pointed back at the live Ground Truth post URL. Every post lives as plain Markdown under `docs/<post-slug>/`, written to build cleanly with `mkdocs build --strict` and to paste into dev.to with minimal rework (swap local `images/...` paths for their live GitHub Pages URLs, since they're already publicly hosted once Ground Truth is deployed).

## Voice and structure

These posts are hands-on technical deep-dives (harness tracing, source-level investigation), not tutorials or listicles. Follow the shape already proven across the pi/dsh/opencode series:

- **Open with a one-paragraph context section**: what's being investigated and why, linking back to the prior post in a series if there is one.
- **Numbered/titled parts (`## Part N: ...`)**, not a flat wall of prose. Each part earns its own heading only if it's a distinct phase of the investigation (install, config, trace instrumentation, findings, comparison).
- **Show real artifacts, not paraphrases**: actual config snippets, actual command output, actual trace/log excerpts. If a number or quote appears in the post, it came from a real file or terminal output, not from memory.
- **Distinguish verified facts from inference, explicitly.** If something is proven (a direct query, a byte-for-byte comparison), say so. If it's a reasonable hypothesis not yet checked, label it as such — don't blur the two. This distinction is itself part of the content's value; readers trust posts more when the author shows their proof, not just their conclusion.
- **Correct yourself in the text when an earlier assumption turns out wrong**, rather than quietly fixing it. A visible correction ("my initial assumption was X; checking the actual data showed Y instead") is more credible than airbrushed certainty, and it's honest about how real investigation works.
- **Comparison tables** whenever contrasting two or more systems/approaches — a table beats three paragraphs of "unlike X, Y does..." prose.
- **Close with a short takeaways section and a one-line teaser for what's next**, if this is part of a series.

## Visual standard: colorful, well-typeset, image-rich

Both Ground Truth (via its own theme CSS) and dev.to (platform-controlled) constrain fonts/theme to different degrees — so "colorful and good fonts" is achieved through the handful of levers actually available on each:

- **Every post needs a custom cover image.** Design or generate something on-theme (terminal/code aesthetic fits this series) — don't publish without one.
- **Use inline images and diagrams at key moments**, not just a cover image. A step-by-step trace or an architecture comparison is a natural fit for a diagram. Screenshots of real terminal output are also fair game where they add more than a code block would. Two distinct diagram jobs, two distinct tools — don't force either into the wrong shape:
  - **Quantitative charts** (token costs, tool-call counts, any measured comparison) → use the `dataviz` skill's method and validated categorical palette. These stay clean/technical — that rigor is the point.
  - **Flow, architecture, and conceptual illustrations** (the request/response loop, how a system is structured, comparing two mechanisms side by side) → use the **hand-drawn explainer style** documented below. Don't default to plain rectangles-and-arrows technical diagrams for these; the sketch style is what makes them inviting rather than clinical.
- **Tag every code fence with its language** (` ```bash `, ` ```json `, ` ```ts `) — this is the single biggest lever for visual "color" in a technical post, since both platforms syntax-highlight fenced code automatically. Never use a bare ` ``` ` fence for real code/config/output.
- **Use blockquotes as callouts** for asides worth visually separating — a caveat, a correction, a "worth flagging" aside. Both platforms render blockquotes with a colored left border by default, so this is free visual structure, not just semantic markup. On Ground Truth specifically, prefer Material's admonition blocks (`!!! note`, `!!! warning`, `!!! danger`, `!!! tip`) over plain blockquotes when the callout has a clear category — they render with the site's brand-tuned colors (see `docs/stylesheets/extra.css`).
- **One relevant emoji per major section heading is fine for scannability** (⚙️ for setup, 🔍 for findings, 📊 for comparisons) — sparing, not decorative on every line. Skip it if it feels forced.
- **Bold the load-bearing numbers and findings**, not whole sentences. A reader skimming should be able to catch the key facts (token counts, character counts, call counts) from bolded text alone.
- Prefer **tables over bullet lists** for anything with more than two comparable dimensions (tool counts, token costs, storage formats across harnesses) — bullets read as flat, tables read as structured and scannable.

## Diagram style: hand-drawn flow / architecture illustrations

Reference genre: Excalidraw-style ML/systems explainer diagrams — rounded sketch-style boxes, a marker/handwriting font, colored lanes, side-by-side comparison panels, and a bold one-line takeaway sentence framing the whole diagram. Distinct from the `dataviz`-skill charts referenced above; this is for *explaining a mechanism*, not *plotting a measurement*.

**Font**: [Kalam](https://fonts.google.com/specimen/Kalam) (Google Font, weights 400/700) — closest open match to the marker-style handwriting font in the reference genre. Embed the same way as the site's `Space Grotesk` heading font:
```
@import url("https://fonts.googleapis.com/css2?family=Kalam:wght@400;700&display=swap");
```
Never use a plain sans-serif for these diagrams — the handwriting font is what signals "friendly explainer" instead of "formal spec diagram." Body/label text can drop to a plain sans at very small sizes only if Kalam becomes illegible; prefer keeping Kalam everywhere in the diagram if it stays readable.

**Background**: a breezy, barely-tinted lavender-white — **not** the cream/yellow of the reference genre (explicitly rejected). Use `#f6f4fb` as the diagram canvas.

**Palette** — breezy and purple-led, but multi-hue like the reference (one hue per concept/role, reused consistently across a diagram, never cycled arbitrarily):

| Role | Stroke | Fill (soft tint) | Use for |
|---|---|---|---|
| Primary / signature | `#8b7fe8` (purple) | `#ece8fa` | The lead concept in a diagram — whatever the headline sentence is about |
| Secondary | `#4f9bd6` (blue) | `#e6f1fb` | A supporting/contrasting concept |
| Tertiary | `#3fae87` (green) | `#e5f6ef` | A third distinct concept, or a "this is the good/efficient path" signal |
| Accent / highlight | `#e8935a` (warm coral) | `#fdefe3` | Sparing use only — one emphasized element per diagram, not a general-purpose fourth color |
| Text | `#2e2a3d` (warm dark plum) | — | All labels and body text. **Never pure black** — it clashes with the soft palette. |
| Muted text / captions | `#6b6580` | — | Secondary annotations, small print |

Connector lines and arrows: colored to match whichever hue they're leaving or entering (a purple box's outgoing arrow is purple-ish, not a flat neutral gray) — this is part of what makes the reference genre read as coherent rather than a generic flowchart.

**Structural grammar** (borrow this shape, don't reinvent per diagram):

1. **Bold one-line headline at the top** stating the actual insight, not a generic label. ("Causal masking is why only K and V are worth keeping" — not "Attention Diagram.") This is the single most important element; write it last, after you know what the diagram proves.
2. **Rounded boxes** (corner radius ~10-14px), soft fill + colored stroke per the palette above, one hue per role, consistent across the whole diagram.
3. **Optional left-side lane labels** when the diagram has grouped rows (e.g., "Query lane" / "Key and value lane" in the reference) — a plain-text label to the left of each horizontal group, not inside a box.
4. **Optional comparison panel**: an outer rounded container split into 2+ colored sub-panels side by side, each with a short heading and a couple of bullet lines — the go-to shape for "here's mechanism A vs. mechanism B" content.
5. **Bold one-line takeaway caption at the bottom**, restating the headline's insight in different words — bookend the diagram, don't just let it trail off after the last box.

**Implementation note**: the reference genre's literal wobbly/imperfect line texture comes from a hand-drawn rendering pass (Excalidraw itself, or the `rough.js` library, which perturbs straight SVG paths into a sketchy stroke). That's a heavier tool dependency than the clean-SVG generation already used for the site's charts. Default to **clean rounded rects + the Kalam font + this palette** — that alone gets most of the "friendly explainer" feeling without a new dependency. Only reach for `rough.js` (or hand-jittering bezier control points) if a specific diagram genuinely needs the literal hand-drawn wobble and the clean-rect version reads as too sterile.

## Cross-posting mechanics

1. Publish first on **Ground Truth** (`https://s4sarath.github.io/ground-truth/...`, or the custom domain once mapped). That URL is canonical.
2. Copy the identical Markdown to dev.to — replace local `images/...` paths with the live Ground Truth URLs for the same files (already publicly hosted, no re-upload needed).
3. On dev.to, set the canonical URL field to the live Ground Truth post URL before publishing.
4. Tags: dev.to has its own tag system — set 3-5 relevant tags there for discovery. (Ground Truth's own nav/index entry, per "File organization" below, is the equivalent for the canonical site.)

## File organization

- One folder per post under `docs/`, named for the topic (not the date) — e.g. `docs/harness-agents-deep-dive/`, not `docs/2026-08-26-post/`.
- Keep source images/diagrams for a post inside that same folder's `images/` subfolder so assets don't get orphaned or ambiguous across posts.
- Every new post needs: the post added to `nav:` in `mkdocs.yml`, and a card added to `docs/index.md`'s grid-cards block (see the existing post's card for the pattern).
- Draft here first; run `mkdocs build --strict` locally (or `mkdocs serve` to preview) before pushing, so this directory stays the single source of truth and nothing broken ships.
