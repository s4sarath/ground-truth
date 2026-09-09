# Technical Blog Editorial Standard

Use this checklist when creating or substantially revising posts in this repository. `CLAUDE.md` remains the repository's operational guide; this document defines the editorial bar.

## Purpose

Write technical articles that are useful to a practitioner who has not followed the investigation. The reader should understand the problem, mechanism, evidence, and practical consequence without needing to infer missing steps.

## Structure

1. Start with the conclusion and the problem being solved.
2. Build from a simple mental model to implementation detail.
3. Use descriptive sections with a logical progression; use numbered parts for substantial deep dives.
4. Put methodology and comparison boundaries near the beginning.
5. End with operational takeaways, not a vague summary.

## Evidence and technical accuracy

- Separate verified facts, measurements, and inferences.
- Name the source of measurements and state when comparisons are not apples-to-apples.
- Prefer a small, well-labelled table over unqualified numerical claims.
- Explain why a behavior happens in the system, not just what appeared on screen.
- Remove experiments, anecdotes, and implementation details that do not advance the reader's understanding.

## Language and readability

- Use direct, professional language and short paragraphs.
- Define a term before relying on it.
- Prefer concrete verbs and avoid hype, filler, and unexplained acronyms.
- Use code blocks only when the exact output or interface is materially helpful.

## Visual design and release

- Use the OpenAI Developers blog as the visual reference: light editorial canvas, restrained black typography, compact metadata, precise hairline borders, controlled whitespace, and sparing violet accents.
- Keep light as the default theme. A dark theme may be offered as a reader-controlled toggle, never as the automatic default.
- Do not introduce oversized display type, decorative gradients, or documentation-style sidebars on the homepage.

- Use visuals only when they clarify a relationship, sequence, or comparison.
- Give each chart a specific caption; label units and the scope of data.
- Protect reading comfort with readable body type, whitespace, and a clear content column.
- Verify internal links, images, navigation, and Markdown rendering.
- Run `mkdocs build --strict` before publishing.
