Omar,

I took a different approach to the deck system than the PptxGenJS skill you built. Instead of improving `ops-ascend-pptx`, I built a parallel system in HTML/CSS. Here's what it is, why, and how they relate.

**What I built**

A complete HTML-based deck system for Ascend. You describe a deck in plain language, the system generates it as a self-contained HTML file, you open it in Chrome and Cmd+P to PDF.

```
ascend-deck-system/
├── HANDOFF_OMAR.md                           — This file — read first
├── DECK_QUICK_START.md                       — Operator guide: 4 reference prompts
├── ASCEND_DECK_GUIDE.md                      — Full reference (30 slide types)
├── ascend-deck-blocks.md                     — Reusable content blocks (26 blocks)
├── brand.css                                 — Design tokens (single source of truth)
├── ascend-deck.css                           — Slide system, 100% tokenized
├── ascend-deck-template.html                 — Starter kit (30 types + variants)
├── ascend-sales-deck.html                    — Production: sales deck (34 slides)
├── ascend-jet-mgmt-partnership.html          — Production: JET Management deck
├── ascend-webinar-travel-optimization.html   — Production: travel webinar
├── ascend-advanced-travel-hackers.html       — Production: travel hackers deck
├── ascend-case-study-blondish.html           — Production: Blondish case study
├── Fonts/                                    — FT System Trial (Grotesk + Mono)
├── Assets/                                   — Imagery, Headshots, Logos, Patterns, Cards
└── References/                               — Figma Slides PNGs + PDF references
```

**Why HTML instead of building on your PptxGenJS skill**

Your system has Claude write a bespoke JS build script every time someone asks for a deck. That script calls functions from `components.js`, runs via Node, and outputs `.pptx`. It works — the Bilt deck proves it. But the output varies because Claude improvises the script each time. Two identical requests can produce different layouts.

The HTML system uses a structured Markdown format as input. Every slide type has a fixed grammar (`## metrics`, `- value: X | label: Y`). Same input always produces same output. The tradeoff: the output is HTML/PDF, not editable `.pptx`.

**What this covers from your original brief**

| Your priority | Status |
|---|---|
| 1. Audit components (spacing, type, contrast, edge cases) | Done — 100% tokenized, density limits enforced pre-assembly, auto-shrink for edge cases |
| 2. Add templated layouts | 30 types built. Map, timeline, pricing, testimonials, before/after, matrix all covered. Missing: product screenshot mount |
| 3. Expand asset library | Structure ready (12 hero photos, patterns, logos). Adding more is production work |
| 4. Codify design tokens | Done — `brand.css` `:root` has every token. `ascend-deck.css` has 17 deck-specific variables. Zero hardcoded values |
| 5. Strengthen QA | Auto-shrink system built. See note below on programmatic QA |

**What your PptxGenJS skill still does better**

Editable `.pptx` output. If the recipient needs to modify slides in PowerPoint or Google Slides, HTML can't do that. Your skill is the right tool for those cases.

**How they can coexist**

Your skill for when the recipient needs to edit. This system for when the team needs to produce decks fast with consistent quality and zero dependencies. Both use the same brand tokens, same content blocks, same slide types — just different output formats.

**The operator experience**

Any team member opens Claude Code in the Slides folder, describes what they need (or copies one of the 4 reference prompts in the Quick Start), confirms a checklist of pre-loaded content blocks (your stats, cases, pricing — already in the system), and gets a deck. No Node, no LibreOffice, no ImageMagick. The Quick Start doc walks through everything.

**Already tested in production**

Chloe needed a partnership deck for JET Management. She shared a Notion page with the content, I prompted the system based on that, and it produced the full deck. She's already sent it out. The workflow was: Notion content → prompt → deck outline → assembled HTML → PDF → delivered. No iteration loops, no screenshot-and-fix cycles.

**What's not done (and why)**

- **Programmatic QA (screenshot + overflow detection):** Decided against implementing it for now. The operator always opens the deck in Chrome before exporting to PDF — that's the visual QA. The script adds value when you're producing decks at volume and can't eyeball each one. Ascend isn't there yet. The framework exists on the TCL side and can be ported in an afternoon if the volume justifies it later.
- **Product screenshot mount slide type:** Not built. Can be added following the same pattern as the other 27 types.
- **More hero photography and partner logos:** Production work, not system work. The asset pipeline is ready.

Everything is in `05-CreativeOps/Clients/Ascend/Brand Assets/Slides/`. The Quick Start is the entry point for anyone on the team.

Ramiro
