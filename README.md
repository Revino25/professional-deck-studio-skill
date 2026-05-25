# Professional Deck Studio Skill

Codex skill for creating, reviewing, and improving professional decks, consulting-style presentations, pitch decks, and executive decks.

## What It Includes

- Integrated full McKinsey-style deck content methodology.
- Dependency bootstrap for `huashu-design` visual deck workflow.
- Dependency bootstrap for `generate-image` image generation workflow.
- Consulting-neutral default visual direction.

## Install

After this repository is available on GitHub:

```bash
npx skills add https://github.com/<owner>/professional-deck-studio-skill
```

If your installer expects a specific path, install the skill folder:

```bash
npx skills add https://github.com/<owner>/professional-deck-studio-skill/tree/main/professional-deck-studio
```

## Skill Folder

The installable skill is in:

```text
professional-deck-studio/
```

## Optional Dependencies

For full slide production and image generation capabilities, users should also have:

- `huashu-design`
- `generate-image`
- `OPENROUTER_API_KEY` configured when generating images

The skill includes bootstrap instructions for those dependencies.
