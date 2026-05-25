---
name: professional-deck-studio
description: Use when creating deck content, creating professional slides, reviewing deck storyline, reviewing slide aesthetics, or improving consulting-style presentations, pitch decks, and executive decks.
---

# Professional Deck Studio

Comprehensive workflow for professional decks. This skill contains the full McKinsey-style content methodology as a bundled reference and bootstraps visual/image dependencies when they are missing.

## Bundled Content Method

For content work, read `references/mckinsey-slide-craft-full.md`. It is the full integrated McKinsey Slide Craft method and is the source of truth for deck content, storyline, SCR, Pyramid Principle, action titles, evidence framing, and content QA.

## Dependency Bootstrap

`huashu-design` and `generate-image` are runtime dependencies for their corresponding work. Before using either dependency, check whether it is available in the current skill list or on disk. If a required dependency is missing, attempt this bootstrap first; continue with a reduced fallback only if install is impossible or the user declines approval.

### huashu-design

Use for slide visuals, HTML-first deck production, aesthetic QA, export guidance, and render verification.

1. If `huashu-design` is available as a skill, use it normally.
2. If it is not available, check common local sources:
   - `~/.agents/skills/huashu-design`
   - `~/.codex/skills/huashu-design`
   - any user-provided local `huashu-design` skill folder
3. If a local source exists, ask for approval to install or symlink it into `~/.codex/skills/huashu-design` before creating or reviewing visual slides.
4. If no local source exists, ask the user to provide a local path or install source. Do not invent a remote source.

### generate-image

Use for non-technical visual assets such as hero images, conceptual illustrations, and general-purpose infographic imagery.

1. If `generate-image` is available as a skill, use it normally.
2. If it is not available, check common local sources:
   - `~/.codex/skills/generate-image`
   - `~/.agents/skills/generate-image`
   - any user-provided local `generate-image` skill folder
3. If a local source exists, ask for approval to install or symlink it into `~/.codex/skills/generate-image` before generating or editing images.
4. If no local source exists, ask the user to provide a local path or install source. Do not invent a remote source.
5. Before generating images, check for `OPENROUTER_API_KEY` in the environment or a nearby `.env`. If missing, explain that image generation needs an OpenRouter API key.

Default visual direction is consulting-neutral. Do not use PHE style, PHE templates, or PHE assets unless the user explicitly asks for PHE.

## Mode Router

Choose exactly one primary mode from the user's request. If the user asks for multiple outcomes, run the modes in this order: content before slides, review before improvement.

| Mode | Use When | Output |
| --- | --- | --- |
| Create Content | User wants the deck narrative, outline, storyline, ghost deck, slide messages, or content draft | Structured deck content only; no visual slide files |
| Create Slides | User wants visual slides, a deck file, HTML deck, PDF/PPTX export, or slides from approved content/outline | HTML-first slide deck; PDF/PPTX only if requested |
| Review Content | User asks to review the story, logic, content, title quality, evidence, or executive narrative | Content findings and concrete rewrites |
| Review Slides | User asks to review aesthetics, layout, visual quality, typography, spacing, or polish | Aesthetic findings and prioritized fixes |
| Improve Content | User wants better storyline, action titles, executive summary, evidence framing, or ordering | Revised content with before/after where useful |
| Improve Slides | User wants visual cleanup, redesign, consistency, image treatment, infographic treatment, or export readiness | Updated visual plan or edited deck output |

## Create Content

Read and apply `references/mckinsey-slide-craft-full.md`.

1. Clarify only high-impact missing details: audience, decision the deck should drive, page count, presentation context, available evidence, constraints, and language.
2. Build a ghost deck before detailed slides. Use SCR and Pyramid Principle.
3. For each slide, specify:
   - action title as a complete sentence
   - one message the slide proves
   - suggested exhibit type
   - required evidence/source
   - speaker intent
4. Output structured deck content. Do not create visual slide files in this mode unless the user explicitly switches to Create Slides.

## Create Slides

Use `huashu-design`; run Dependency Bootstrap first if it is missing.

1. Require approved content, an outline, an existing draft, or enough source material to create slide content first.
2. Default to HTML-first: the HTML deck is the source; PDF/PPTX are derivatives only when requested.
3. If the deck has 5 or more slides, create 2 visually distinct showcase slides first to lock the visual grammar before producing the full deck.
4. Keep the default design consulting-neutral: restrained palette, strong grid, executive typography, clear data exhibits, purposeful whitespace, and minimal decoration.
5. If editable PPTX is requested, follow the `huashu-design` editable-PPTX constraints from the first line of HTML.
6. Use `generate-image` only for non-technical images or general-purpose infographic visuals that materially improve the deck. Run Dependency Bootstrap first if it is missing.

## Review Content

Read and apply `references/mckinsey-slide-craft-full.md`. Evaluate:

- Do action titles tell a complete story when read in sequence?
- Does the deck lead with the answer or recommendation?
- Is the SCR arc clear?
- Does each slide make exactly one point?
- Does every exhibit support the title's claim?
- Is the executive summary a true summary of findings, not an agenda?
- Is the evidence credible, current enough for the use case, and explicit about the "so what"?

Report structural issues first, then slide-level issues, then polish. Rewrite weak titles instead of only describing the problem.

## Review Slides

Use `huashu-design`; run Dependency Bootstrap first if it is missing. Evaluate:

- visual hierarchy, typography, spacing, alignment, and composition
- consistency of color, title treatment, footers, page numbers, charts, and image treatment
- data exhibit clarity and whether the visual draws attention to the main insight
- anti-AI-slop issues: generic gradients, emoji decoration, fake stats, over-carded layouts, decorative SVG imagery, filler icons, and visual clutter
- overflow, unreadable text, console errors, blank renders, and export readiness

Prioritize issues that affect executive comprehension before minor polish.

## Improve Modes

For improvement requests, separate findings and edits into `Content` and `Slides/Aesthetic`.

- Improve Content: rewrite action titles, reorder slides, sharpen executive summary, split or merge overloaded slides, and strengthen evidence framing.
- Improve Slides: establish or repair visual grammar, improve hierarchy, simplify crowded slides, align charts/tables, improve image use, and prepare output for requested export format.

When a change is important, show before/after pairs for titles, ordering, or visual direction.

## QA Gates

Before calling the work complete:

- Content QA: action-title story passes, one-message-per-slide passes, executive summary is recommendation-led, evidence supports claims, and every slide answers "so what?"
- Slide QA: no obvious AI slop, no incoherent overlap, text is readable, visual hierarchy is clear, and design is consistent.
- HTML QA: render the deck, capture screenshots, and check console errors when producing slide files.
- Export QA: export PDF/PPTX only if requested; for editable PPTX, verify the deck followed editable constraints before export.

## Image Use

Use `generate-image` for:

- hero imagery
- conceptual images
- polished general-purpose presentation visuals
- non-technical infographic imagery
- image edits

Do not use `generate-image` for technical diagrams, process flowcharts, system architecture, scientific schematics, or charts requiring exact data. Use HTML, charting, or a more specific diagram skill instead.

## Common Defaults

- Language follows the user's prompt.
- If no format is specified for visual slides, produce HTML-first.
- If no visual brand is specified, use consulting-neutral.
- If the user asks for content only, do not create slide files.
- If the user asks for slides from weak or missing content, create or request approval for content first.
