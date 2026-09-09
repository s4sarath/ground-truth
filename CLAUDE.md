# Ground Truth Blog Standard

This repository publishes Ground Truth, an MkDocs + Material technical blog. This file is mandatory guidance for every new post and revision. `AGENTS.md` contains the same non-negotiable rules in a compact form; when guidance differs, use the stricter interpretation.

## Non-negotiable writing rules

- Write a cohesive technical story, not a report, changelog, tutorial, or listicle.
- Begin with the practical problem or conclusion, then progress from a simple mental model to evidence and implementation detail.
- Use descriptive, claim-led headings. Do **not** use `Part 1`, `Part 2`, or headings that merely describe document position.
- Keep paragraphs short and purposeful. One paragraph should normally carry one idea.
- Define technical terms before relying on them. Prefer direct, precise language over hype, filler, or unexplained acronyms.
- Separate verified facts, measurements, and interpretations. State the source and scope of a measurement; never present a single observed run as a universal ranking.
- State comparison boundaries early. If systems, endpoints, settings, workloads, or environments differ, say so where the comparison appears.
- Retain only details that advance the reader’s understanding. A precise detail is useful; a pile of implementation trivia is not.

## Scan-first emphasis

Readers must be able to find the article’s important evidence quickly.

- Bold **load-bearing numbers, durations, counts, limits, costs, sample sizes, paths, and outcomes** when they support the argument: for example, **25 tools**, **70,907 paths**, **22.60 seconds**, or **wrong directory**.
- Bold the key conclusion of a paragraph when it is easy to miss, but never bold a whole paragraph or several consecutive sentences.
- In comparison tables, bold the values or outcome that a reader must notice. Do not use bold merely as decoration.
- Do not over-emphasize routine code, names, or every number. Bold should create a useful skim layer, not visual noise.

## Structure and evidence

1. Open with the reader’s problem and the article’s central claim.
2. Establish the mental model with the smallest useful example.
3. Explain the system or investigation in focused sections.
4. Present evidence beside the specific claim it supports.
5. End with practical principles or takeaways that are earned by the evidence.
6. Include a `## References` section with direct, authoritative sources for systems, papers, and specifications used in the post.

- Prefer a labelled table when comparing more than two dimensions.
- Every chart or diagram needs a descriptive nearby heading, meaningful alt text, labelled units where applicable, and a clear statement of its measurement scope.
- Use code blocks only when the exact code, configuration, or output is materially useful. Always tag the fence language.
- Use admonitions sparingly for genuine caveats, methodology limitations, corrections, or safety boundaries.

## Visual and interaction standard

The site should feel calm, precise, readable, and editorial—not card-heavy or dashboard-like.

- Preserve the established light theme as the default, with the reader-controlled Light/Dark theme toggle.
- Use the existing system font stack and typography tokens. Keep headings strong but compact; do not introduce oversized or excessively bold headings.
- Maintain a generous but balanced reading rhythm. Remove accidental blank space, but do not compress distinct ideas together.
- Use the site’s creamy light neutral background, restrained ink palette, and subtle violet borders already established in the theme.
- Every diagram, chart, code-like trace panel, or contained explanatory box must have a clear title/caption and a visible, light violet boundary. Tables need clear row and column separation.
- Use visuals only when they make a relationship, sequence, mechanism, or comparison easier to understand. Preserve natural media proportions and avoid gratuitous cards, gradients, shadows, and decorative motion.
- Do not imitate another company’s trademarks, copy, images, or exact layouts. Use external design references only as high-level inspiration.
- Keep desktop, tablet, and mobile layouts readable. Avoid overflow, overlapping labels, unreadably small annotations, and excessive media height.
- Ensure meaningful alt text, semantic heading order, keyboard-visible controls, and sufficient contrast.

## File organization and release checks

- Store each post in `docs/<post-slug>/` and its assets in that post’s `images/` directory.
- Add new posts to `mkdocs.yml` navigation and the homepage card list.
- Verify links, image paths, captions, table rendering, theme behavior, and responsive layout after substantive changes.
- Run `mkdocs build --strict` before handing off any blog change.
- Cross-posts must preserve the Ground Truth article as canonical and replace local asset paths with their published URLs.
