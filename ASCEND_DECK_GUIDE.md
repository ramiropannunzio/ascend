# Ascend Deck System — Input Format Guide

> **Viewport:** 960×540 (16:9, Figma Slides equivalent)
> **Font:** FT System Trial (Grotesk) + FT System Mono
> **Output:** Self-contained HTML deck, on-brand, Chrome → Cmd+P → PDF
> **CSS:** `brand.css` (tokens) → `ascend-deck.css` (slide system). Both linked from the HTML `<head>`.
> **Contract:** `deck-token-contract v1.1` — Layer 1 constants (density, spacing, auto-shrink thresholds) + Layer 2 variables (type scale, colors, fonts) defined in `ascend-deck.css :root`.

---

## Prerequisites — Load Before Responding

**Fast path (most decks):** Read `ascend-deck-partials.html` (~8K tokens) instead of the full template. It contains 13 pre-assembled slides covering the most common patterns (cover, split-image, icon cards, steps, metrics, testimonials, pricing, agenda, CTA, closing). Only fall back to the full template for slide types not in partials.

1. `05-CreativeOps/Clients/Ascend/Brand/Slides/ascend-deck-partials.html` — **read first.** Pre-assembled HTML for 13 recurring slide patterns with [PLACEHOLDER] markers. Includes sprite sheet.
2. `05-CreativeOps/Clients/Ascend/Brand/Slides/ascend-deck-template.html` — full slide catalog (30+ types). Read only for slide types not covered by partials.
3. `05-CreativeOps/Clients/Ascend/Brand/Slides/ascend-deck.css` — slide system (Layout, chrome, type modifiers, auto-shrink, print). Extends brand.css.
4. `05-CreativeOps/brain/raw/standards/Ascend/brand.css` — design tokens (colors, typography, spacing, radii, font-face declarations).
5. `05-CreativeOps/Frameworks/deck-token-contract.md` — Layer 1 constants + Layer 2 variable naming contract.
6. `05-CreativeOps/Clients/Ascend/Brand/Assets/Ascend_StyleGuide.md` — brand rules and visual identity.
7. `05-CreativeOps/Clients/Ascend/Brand/Fonts/` — FT System Trial (Grotesk: Regular, Medium, Semibold, Bold) + FT System Mono (Regular, Medium).

> **Asset path warning:** `brand.css` `@font-face` declarations use relative paths to `Brand/Fonts/`. Image paths in deck HTMLs point to `../Assets/Imagery/Travel/`. If folders are renamed or restructured, these paths break silently — fonts fall back to system sans-serif and images disappear. Always verify font rendering and image loading after any folder change.

---

## Input Format — `.md` Deck Outline

The user provides a Markdown file (or inline content) with this structure:

```markdown
---
title: "Deck Title"
client: "Client Name"
date: 2026-04-16
theme: light
---

## cover-photo
# ascend
[Tagline or subtitle]

---

## section-break
bg: midnight
# [Section headline]

---

## three-col-numbered
# [Headline as takeaway]
- number: 01 | desc: [Card 1 description, max ~20 words]
- number: 02 | desc: [Card 2 description]
- number: 03 | desc: [Card 3 description]

---

## split-image-list
variant: light
photo: Assets/[photo].jpg
pills: [Label 1] | [Label 2]
- 01 | [List item 1, max ~15 words]
- 02 | [List item 2]
- 03 | [List item 3]
- 04 | [List item 4]

---

## four-col-metrics
# [Headline as takeaway]
- pill: [Category] | value: [XX%] | subtitle: [Label] | desc: [context, max ~10 words]
- pill: [Category] | value: [XX%] | subtitle: [Label] | desc: [context]
- pill: [Category] | value: [XX%] | subtitle: [Label] | desc: [context]
- pill: [Category] | value: [0] | subtitle: [Label] | desc: [context]

---

## timeline
# [Headline as takeaway]
- label: [Phase 1] | desc: [Description]
- label: [Phase 2] | desc: [Description]
- label: [Phase 3] | desc: [Description]
- label: [Phase 4] | desc: [Description]

---

## quote
# [Optional headline]
quotes:
- quote: [Quote text, max ~25 words] | author: [Name] | role: [Title @ Company]

---

## cta-contacts
# [CTA headline, max ~60 chars]
- name: [Full Name] | email: [email@domain.com]
- name: [Full Name] | email: [email@domain.com]

---

## closing-photo
# Thank you
photo: Assets/[closing-photo].jpg
```

> **Note:** This example shows a subset of the 27 available slide types. See the full type reference below for all markers and fields.

---

## Slide Types — All 30

### 1. `cover-photo`

Full-bleed background photo with centered logo wordmark and tagline. No topbar chrome.

**Marker:** `## cover-photo`
**Fields:**
- `# [headline]` — Wordmark text (typically "ascend")
- Plain text line — Tagline
- `photo: [path]` — Background image (optional; defaults to placeholder)

**Density:** 1 headline + 1 tagline. No lists, no body text.

```markdown
## cover-photo
# ascend
Make booking travel effortless
photo: Assets/cover-sky.jpg
```

**Co-branding variant:** When building a deck for a specific prospect or partner, include their logo next to the Ascend wordmark. Layout: `[Ascend wordmark] × [Client logo]` centered horizontally. The `×` separator uses mono font at `text-lg`, 60% white opacity. Client logo height matches Ascend wordmark visually (~52px). If the client logo is dark, apply `filter: brightness(0) invert(1)` to make it white. Client logos live in `Assets/Partner Logos/`.

```markdown
## cover-photo
# ascend
cobrand: Assets/Partner Logos/[client-logo].png
Make booking travel effortless
photo: Assets/cover-sky.jpg
```

```html
<div class="cover-wordmark" style="gap:var(--space-4);align-items:center;">
  <img src="../Assets/Logo/Wordmark/ascend-wordmark-white.svg" alt="Ascend" class="cover-logo">
  <span style="font-family:var(--font-mono);font-size:var(--text-lg);color:rgba(255,255,255,.6);">&times;</span>
  <img src="../Assets/Partner Logos/[logo]" alt="[Client]" style="height:52px;width:auto;filter:brightness(0) invert(1);">
</div>
```

> **When to use:** Any deck targeting a named prospect or partner. Omit for generic capabilities or investor decks.
> **Filter rule:** Apply `brightness(0) invert(1)` only if the source logo is dark. If a white version of the logo exists, use it directly without the filter.

---

### 2. `section-break`

Full-color background with large headline anchored bottom-left. No topbar chrome.

**Marker:** `## section-break`
**Fields:**
- `bg: midnight|land|purple|sun|sky` — Background color (required)
- `# [headline]` — Large section title (80px)

**Density:** Headline only. Max 2 lines at 80px (~20 chars/line).

```markdown
## section-break
bg: midnight
# The problem
```

**CSS mapping:** `bg: midnight` -> `.slide--section-midnight`, `bg: land` -> `.slide--section-land`, `bg: purple` -> `.slide--section-purple`, `bg: sun` -> `.slide--section-sun`, `bg: sky` -> `.slide--section-sky`.

**Note:** Sun and Sky variants use Midnight-colored text and icon instead of white.

---

### 3. `three-col-numbered`

Sky background. Centered title + 3 white cards, each with a large mono number and description.

**Marker:** `## three-col-numbered`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- number: XX | desc: YY` — Card items (exactly 3)

**Density:** 3 cards (fixed). Description max ~20 words per card.

```markdown
## three-col-numbered
# Booking travel shouldn't be this hard
- number: 01 | desc: Hours wasted searching across sites and portals.
- number: 02 | desc: Paying retail fares without proprietary inventory.
- number: 03 | desc: Disruptions handled alone, often at inconvenient hours.
```

---

### 4. `hero-photo-tags`

Full-bleed photo background with dark overlay, floating Sun pills, and white headline bottom-left. Topbar chrome (white variant).

**Marker:** `## hero-photo-tags`
**Fields:**
- `# [headline]` — White headline (32px), max-width 700px
- `photo: [path]` — Background image
- `tags:` followed by `- [tag text]` — Floating pill tags (Sun color, positioned automatically)

**Density:** 1 headline (max 2 lines) + up to 6 tags.

```markdown
## hero-photo-tags
# Your 24/7 travel concierge, for premium, stress-free journeys.
photo: Assets/hero.jpg
tags:
- Paris
- London
- New York
```

---

### 5. `split-image-list`

50/50 split. Left panel: photo in rounded window with pill overlays. Right panel: numbered list rows with chevron icons.

**Marker:** `## split-image-list`
**Fields:**
- `variant: light|purple` — Left panel background. `light` = neutral-95 (default), `purple` = primary purple
- `photo: [path]` — Image in left panel rounded window
- `pills: [label1] | [label2]` — Overlay pills on image (optional)
- `- NN | [text]` — Numbered list items (01-04)

**Density:** 4 items (hard limit). Each item max ~15 words.

```markdown
## split-image-list
variant: purple
photo: Assets/concierge.jpg
pills: Jake | One-way
- 01 | Real humans. No chatbots, portals or hold music.
- 02 | Book flights, hotels, and ground transport from one WhatsApp Group.
- 03 | Save an average of 35% on business and first class.
- 04 | We monitor every leg and fix problems before you notice.
```

**Additional field:** `reversed: true` — Swaps panels (image right, list left). CSS class: `slide--split-reversed`.

---

### 6. `three-col-steps`

Sky background. Centered title + 3 step cards, each with a midnight mockup area, step label, name, and description.

**Marker:** `## three-col-steps`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- step: NN | name: XX | desc: YY` — Step items (exactly 3)

**Density:** 3 steps (fixed). Description max ~25 words per step.

```markdown
## three-col-steps
# Text. Approve. Done.
- step: 01 | name: Text | desc: Send us your travel plans on WhatsApp. Dates, destinations, preferences. One message is all we need.
- step: 02 | name: Approve | desc: Within 60 minutes, we send personalized options with transparent pricing. You review and approve.
- step: 03 | name: Done | desc: We book everything, monitor your journey, and handle any changes.
```

---

### 7. `team-grid`

White background. Centered title, avatar grid in rows, bottom stat pill.

**Marker:** `## team-grid`
**Fields:**
- `# [headline]` — Centered title (42px)
- `members:` followed by `- name: XX | role: YY` — Team members. Use `---` within members block to indicate row break.
- `stat: [text]` — Bottom pill text (mono, uppercase, outline style)

**Density:** Max 5 members per row, max 2 rows (10 total). Stat pill max 80 chars.

```markdown
## team-grid
# Real people. Available 24/7.
members:
- name: Zach | role: Chief Executive Officer
- name: Cameron | role: Chief Experience Officer
- name: Omar | role: Chief Operating Officer
---
- name: Maleeha | role: Head of Concierge
- name: Deeksha | role: Head of Product
stat: +60 team members across four time zones ensuring 24/7 coverage
```

---

### 8. `four-col-metrics`

Light gray background (neutral-95). Centered title + 4 metric columns with left border separators.

**Marker:** `## four-col-metrics`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- pill: XX | value: YY | subtitle: ZZ | desc: WW` — Metric items (exactly 4)

**Density:** 4 metrics (fixed). Value = mono 72px number. Description max ~10 words.

**Pill colors:** Default = `pill--purple`. Override with `pill-color: midnight|sun|land|light|outline`.

```markdown
## four-col-metrics
# Save more on every trip
- pill: Business Class | value: 35% | subtitle: Average savings | desc: on business and first class (North America-Europe routes).
- pill: Long-Haul | value: 20% | subtitle: Average savings | desc: other long-haul premium routes.
- pill: Last-Minute | value: 62% | subtitle: Average savings | desc: on last-minute business class.
- pill: Fees | value: 0 | subtitle: Booking fees | desc: or hidden charges.
```

---

### 9. `timeline-two-col`

Light gray background. Left-aligned title + 2-column grid of numbered timeline rows with chevron icons.

**Marker:** `## timeline-two-col`
**Fields:**
- `# [headline]` — Left-aligned title (42px), max-width 900px
- `- num: NN | title: XX | desc: YY` — Timeline items (max 5; items 1-3 go in left column, 4-5 in right)

**Density:** 5 items (hard limit). Description max ~25 words per item.

```markdown
## timeline-two-col
# Executive flying San Francisco to London
- num: 01 | title: Request (Monday morning) | desc: "Need SFO to London this Friday, business class, return following Wednesday".
- num: 02 | title: Response (45 minutes later) | desc: Three complete options with transparent pricing.
- num: 03 | title: Approved and booked | desc: Flight, hotel near office, car service confirmed.
- num: 04 | title: Proactive handling (Friday morning) | desc: Team rebooks onto later BA flight, adjusts hotel check-in.
- num: 05 | title: Outcome | desc: Member arrives on time. Total time spent: 3 minutes.
```

---

### 9b. `timeline`

Neutral-95 background. Centered title + horizontal row of nodes connected by a line. Each node has a purple dot marker, label, and optional description.

**Marker:** `## timeline`
**Fields:**
- `# [headline]` — Left-aligned title (42px)
- `- label: XX | desc: YY` — Timeline nodes (max 5). `desc` is optional.

**Density:** 5 nodes (hard limit). Label max ~3 words, description max ~15 words.

```markdown
## timeline
# Our 90-day roadmap
- label: Week 1-2 | desc: Discovery and onboarding
- label: Week 3-4 | desc: Pilot launch with initial cohort
- label: Week 5-8 | desc: Optimize and expand coverage
- label: Week 9-12 | desc: Full rollout and reporting
```

**CSS mapping:** `.slide--timeline`. Purple dot markers (`.timeline-marker`), horizontal connector line (`::before` pseudo-element), nodes in flex row.

---

### 10. `three-col-testimonials`

White background. Centered title + 3 testimonial columns with left border separators.

**Marker:** `## three-col-testimonials`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- tier: XX | amount: YY | saved: ZZ | detail: WW | quote: QQ` — Testimonial items (exactly 3)

**Density:** 3 testimonials (fixed). Quote max ~25 words. Detail max ~20 words.

**Tier pill colors:** `Enterprise` = `pill--purple`, `Individual` = `pill--midnight`. Third testimonial quote-mark uses Land color.

```markdown
## three-col-testimonials
# Real savings from real members
- tier: Enterprise | amount: $127,000 | saved: Saved for Bitkraft | detail: Bitkraft Ventures: $127,000 saved over 6 months, 47 bookings. | quote: The time we save on travel coordination is time we spend with founders.
- tier: Enterprise | amount: $42,000 | saved: Saved for Charlotte Tilbury | detail: Charlotte Tilbury: $42,000 saved over 3 months, 18 bookings. | quote: I'm not buying cheaper travel -- I'm buying calm.
- tier: Individual | amount: $18,500 | saved: Saved for Individual executive | detail: $18,500 saved over 12 months, 14 trips. | quote: It's become my default travel brain.
```

---

### 11. `three-col-features`

Sky background. Centered title + 3 feature cards with photo, subtitle, and checklist.

**Marker:** `## three-col-features`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- photo: XX | subtitle: YY | checks: A | B | C | D` — Feature cards (exactly 3). Checks pipe-separated.

**Density:** 3 cards (fixed). 4 checklist items per card (hard limit). Photo area = 200px height with flight-path decorative overlay.

```markdown
## three-col-features
# Everything included, no surprises
- photo: Assets/travel.jpg | subtitle: Unlimited travel | checks: Flights, hotels, ground transport. | Business and personal trips. | Family travel included. | No per-booking fees.
- photo: Assets/service.jpg | subtitle: 24/7 service | checks: Real humans via WhatsApp. | 1-minute response time. | Proactive monitoring and rebooking. | No hold music, no chatbots.
- photo: Assets/prefs.jpg | subtitle: Your preferences protected | checks: Loyalty numbers and status preserved. | Preferred airlines, seats, hotels. | Points and upgrades maintained. | Works inside corporate policies.
```

---

### 12. `two-col-comparison`

Midnight background. White centered title + 2 white cards with photo, subtitle, and checklist.

**Marker:** `## two-col-comparison`
**Fields:**
- `# [headline]` — Centered title (60px, white text)
- `left:` block — First card (`photo:`, `subtitle:`, `checks:` list)
- `right:` block — Second card (`photo:`, `subtitle:`, `checks:` list, optional `muted: true`)

**Density:** 2 cards. Max 4 checklist items per card. Right card's `muted: true` renders checks with muted icon color.

```markdown
## two-col-comparison
# Is Ascend right for you?
left:
  photo: Assets/yes.jpg
  subtitle: Ascend is for you if you
  checks:
  - Fly frequently (6+ trips per year).
  - Value reliability, precision, and speed.
  - Prefer real humans over apps or call centers.
  - Expect issues to be solved before you know they exist.
right:
  photo: Assets/no.jpg
  subtitle: Ascend isn't for you if you
  checks:
  - Fly infrequently.
  - Enjoy searching for fares yourself.
  - Prefer self-service comparison sites.
  muted: true
```

---

### 13. `three-col-pricing`

Sky background. Centered title + 3-column grid: pricing card (Midnight) + ROI card (neutral-95) + savings table card (neutral-95).

**Marker:** `## three-col-pricing`
**Fields:**
- `# [headline]` — Centered title (42px)
- `pricing:` block — `title:`, `price:`, `alt:`, `features:` (list), `cta:`
- `roi:` block — `title:`, `pill:`, `amount:`, `label:`, `details:` (pipe-separated), `footer:`
- `savings:` block — `heading:`, `columns:` (pipe-separated headers), `rows:` (pipe-separated data)

**Density:** Fixed 3-column layout. Pricing features max 4 items. Savings rows max 4.

```markdown
## three-col-pricing
# Unlimited trips. No booking fees.
pricing:
  title: Individual membership
  price: $2,500/year
  alt: (or $250 per month)
  features:
  - Unlimited trips.
  - No per-booking fees.
  - Covers business, personal, and family travel.
  cta: Call out here
roi:
  title: ROI example
  pill: Payback in 2-3 trips
  amount: $4,000
  label: Savings
  details: 2 transatlantic trips: $4,000 saved. | Membership cost: $2,500. | Net benefit: $1,500+ in year one.
  footer: Most members pay back within 2-3 trips.
savings:
  heading: Savings by route and cabin
  columns: Route Type | Business/First | Economy
  rows:
  - US > Europe | 35% average | 5-10%
  - Other long-haul | 20% average | 3-8%
  - Last-minute (any route) | Up to 62% | 10-15%
```

---

### 14. `faq-split`

50/50 split on neutral-95 background. Left: numbered Q&A rows. Right: photo in rounded window with optional route tag overlay.

**Marker:** `## faq-split`
**Fields:**
- `- q: XX | a: YY` — FAQ items (max 5)
- `photo: [path]` — Right panel image
- `route: [code1] | [code2] | [city1] | [city2]` — Optional flight route overlay on photo

**Density:** 5 Q&A items (hard limit). Answer max ~15 words.

```markdown
## faq-split
- q: Do you charge booking fees? | a: No. Flat membership covers everything.
- q: Will I lose my loyalty status? | a: No. We book using your loyalty numbers.
- q: Can my EA use this for me? | a: Yes. Many members are EAs managing executive travel.
- q: What if I need to cancel? | a: Included. We handle all changes at no extra charge.
- q: What if savings aren't as advertised? | a: We show comparison on every booking.
photo: Assets/faq-window.jpg
route: LDN | LAX | London | Los Angeles
```

---

### 15. `cta-contacts`

Midnight background. White headline top-left + contact rows bottom-right. Topbar chrome (white variant).

**Marker:** `## cta-contacts`
**Fields:**
- `# [headline]` — White headline (42px), max-width 800px
- `- name: XX | email: YY` — Contact items

**Density:** Max 4 contact rows. Email always hyperlinked as `mailto:`.

**Headshot rule:** When a contact has a headshot file in `Assets/Headshots/`, include it as a 36px circular photo at the start of the contact row. Grid changes from `[name] [email]` to `[headshot 36px] [name 160px] [email 1fr]`. Always check `Assets/Headshots/` before building the slide — if the file exists, include it. Available headshots are listed in `ascend-deck-blocks.md` § Team Roster.

```markdown
## cta-contacts
# Ready to make travel effortless?
- name: Chloe Rose Mitchell | email: chloe@joinascend.com | photo: Assets/Headshots/Chloe Rose Mitchell.jpeg
- name: Zach Resnick | email: zach@joinascend.com | photo: Assets/Headshots/Zach Rensick.jpeg
```

---

### 16. `closing-photo`

Full-bleed photo background with centered "Thank you" + Ascend arrow icon. No topbar chrome.

**Marker:** `## closing-photo`
**Fields:**
- `# [headline]` — Centered text (80px, white) — typically "Thank you"
- `photo: [path]` — Background image

**Density:** Headline only. No body text, no lists.

```markdown
## closing-photo
# Thank you
photo: Assets/closing-sky.jpg
```

**Headline length:** Max ~20 characters for the default inline (horizontal) layout. For longer headlines, add the `closing-column` class to the `<section>` to switch to a vertical stack where the text sits above the arrow icon.

```markdown
## closing-photo
# Questions? Let's talk.
photo: Assets/closing-sky.jpg
layout: column
```

---

### 17. `content`

Generic text slide. Neutral-95 background. Headline + body paragraph + optional bullet list with check icons.

**Marker:** `## content`
**Fields:**
- `# [headline]` — Left-aligned title (42px)
- `body: [text]` — Body paragraph (max 3 sentences)
- `- [bullet text]` — Optional bullet list items with check icons (max 6)

**Density:** Body ≤3 sentences OR ≤6 bullets. Not both at max.

```markdown
## content
# Why this matters
body: The travel industry has shifted. Companies that adapt their booking processes save both time and money. Here's what we've learned.
- Consolidation reduces cost by 20-30%
- Dedicated concierges cut coordination time by 80%
- Proactive monitoring eliminates 95% of disruptions
```

---

### 17b. `screenshot`

Neutral-95 background. Centered headline + contained image (no crop). Use for UI screenshots, dashboards, app screens, or any visual that must remain uncropped.

**Marker:** `## screenshot`
**Fields:**
- `# [headline]` — Centered title (42px)
- `image: [path]` — Screenshot or image file
- `alt: [text]` — Alt text for accessibility

**Density:** 1 headline + 1 image. No body text.

**CSS class:** `.slide--screenshot`

```markdown
## screenshot
# Platform dashboard
image: Assets/Imagery/dashboard-screenshot.jpg
alt: Ascend platform dashboard showing booking overview
```

**Notes:** The image is displayed with `object-fit: contain` — it will never be cropped, only scaled down to fit. A subtle shadow and border-radius are applied automatically.

---

### 18. `agenda`

White background with left purple accent strip containing arrow pattern. Numbered step list with title and optional description. No topbar chrome.

**Marker:** `## agenda`
**Fields:**
- `# [headline]` — Left-aligned title (42px)
- `- step: N | title: XX | desc: YY` — Agenda items. `desc` is optional.

**Density:** 4 default, 5 max steps. Description max ~15 words per step.

```markdown
## agenda
# What we'll cover
- step: 1 | title: The problem | desc: Why traditional booking fails frequent travelers
- step: 2 | title: Our solution | desc: How Ascend works differently
- step: 3 | title: Results | desc: Real savings from real members
- step: 4 | title: Next steps | desc: How to get started
```

**CSS mapping:** No topbar. Left `.agenda-accent` strip uses Primary (purple) background. Step numbers render in FT System Mono, Primary color.

---

### 19. `problem`

White background. Centered title + 2×2 grid of cards, each with a purple icon circle, title, and description.

**Marker:** `## problem`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- icon: XX | title: YY | desc: ZZ` — Grid items (exactly 4). `icon` is the Ascend arrow by default.

**Density:** 4 grid items (2×2 fixed). Description max ~20 words per card.

```markdown
## problem
# What's holding your team back?
- icon: arrow | title: Fragmented booking | desc: Hours wasted across multiple platforms and portals with no central control.
- icon: arrow | title: Retail pricing | desc: Paying full fare without access to proprietary inventory or negotiated rates.
- icon: arrow | title: No proactive support | desc: Disruptions handled alone, often at inconvenient hours with no backup.
- icon: arrow | title: Lost visibility | desc: No consolidated view of spend, savings, or travel patterns across the organization.
```

**Card layout:** Icon and title render inline (horizontal row), with description below. Icon uses `icon-container--sm` (32px squircle).

---

### 20. `results`

Neutral-95 background. Centered title + 2 white cards with pill label, large mono value, unit description, and delta badge (Sun color).

**Marker:** `## results`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- label: XX | value: YY | unit: ZZ | delta: WW` — Result cards (exactly 2). First card = "before", second = "after".

**Density:** 2 cards (fixed). Value renders in mono 48px.

```markdown
## results
# The bottom line
- label: Before | value: $4,850 | unit: Per booking average | delta: Baseline
- label: With Ascend | value: $3,200 | unit: Per booking average | delta: -34% cost reduction
```

**Pill colors:** First card label = `pill--midnight`, second card label = `pill--purple`. Delta badge = Sun background.

---

### 21. `cards`

White background. Centered title + 2×2 grid of bordered cards with purple icon circle, title, and description.

**Marker:** `## cards`
**Fields:**
- `# [headline]` — Centered title (42px)
- `- card: XX | icon: YY | desc: ZZ` — Card items (4 default, 6 max for 3-col variant). `icon` is the Ascend arrow by default.

**Density:** 4 (2×2), 6 max (3-col variant). Description max ~20 words per card.

```markdown
## cards
# What you get with Ascend
- card: Dedicated team | icon: arrow | desc: A named concierge who knows your preferences and handles everything.
- card: Proprietary rates | icon: arrow | desc: Access to fares 20-35% below retail on premium cabins.
- card: 24/7 monitoring | icon: arrow | desc: We track every leg and fix problems before you notice them.
- card: Zero fees | icon: arrow | desc: No booking fees, no change fees, no hidden charges. Ever.
```

**Card layout:** Icon and title render inline (horizontal row), with description below. Icon uses `icon-container--sm` (32px squircle).

---

### 22. `matrix`

Neutral-95 background. Centered title + comparison table. Two variants: **featured** (one column highlighted in purple) or **all-alt** (no featured column — neutral comparison between options).

**Marker:** `## matrix`
**Fields:**
- `# [headline]` — Centered title (42px)
- `featured: XX` — Featured column header label (renders as `pill--purple`). **Optional** — omit for all-alt variant.
- `columns: XX | YY | ZZ` — Column header labels (render as `pill--light`). When `featured:` is present, these are the non-featured columns. When `featured:` is omitted, ALL columns use this field.
- `- row: XX | val1 | val2 | val3` — Table rows. First value = row label, then one value per column.

**Density:** Max 5 columns × 6 rows.

**Variant A — Featured column (us vs. them):**

```markdown
## matrix
# How we compare
featured: Ascend
columns: Traditional agency | DIY booking
- row: Response time | Under 60 min | 24-48 hours | Self-service
- row: Pricing | Proprietary rates | Retail + markup | Retail
- row: Support | 24/7 WhatsApp | Business hours | Email only
- row: Rebooking | Proactive | On request | Self-service
- row: Booking fees | $0 | $25-75 per ticket | $0
```

**Variant B — All-alt (neutral comparison):**

```markdown
## matrix
# Card programs at a glance
columns: AMEX MR | Chase UR | Cash back
- row: Travel earn rate | 5x (Platinum) | 3x (Reserve) | 1-2%
- row: Transfer partners | 20+ airlines | 14+ airlines | None
- row: Points rebate / boost | Up to 50% rebate | Up to 100% boost | None
- row: Annual travel credits | $200 airline + $200 hotel | $300 travel credit | None
- row: Concierge access | Platinum line | None | None
```

**CSS mapping:** When `featured:` present: first data column = `.matrix-featured` (purple tint bg), others = `.matrix-alt`. When `featured:` omitted: all data columns = `.matrix-col-alt`. Header row uses pills (`pill--purple` for featured, `pill--light` for alt).

**Column count override:** The base matrix defaults to 5 columns (label + featured + 3 alt). For fewer columns, add `data-cols` on the `<section>`:
- `data-cols="4"` — label + featured + 2 alt
- `data-cols="3"` — label + featured + 1 alt

**Flat/neutral variant (CSS class `slide--matrix-flat`):** When no column should be highlighted (e.g., comparing items where none is "ours"), add the `slide--matrix-flat` class to the `<section>`. In the flat variant:
- Use `matrix-col-alt` for ALL data columns (not `matrix-col-featured`)
- No column gets the Midnight background or Ascend arrow logo treatment
- All columns render in neutral-90 with equal visual weight
- Use case: credit card program comparison, vendor feature grids, anything without a "home team"
- The flat variant also supports `data-cols` overrides: `data-cols="2"`, `data-cols="4"`, `data-cols="5"`

---

### 23. `two-col-text`

White background. Full-width headline + two equal text columns separated by a vertical divider. Each column has a sub-title and bullet list with check icons.

**Marker:** `## two-col-text`
**Fields:**
- `# [headline]` — Left-aligned title (42px)
- `left_title: XX` — Left column sub-title
- `left:` followed by `- [text]` — Left column bullet items
- `right_title: XX` — Right column sub-title
- `right:` followed by `- [text]` — Right column bullet items

**Density:** 5 items per column max.

```markdown
## two-col-text
# What changes when you join
left_title: Before Ascend
left:
- Hours spent searching across booking platforms
- Paying retail fares on every trip
- Handling disruptions alone at midnight
right_title: With Ascend
right:
- One message to your dedicated concierge
- Proprietary rates, 20-35% below retail
- Proactive monitoring and instant rebooking
```

---

### 24. `logo-wall`

White background. Optional mono eyebrow + centered title + symmetric grid of logo placeholders. Default 4 columns; override with `data-cols: 3` or `data-cols: 5`.

**Marker:** `## logo-wall`
**Fields:**
- `eyebrow: XX` — Optional mono uppercase eyebrow text
- `# [headline]` — Centered title (42px)
- `data-cols: N` — Column count (3, 4, or 5; default 4)
- `- src: XX | alt: YY` — Logo items. `src` = image path, `alt` = company name.

**Density:** 8 logos default, symmetric rows. Max 12.

```markdown
## logo-wall
eyebrow: Trusted by
# Companies that fly with Ascend
data-cols: 4
- src: Assets/logo-bitkraft.png | alt: Bitkraft Ventures
- src: Assets/logo-tilbury.png | alt: Charlotte Tilbury
- src: Assets/logo-acme.png | alt: Acme Corp
- src: Assets/logo-vertex.png | alt: Vertex Partners
- src: Assets/logo-nova.png | alt: Nova Capital
- src: Assets/logo-summit.png | alt: Summit Group
- src: Assets/logo-catalyst.png | alt: Catalyst Fund
- src: Assets/logo-meridian.png | alt: Meridian Advisors
```

**CSS mapping:** `data-cols` attribute on `<section>` controls grid columns. Logo placeholders = 160×60px rounded rectangles on neutral-90 background.

---

### 25. `blank`

White background. Topbar chrome only. No content. Used for breathing room, manual customization, or placeholder slides.

**Marker:** `## blank`
**Fields:** None.

**Density:** n/a — empty slide.

```markdown
## blank
```

---

### 26. `quote`

Neutral-95 background, 2-column split: quotes left, image right. Supports single (large centered quote), 2-stack (side-by-side cards), and 3-stack (tighter cards). Right panel has a rounded photo window with optional pill overlays.

**Marker:** `## quote`
**Fields:**
- `# [headline]` — Optional left-aligned title above quotes
- `photo: [path]` — Right panel image in rounded window
- For single quote: `quote: XX | author: YY | role: ZZ`
- For multi-quote: `quotes:` followed by `- quote: XX | author: YY | role: ZZ` (2 or 3 items)

**Density:** 1 quote (single, large text), 2 (stacked cards), 3 max (tight stacked). 4+ → split into 2 slides.

```markdown
## quote
photo: Assets/quote-photo.jpg
quotes:
- quote: [Quote text, max ~25 words] | author: [Name] | role: [Title @ Company]
- quote: [Quote text, max ~25 words] | author: [Name] | role: [Title @ Company]
```

**CSS mapping:** `.slide--quote`. Single = `.quote-single` (larger text). Multi = `.quote-stack` (2 cards) or `.quote-stack--3` (3 cards, tighter spacing). Quote marks use `::before` pseudo with Primary color.

### 27. `map`

Midnight background. Simplified world map silhouette with purple dot markers at specified locations. Stat bar at the bottom showing key numbers. Used for geographic presence, coverage areas, or office locations.

**Marker:** `## map`
**Fields:**
- `# [headline]` — White title (42px)
- `stat: XX` — Bottom stat bar text (e.g., "14 time zones · 21 countries · 70+ team"). Segments separated by ` · `
- `markers:` followed by `- label: XX | region: YY` — Location markers. Region determines approximate position: `na` (North America), `sa` (South America), `eu` (Europe), `af` (Africa), `me` (Middle East), `asia` (Asia), `oc` (Oceania)

**Density:** 12 markers max. Stat bar max 80 characters.

```markdown
## map
# Global coverage, local expertise
stat: 14 time zones · 21 countries · 70+ team members
markers:
- label: New York | region: na
- label: London | region: eu
- label: Dubai | region: me
- label: Singapore | region: asia
- label: Sydney | region: oc
- label: São Paulo | region: sa
```

**CSS mapping:** `.slide--map`. Map SVG uses `#icon-world-map` from sprite sheet. Markers positioned with `top`/`left` percentages. Purple dots (`.map-dot`) with glow ring. Stat bar uses FT System Mono, Sky color.

### 28. `cover-speakers`

Midnight background. Centered layout: Ascend wordmark (small) + large title + subtitle + speaker photo cards. No topbar chrome. Used for webinars, panels, and multi-presenter decks.

**Marker:** `## cover-speakers`
**Fields:**
- `# [headline]` — Large centered title (42px, white)
- Plain text line — Subtitle (18px, white 85% opacity)
- `speakers:` followed by `- name: XX | role: YY | photo: ZZ` — Speaker cards with circular photo, name, and role

**Density:** 1 headline + 1 subtitle + max 4 speakers. Title max 2 lines.

```markdown
## cover-speakers
# Maximizing corporate and personal travel
Credit cards, points strategy, and consolidator access
speakers:
- name: Zach Resnick | role: Founder & CEO | photo: Assets/Headshots/Zach.jpg
- name: Cameron Resnick | role: CXO | photo: Assets/Headshots/Cameron.jpg
```

**CSS mapping:** `.slide--cover-speakers`. Midnight BG. Wordmark via `<img>` (32px height). Speaker photos = 80px circular crops. Speaker role in FT System Mono, uppercase. No topbar.

---

## Parsing Rules

| Marker | Meaning | HTML mapping |
|---|---|---|
| `## [type]` | Slide type | `<section class="slide slide--[type]">` |
| `# [text]` | Slide headline | `.slide-title` / `.headline` / `.cta-headline` / `.section-headline` (per type) |
| `bg: midnight\|land\|purple\|sun\|sky` | Section-break background | `.slide--section-midnight` / `.slide--section-land` / `.slide--section-purple` / `.slide--section-sun` / `.slide--section-sky` |
| `variant: light\|purple` | Split-image-list panel color | `.left-panel` (light) / `.left-panel--purple` |
| `- number: XX \| desc: YY` | Numbered card item | `.card` > `.mono-number` + `<p>` |
| `- pill: XX \| value: YY \| subtitle: ZZ \| desc: WW` | Metric item | `.metric-col` > `.pill` + `.metric-number` + `.metric-subtitle` + `.metric-desc` |
| `- step: NN \| name: XX \| desc: YY` | Step item | `.step-card` > `.step-label` + `.step-name` + `.step-desc` |
| `- name: XX \| role: YY` | Team member | `.team-member` > `.avatar` + `.member-title` + `.member-name` |
| `stat: [text]` | Team stat pill | `.team-stat` > `.pill--outline` |
| `- num: NN \| title: XX \| desc: YY` | Timeline item | `.timeline-row` > `.tl-num` + `.tl-title` + `.tl-desc` |
| `- tier: XX \| amount: YY \| saved: ZZ \| detail: WW \| quote: QQ` | Testimonial item | `.testimonial-col` > `.pill` + `.testimonial-amount` + `.testimonial-saved` + `.testimonial-detail` + `.quote-text` |
| `- photo: XX \| subtitle: YY \| checks: A \| B \| C \| D` | Feature card | `.feature-card` > `.feature-photo` + `.feature-subtitle` + `.feature-checklist` |
| `left:` / `right:` + `photo:` + `subtitle:` + `checks:` | Comparison cards | `.comparison-card` > `.comparison-photo` + `.comparison-subtitle` + `.comparison-checklist` |
| `pricing:` / `roi:` / `savings:` blocks | Pricing grid components | `.pricing-card` / `.roi-card` / `.savings-card` |
| `- q: XX \| a: YY` | FAQ item | `.faq-row` > `.faq-question` + `.faq-answer` |
| `route: [code1] \| [code2] \| [city1] \| [city2]` | FAQ photo route overlay | `.faq-route-overlay` > pills + meta |
| `- name: XX \| email: YY` | Contact item | `.contact-row` > `.contact-name` + `.contact-email` |
| `photo: [path]` | Background or panel image | `.photo-bg` / `.image-frame` / `.faq-image` |
| `pills: [label1] \| [label2]` | Image overlay pills | `.pills-overlay` > `.pill` |
| `tags:` + `- [text]` | Floating hero tags | `.floating-pills` > `.pill--sun` |
| `muted: true` | Muted check icons (comparison right card) | `.check-item--muted` + `.icon-check--muted` |
| `body: XX` | Content slide body text | `.slide-body` |
| `- [text]` (inside `## content`) | Content bullet item | `.slide-list` > `<li>` + check icon |
| `- step: N \| title: XX \| desc: YY` (inside `## agenda`) | Agenda item | `.agenda-step` > `.agenda-step-num` + `.agenda-step-title` + `.agenda-step-desc` |
| `- icon: XX \| title: YY \| desc: ZZ` | Problem grid item | `.problem-card` > `.problem-icon` + `.problem-card-title` + `.problem-card-desc` |
| `- label: XX \| value: YY \| unit: ZZ \| delta: WW` | Results card item | `.results-card` > `.pill` + `.results-value` + `.results-unit` + `.results-delta` |
| `- card: XX \| icon: YY \| desc: ZZ` | Cards grid item | `.card-item` > `.card-icon` + `.card-title` + `.card-desc` |
| `featured: XX` | Matrix featured column header | `th.matrix-featured` > `.pill--purple` |
| `columns: XX \| YY` | Matrix alternate column headers | `th.matrix-alt` > `.pill--light` |
| `- row: XX \| val1 \| val2 \| val3` | Matrix table row | `<tr>` > `<td>` + `td.matrix-featured` + `td.matrix-alt` |
| `left_title:` / `right_title:` | Two-col-text column sub-titles | `.col-title` |
| `left:` / `right:` + `- [text]` (inside `## two-col-text`) | Two-col-text bullet items | `.col-list` > `<li>` + check icon |
| `- label: XX \| desc: YY` | Timeline horizontal node | `.timeline-node` > `.timeline-marker` + `.timeline-label` + `.timeline-desc` |
| `quote: XX \| author: YY \| role: ZZ` | Single quote | `.quote-single` > `.quote-text` + `.quote-attribution` |
| `quotes:` + `- quote: XX \| author: YY \| role: ZZ` | Multi-quote stack | `.quote-stack` > `.quote-card` (×2-3) |
| `stat: XX` | Map stat bar text | `.map-stats` > `.map-stat` |
| `speakers:` + `- name: XX \| role: YY \| photo: ZZ` | Cover speaker cards | `.speakers` > `.speaker` (photo + name + role) |
| `- label: XX \| region: YY` | Map location marker | `.map-marker` with position |
| `eyebrow: XX` | Logo-wall eyebrow text | `.slide-eyebrow` (mono, uppercase) |
| `- src: XX \| alt: YY` | Logo-wall logo item | `.logo-placeholder` / `<img>` |
| `data-cols: N` | Logo-wall column count (3, 4, 5) | `data-cols` attribute on `<section>` |
| Plain paragraph | Subtitle or tagline | `.slide-subtitle` / `.cover-tagline` |
| `---` between slides | Slide separator | (frontmatter uses first `---` pair) |
| `theme: light` | Frontmatter — forces light mode | Inline `:root` override in template |
| `variant: midnight` | Per-slide — midnight BG variant | `.slide--midnight` added to `<section>` |

---

## Midnight Variants

Slide types that support `.slide--midnight` modifier (midnight BG alternative):

| Slide type | Default surface | Midnight effect |
|---|---|---|
| `three-col-numbered` | Sky | Midnight BG, translucent cards, white text |
| `four-col-metrics` | Neutral-95 | Midnight BG, translucent borders, sun pills |
| `quote` (single / 2 / 3) | Neutral-95 | Midnight BG, sun quote marks, translucent cards |
| `problem` | Neutral-95 | Midnight BG, translucent cards, sun icon containers |
| `results` | Neutral-95 | Midnight BG, translucent cards, sun delta badges |
| `cards` | Neutral-95 | Midnight BG, translucent cards, sun icon containers |

> Surface temperature rule, auto-fix logic, and `.md` syntax (`variant: midnight`) defined in SKILL.md Rule 20.

---

## Ascend-Specific Density Limits

Extends the universal density limits in SKILL.md with Ascend-specific types:

| Type | Hard limit | If exceeded |
|---|---|---|
| `cover-photo` | 1 headline + 1 tagline | Cannot expand |
| `section-break` | 1 headline (80px, max 2 lines, ~20 chars/line) | Shorten copy |
| `hero-photo-tags` | 1 headline (max 2 lines) + 6 tags | Remove excess tags |
| `split-image-list` | 4 list items | Cannot exceed — layout is fixed |
| `three-col-steps` | 3 steps (fixed), ~25 words/step desc | Shorten descriptions |
| `team-grid` | 5 members/row, 2 rows max (10 total) + 1 stat | Split into 2 slides |
| `timeline-two-col` | 5 timeline items (3 left + 2 right) | 6+ → split into 2 slides |
| `three-col-testimonials` | 3 testimonials (fixed), ~25 words/quote | Shorten quotes |
| `three-col-features` | 3 cards, 4 check items/card | Shorten or split |
| `two-col-comparison` | 2 cards, 4 check items/card | Shorten or remove items |
| `three-col-pricing` | 1 pricing + 1 ROI + 1 savings table (4 rows max) | Summarize |
| `faq-split` | 5 Q&A items, ~15 words/answer | 6+ → split into 2 slides |
| `cta-contacts` | 4 contact rows | Cannot exceed |
| `closing-photo` | 1 headline only | Cannot expand |
| `screenshot` | 1 headline + 1 image | Cannot expand |
| `cover-speakers` | 1 headline + 1 subtitle + 4 speakers max | Reduce speakers or use separate intro slide |
| `map` | 12 markers, stat ≤80 chars | Remove excess markers |

> Universal types (content, problem, results, cards, metrics, matrix, etc.) use the limits in SKILL.md Step 1.6.

---

## Ascend Content Zones

Pixel dimensions for the Ascend template (960×540, 48px padding):

| Slide type | Content width (px) | Content height (px) | Notes |
|---|---|---|---|
| Full-width (content, problem, cards, metrics, results, three-col-*) | 864 | 444 | Slide − padding × 2 |
| split-image-list (right panel, 50/50) | 352 | 444 | 50% of slide − padding × 2 |
| split-image-list (right panel, 2fr/1fr) | 544 | 444 | 66% of slide − padding × 2 |
| two-col-text (per column) | 380 | 380 | (864 − divider − gap) / 2 |
| section-break | 864 | 444 | Headline at 80px = ~20 chars/line max |
| cover-speakers | 864 | ~400 | Depends on speaker count |

Headline tiers for Ascend:

| Context | Font size | Full-width chars/line | Split panel chars/line |
|---|---|---|---|
| Section-break / closing | 80px | ~20 | n/a |
| Slide title (default) | 42px | ~37 | ~15 |
| Hero-photo-tags | 32px | ~49 | n/a |

> Content budget formula, overflow handling, and auto-shrink thresholds defined in SKILL.md Rules 1 and 18.

---

## Ascend Assembly — Overrides to SKILL.md Output Steps

The assembly process follows SKILL.md Steps 1–4. Below are Ascend-specific overrides only:

**Step 2 overrides:**
- Base file: `ascend-deck-template.html` (not TCL default)
- Topbar color is **automatic** via CSS — no manual variant class needed. For mixed-BG slides, use `topbar-el--*` per-element overrides.
- No topbar on: `cover-photo`, `closing-photo`, section-breaks, `agenda`
- `cta-contacts` has topbar (white variant, Midnight BG)
- Section-breaks use class variant: `.slide--section-midnight` / `land` / `purple` / `sun` / `sky`

**Step 3 — additional Ascend checks:**

| Check | Pass criteria |
|---|---|
| Pills uppercase | All `.pill` text in FT System Mono, uppercase |
| Sentence case | All headlines and body in sentence case (not Title Case) |

**Step 4 — Visual QA:**
Open in Chrome. Verify topbar consistency, pill rendering in FT System Mono, headline type scale (80px / 42px / 32px), Ascend palette compliance.

> Copy fidelity protocol, consistency checks, and `deck-qa.mjs` workflow defined in SKILL.md.

---

## Layout Utilities

### `data-split` — Panel ratio override
For any 2-column slide (`split-image-list`, `quote`, `faq-split`), override the default 50/50 split:

| Attribute | Ratio |
|---|---|
| `data-split="60-40"` | 3fr 2fr |
| `data-split="40-60"` | 2fr 3fr |
| `data-split="70-30"` | 7fr 3fr |
| `data-split="30-70"` | 3fr 7fr |

Usage: `<section class="slide slide--quote" data-split="70-30">`

### `data-cols` — Column count override
Available on grid-based slides to change the default column count:

| Slide type | Default | Available overrides |
|---|---|---|
| `three-col-numbered` | 3 | `data-cols="2"`, `"4"`, `"5"` |
| `four-col-metrics` | 4 | `data-cols="2"`, `"3"` |
| `three-col-testimonials` | 3 | `data-cols="2"` |
| `three-col-steps` | 3 | `data-cols="2"`, `"4"` |
| `three-col-features` | 3 | `data-cols="2"`, `"4"` |
| `matrix` | 5 (label+4) | `data-cols="3"`, `"4"` |
| `matrix-flat` | 4 (label+3) | `data-cols="2"`, `"4"`, `"5"` |

Usage: `<section class="slide slide--four-col-metrics" data-cols="3">`

---

## Ascend-Specific Rules

> Universal rules (content budget, copy fidelity, density enforcement, auto-shrink, surface temperature, content-to-type matching, slide count warning) live in SKILL.md Rules 1–21. Below are Ascend-only rules.

1. **Theme default: `light`.** Ascend uses light mode by default. Set via frontmatter `theme: light|dark`.

2. **Topbar chrome.** Interior slides get `.topbar` with deck title (mono) + slide number (zero-padded, starting `01`) + Ascend arrow icon. Color is **automatic** via CSS:
   - Dark BG → white | Light BG → dark | Sun/Sky → midnight
   - No topbar on: `cover-photo`, `closing-photo`, section-breaks, `agenda`
   - Mixed-BG slides: use `topbar-el--white` / `topbar-el--dark` / `topbar-el--midnight` per element

3. **Cover slide.** Always first. Centered: arrow icon + "ascend" wordmark + tagline. BG: full-bleed photo or Land default. Auto-prepend if `.md` doesn't start with `## cover-photo`.

4. **Closing slide.** Always last. Full-bleed photo + centered "Thank you" + arrow icon. Auto-append if `.md` doesn't end with `## closing-photo`.

5. **Sentence case everywhere.** Per Ascend TOV. Exception: pills, tags, mono labels = ALL CAPS.

6. **Typography.**
   - **FT System Mono** for data: numbers, pills, tags, step labels, timeline numbers, contact names, stat pills. Uppercase, tracking: 0.
   - **FT System Grotesk** for narrative: headlines (Medium), body (Regular), subtitles (Regular). Semibold only for emphasis within body.

7. **Surface temperatures.** Six branded backgrounds:
   - **Midnight** (`#1E2F39`): section-break, two-col-comparison, cta-contacts, step mockups
   - **Sky** (`#E0EFFF`): three-col-numbered, three-col-steps, three-col-features, three-col-pricing
   - **Land** (`#727841`): section-break variant, cover-photo default bg
   - **Purple** (`#6F57FF`): section-break variant, split-image-list panel variant, primary pills, agenda accent
   - **White** (`#FFFFFF`): agenda, problem, cards, two-col-text, logo-wall, blank
   - **Neutral-95** (`#F2F2F2`): content, results, matrix

8. **Flight-path overlays.** Dashed SVG lines (1.5pt, white, `stroke-dasharray="4 4"`) inside feature/comparison card photos. Decorative, auto-generated — not in `.md` input.

9. **Rounded windows.** `border-radius: var(--radius-2xl)` (24px). Three-col-numbered cards: `var(--radius-3xl)` (64px).

10. **Pills.** `--radius-full`, FT System Mono, uppercase. Variants: `pill--sun`, `pill--purple`, `pill--midnight`, `pill--light`, `pill--outline`, `pill--outline-white`, `pill--land`.

11. **Check icons.** Purple stroke (positive), muted gray (negative/exclusion), white (dark backgrounds).

12. **Chevron circles.** 44px, 1.5px border. Purple on light BGs, white on dark BGs. Used in: split-image-list, timeline, FAQ.

13. **Print.** `@page: 10in 5.625in landscape, margin: 0`. `page-break-after: always`. No box shadows.

14. **Ascend arrow icon.** Sprite sheet `#icon-ascend-arrow`, `fill="currentColor"`. Sizes: cover (112×64), topbar (32×18), closing (48×27), mockup/matrix (20×18).

15. **Imagery — contrast safety.** For slides with white text overlay (cover-photo, hero-photo-tags, closing-photo, split-image, FAQ):
    - **Use:** dark/mid-tone images, silhouettes, backlit subjects, urban shadow/contrast, low-key executive travelers
    - **Reject:** overexposed, bright sky >50%, flash/studio lighting, subject competing with text overlay
    - **Pre-flight:** mentally overlay white text at 16px — if not legible, reject or crop to darker region

---

## Slide Type Reference

| # | Type | CSS Class | Background | Topbar | Layout |
|---|---|---|---|---|---|
| 01 | `cover-photo` | `.slide--cover-photo` | Photo / Land | None | Centered: arrow icon + wordmark + tagline |
| 02 | `section-break` | `.slide--section-midnight` / `land` / `purple` / `sun` / `sky` | Midnight / Land / Purple / Sun / Sky | None | Large headline bottom-left (120px) |
| 03 | `three-col-numbered` | `.slide--three-col-numbered` | Sky | Dark | Centered title + 3 white cards with mono numbers |
| 04 | `hero-photo-tags` | `.slide--hero-photo-tags` | Photo + overlay | White | Full photo, floating Sun pills, headline bottom-left |
| 05 | `split-image-list` | `.slide--split-image-list` | Light / Purple + White | Dark | 50/50: rounded photo left, numbered list right |
| 06 | `three-col-steps` | `.slide--three-col-steps` | Sky | Dark | Centered title + 3 step cards with mockup area |
| 07 | `team-grid` | `.slide--team-grid` | White | Dark | Centered title + avatar grid + stat pill |
| 08 | `four-col-metrics` | `.slide--four-col-metrics` | Neutral-95 | Dark | Centered title + 4 metric columns |
| 09 | `timeline-two-col` | `.slide--timeline-two-col` | Neutral-95 | Dark | Left title + 2-col numbered timeline |
| 10 | `three-col-testimonials` | `.slide--three-col-testimonials` | White | Dark | Centered title + 3 testimonial columns |
| 11 | `three-col-features` | `.slide--three-col-features` | Sky | Dark | Centered title + 3 feature cards with photo + checklist |
| 12 | `two-col-comparison` | `.slide--two-col-comparison` | Midnight | White | White title + 2 white cards with photo + checklist |
| 13 | `three-col-pricing` | `.slide--three-col-pricing` | Sky | Dark | Title + pricing card + ROI card + savings table |
| 14 | `faq-split` | `.slide--faq-split` | Neutral-95 | Dark | 50/50: numbered Q&A left, photo right |
| 15 | `cta-contacts` | `.slide--cta-contacts` | Midnight | White | White headline + contact pill rows bottom-right |
| 16 | `closing-photo` | `.slide--closing-photo` | Photo / Midnight | None | Centered: "Thank you" + arrow icon |
| 17 | `content` | `.slide--content` | Neutral-95 | Dark | Left title + body paragraph + optional bullet list |
| 17b | `screenshot` | `.slide--screenshot` | Neutral-95 | Dark | Centered title + contained image (no crop) |
| 18 | `agenda` | `.slide--agenda` | White | None | Purple accent strip + numbered step list |
| 19 | `problem` | `.slide--problem` | White | Dark | Centered title + 2×2 icon cards |
| 20 | `results` | `.slide--results` | Neutral-95 | Dark | Centered title + 2 before/after cards with delta badges |
| 21 | `cards` | `.slide--cards` | White | Dark | Centered title + 2×2 bordered card grid with icons |
| 22 | `matrix` | `.slide--matrix` | Neutral-95 | Dark | Centered title + comparison table with featured column |
| 23 | `two-col-text` | `.slide--two-col-text` | White | Dark | Left title + 2 equal text columns with divider |
| 24 | `logo-wall` | `.slide--logo-wall` | White | Dark | Eyebrow + centered title + symmetric logo grid |
| 25 | `blank` | `.slide--blank` | White | Dark | Topbar chrome only — empty |
| 26 | `quote` | `.slide--quote` | Neutral-95 | Dark | 50/50 split: quote(s) left, rounded photo right |
| 27 | `map` | `.slide--map` | Midnight | White | World map silhouette + purple dot markers + stat bar |
| 28 | `cover-speakers` | `.slide--cover-speakers` | Midnight | None | Centered: wordmark + title + subtitle + speaker photo cards |
| 9b | `timeline` | `.slide--timeline` | Neutral-95 | Dark | Horizontal nodes with purple dot markers + connector line |

---

## Recommended Sequences

| Deck type | Suggested slide order |
|---|---|
| **Sales Deck** | `cover-photo` → `agenda` → `section-break` → `problem` → `content` → `section-break` → `results` → `four-col-metrics` → `three-col-testimonials` → `section-break` → `three-col-pricing` → `cta-contacts` → `closing-photo` |
| **Partnership Deck** | `cover-photo` → `agenda` → `content` → `logo-wall` → `cards` → `results` → `matrix` → `cta-contacts` → `closing-photo` |
| **Capabilities Overview** | `cover-photo` → `section-break` → `cards` → `three-col-features` → `results` → `three-col-testimonials` → `logo-wall` → `closing-photo` |
| **Webinar / Educational** | `cover-speakers` → `section-break` → `three-col-numbered` → `matrix` → `logo-wall` (×N) → `results` (×N) → `closing-photo("Questions?")` |

---

## Build Rules — Learned from Production

### 1. Always copy the full sprite sheet

When creating a new deck from the template, copy the **entire** `<svg>` sprite block — not a subset. Mid-build icon additions cause avoidable rework.

### 2. Body text color is always `--color-neutral-0`

No exceptions on light-background slides. Do not use `--color-neutral-40` or any muted variant for body paragraphs. Muted colors are reserved for footnotes/disclaimers (`--text-xs` size) only.

### 3. Density overrides for non-standard layouts

Standard slide types are calibrated for their documented density limits. When exceeding them (e.g., 6 items in a `four-col-metrics` 3×2 grid, or `agenda` with a headline that wraps to 3+ lines), apply inline overrides:

| Override | Values |
|---|---|
| Headline | `font-size: 32px` (down from 42px) |
| Metric numbers | `font-size: 36px` (down from 48px) |
| Column padding | `var(--space-4) var(--space-6)` (down from `var(--space-6)`) |
| Column gap | `var(--space-2)` (down from `var(--space-3)`) |
| Grid row-gap | `var(--space-4)` |
| Content padding | `padding-top: var(--space-16); padding-bottom: var(--space-6)` |
| Agenda steps gap | `var(--space-6)` (down from `var(--space-8)`) |

### 4. `split-image-list` supports body text in right panel

The right panel is not limited to numbered list rows. It accepts:
- `.slide-title` (already styled at line 816 of `ascend-deck.css`)
- `<p>` elements with inline body-text styles

Use for narrative slides that need a photo panel without the numbered-list structure. Combine with `slide--split-reversed` and `data-split` as normal.

```markdown
## split-image-list
variant: light
photo: Assets/Imagery/Travel/photo.jpg
# Headline here
body: Paragraph text. Second sentence.
```

### 5. Slide type selection heuristics

| Content pattern | Best slide type |
|---|---|
| 3 items with a prominent number each | `three-col-numbered` |
| 4 items with icon + title + description | `cards` (2×2) |
| 6+ icon+title items, no description | `cards` with `grid-template-columns: repeat(4, 1fr)` + `flex-direction: row` on cards |
| Narrative text + photo | `split-image-list` with body text (see §4) |
| 4 numbered activation steps | `agenda` |
| Financial data, 4 metrics | `four-col-metrics` |
| Financial data, 6 metrics | `four-col-metrics` `data-cols="3"` + density overrides (see §3) |

### 6. Cards — horizontal layout for high item count

When a `cards` slide has 6+ items with icon + title only (no description), switch cards to horizontal layout:

```html
<div class="card-item" style="flex-direction:row;align-items:center;padding:var(--space-4);gap:var(--space-3);">
  <div class="icon-container icon-container--sm icon-container--light" style="flex-shrink:0;">
    <svg width="16" height="16"><use href="#icon-name"/></svg>
  </div>
  <h3 class="card-title" style="font-size:var(--text-sm);margin:0;">Title</h3>
</div>
```

This keeps card height compact and fits 8 items in a 4×2 grid within 540px.

### 7. Contact rows — include headshots when available

Before building a `cta-contacts` slide, check `Assets/Headshots/` for each contact. If a headshot file exists, include it as a 36px circular image at the start of the row:

```html
<div class="contact-row" style="padding:var(--space-1) var(--space-4) var(--space-1) var(--space-1);display:grid;grid-template-columns:36px 160px 1fr;gap:var(--space-3);align-items:center;">
  <img src="../Assets/Headshots/[file]" alt="" style="width:36px;height:36px;border-radius:50%;object-fit:cover;">
  <span class="contact-name" style="min-width:auto;padding:var(--space-2) var(--space-4);">[Name]</span>
  <span class="contact-email">[email]</span>
</div>
```

If no headshot exists for a contact, fall back to the standard 2-column grid (`[name] [email]`). Do not mix rows with and without headshots — if any contact lacks a photo, omit headshots from all rows.

### 8. Cover overlay — use `.cover-overlay` div, not inline styles

When a cover photo needs darkening for text contrast, add a `.cover-overlay` div and use `data-overlay` on the section instead of inline `rgba()` divs:

```html
<section class="slide slide--cover-photo" data-overlay="20">
  <img class="cover-bg photo-fill" src="..." alt="">
  <div class="cover-overlay"></div>
  <div class="cover-content">...</div>
</section>
```

Supported values: `20` (default), `30`, `40`, `50`. No `data-overlay` = no overlay.

### 9. Unnumbered split-image rows — use `.list-row--plain`

For narrative slides where numbered rows don't apply, add `.list-row--plain` instead of inline `grid-template-columns` overrides:

```html
<div class="list-row list-row--plain">
  <span class="list-text">...</span>
  <span class="chevron-circle icon-chevron">...</span>
</div>
```

For the closing statement (semibold, no chevron, no border), use `.list-row--callout`:

```html
<div class="list-row list-row--callout">
  <span class="list-text">Closing statement here.</span>
</div>
```

### 10. Icon cards — use `slide--icon-cards` for service grids

The "One service" slide is now a first-class slide type. No inline styles needed:

```markdown
## icon-cards
# One service. Full trip.
- icon: plane | label: Flights
- icon: hotel | label: Hotels
- icon: car | label: Cars
footer: Everything handled through Ascend.
```

CSS class: `.slide--icon-cards`. Grid: `.icon-grid` (5×2). Items: `.icon-card` with `.icon-card-label`. Default BG: `neutral-95`.

---

*Guide v3.3 — The Creative Lever for Ascend (960×540)*
