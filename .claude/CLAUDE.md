# Ascend Deck System — Claude Code Instructions

## What this repo is

An HTML/CSS deck system for Ascend. Produces brand-correct presentation decks from plain-language prompts. Output: self-contained HTML → Chrome → Cmd+P → PDF.

## Files

| File | Purpose |
|---|---|
| `ascend-deck-template.html` | Starter kit: 30 slide types with [placeholders]. Duplicate to create new decks. |
| `ascend-deck.css` | Slide system. 100% tokenized. Shared by all decks. Do not edit unless changing the system. |
| `brand.css` | Design tokens (colors, type, spacing). Single source of truth. Font paths → `Fonts/`. |
| `ascend-deck-blocks.md` | Reusable content blocks. Pre-written slides for sales, partnership, investor, webinar decks. |
| `ASCEND_DECK_GUIDE.md` | Full technical reference: 30 slide types, `.md` input format, parsing rules, density limits, content budget validation, copy fidelity protocol. |
| `DECK_QUICK_START.md` | Operator guide: how to ask for a deck, reference prompts, block checklist explanation. |
| `decks/` | Output folder for production decks. |

## When asked to build a deck

1. **Read** `ASCEND_DECK_GUIDE.md` thoroughly — it contains the input format, all 30 slide types, density limits, content budget validation, and copy fidelity rules.
2. **Read** `ascend-deck-blocks.md` — present matching blocks as a Part A checklist. Ask only for deal-specific content (Part B).
3. **Follow the 4-step process** from the guide: Parse & Plan → Assemble HTML → Consistency Check → Visual QA.
4. **Content budget validation is mandatory** — calculate whether content fits BEFORE assembling. Do not assemble slides that exceed their content zone.
5. **Copy fidelity is absolute** — transcribe user content verbatim. Never paraphrase, rewrite, or "improve" the user's text. If it doesn't fit, report and wait.

## Rules (always-on)

- **Sentence case** everywhere. Only pills, tags, and mono labels are ALL CAPS.
- **FT System Mono** for data: numbers, pills, tags, step labels, stat pills.
- **FT System Grotesk** for narrative: headlines (Medium), body (Regular).
- **One idea per slide.** If a slide communicates more than one concept, split it.
- **Headlines are takeaways, not labels.** "Members save $127K in 6 months" not "Our Results". If a user gives a label, flag it but don't rewrite — ask first.
- **Max 18 slides** recommended. Warn if exceeded.
- **Auto-shrink** before splitting: ≤20px overflow → `data-autoshrink="1"`, 21-40px → `"2"`, >40px → split. Never auto-shrink cover, section-break, or closing.
- All colors and font-sizes from CSS tokens. Zero hardcoded values in HTML.
- All emails must use `<a href="mailto:...">`.

## Output location

Save new decks in `decks/` with the naming pattern: `ascend-[client]-[type].html` (e.g., `ascend-jet-mgmt-partnership.html`).
