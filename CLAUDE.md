# Blog Writing Standard

This directory is the staging ground for blog posts before publishing. Primary platform is **Hashnode** (canonical, own custom domain); cross-post to **dev.to** with its canonical URL field pointed back at the Hashnode post. Every post here is plain Markdown, written to paste into either editor with minimal rework.

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

Both Hashnode and dev.to control fonts/theme at the platform level, not per-post — so "colorful and good fonts" is achieved through the handful of levers an author actually has:

- **Every post needs a custom cover image.** Posts without one get deprioritized in Hashnode's feed algorithm and look bare everywhere. Design or generate something on-theme (terminal/code aesthetic fits this series) — don't publish without one.
- **Use inline images and diagrams at key moments**, not just a cover image. A step-by-step trace or an architecture comparison is a natural fit for a diagram (boxes/arrows for the request→LLM→tool→response loop, a side-by-side architecture sketch for the three-harness comparison). Screenshots of real terminal output are also fair game where they add more than a code block would (e.g., showing colored trace output). Generate these with the `dataviz` skill or a diagram tool when a table isn't the right shape for the information; don't force everything into prose.
- **Tag every code fence with its language** (` ```bash `, ` ```json `, ` ```ts `) — this is the single biggest lever for visual "color" in a technical post, since both platforms syntax-highlight fenced code automatically. Never use a bare ` ``` ` fence for real code/config/output.
- **Use blockquotes as callouts** for asides worth visually separating — a caveat, a correction, a "worth flagging" aside. Both platforms render blockquotes with a colored left border by default, so this is free visual structure, not just semantic markup.
- **One relevant emoji per major section heading is fine for scannability** (⚙️ for setup, 🔍 for findings, 📊 for comparisons) — sparing, not decorative on every line. Skip it if it feels forced.
- **Bold the load-bearing numbers and findings**, not whole sentences. A reader skimming should be able to catch the key facts (token counts, character counts, call counts) from bolded text alone.
- Prefer **tables over bullet lists** for anything with more than two comparable dimensions (tool counts, token costs, storage formats across harnesses) — bullets read as flat, tables read as structured and scannable.

## Cross-posting mechanics

1. Publish first on Hashnode. That URL is canonical.
2. Copy the identical Markdown to dev.to.
3. On dev.to, set the canonical URL field to the Hashnode post's URL before publishing.
4. Tags: use Hashnode's tagging for discovery there; dev.to has its own separate tag system, set both independently for each platform's algorithm.

## File organization

- One Markdown file per post, named for the topic (not the date) — e.g. `pi-harness-deep-dive.md`, not `2026-08-26-post.md`.
- Keep source images/diagrams for a post in a matching subfolder (`pi-harness-deep-dive/` for `pi-harness-deep-dive.md`'s images) so assets don't get orphaned or ambiguous across posts.
- Draft in this directory first; only copy into the Hashnode/dev.to editors once a post is ready, so this directory stays the single source of truth for the raw Markdown.
