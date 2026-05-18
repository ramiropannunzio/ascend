# Ascend Deck Blocks — Reusable Content Library

> Pre-written content blocks for Ascend decks. Organized by deck type.
> Each block maps to a slide type and contains ready-to-use `.md` syntax.
>
> **How it works:** When `/deck-brief` detects Ascend as the client,
> it presents the relevant blocks as a checklist. The operator confirms
> which ones to include. Only deal-specific content requires manual input.

---

## Team Roster

Single source of truth for team members with headshots. All blocks (`ascend-team`, `ascend-closing-zach`, `webinar-cover`) reference this roster.

| Name | Role | Headshot |
|---|---|---|
| Zach Resnick | Founder & CEO | `Assets/Headshots/Zach Rensick.jpeg` |
| Cameron Resnick | CXO | `Assets/Headshots/Cameron Resnick.jpeg` |
| Omar Ismail | COO | `Assets/Headshots/Omar Ismail.jpeg` |
| Chloe Rose Mitchell | Head of Strategic Growth | `Assets/Headshots/Chloe Rose Mitchell.jpeg` |
| Mike Finneran | Account Executive | `Assets/Headshots/Mike Finneran.png` |
| Israel Stern | Director of Flights | `Assets/Headshots/Israel Stern.jpeg` |

> **Note:** Headshot paths are relative to `05-CreativeOps/Clients/Ascend/Brand Assets/`. Members without a headshot file (Maleeha, Deeksha, Dave, Nishit) are omitted — add them here when photos are available.

---

## What's Already in the System

All blocks available. `✓ Auto` = Part A (static, injected as-is). `✎ Fill` = requires project-specific content before use.

| Block ID | Slide type | What it contains | Deck types | Status |
|---|---|---|---|---|
| `ascend-metrics` | `four-col-metrics` | 35% savings · 20% long-haul · 62% last-minute · 0 fees | All | ✓ Auto |
| `ascend-response-metrics` | `four-col-metrics` | 22s response · 35% savings · 98% proactive · 70+ team | All | ✓ Auto |
| `ascend-process` | `three-col-steps` | Text → Approve → Done | All | ✓ Auto |
| `ascend-process-list` | `split-image-list` | 4-row numbered list version of the process | All | ✓ Auto |
| `ascend-why` | `content` | Speed, proven at scale, 24/7 coverage, aligned economics | All | ✓ Auto |
| `ascend-bitkraft` | `three-col-testimonials` | Bitkraft $127K · Charlotte Tilbury $42K · Individual $18.5K | Sales · Partnership | ✓ Auto |
| `ascend-fintech-case` | `content` | FinTech with $1B+ card volume launching Q2 2026 | Partnership · Investor | ✓ Auto |
| `ascend-comparison` | `two-col-comparison` | "Ascend is for you if" / "isn't for you if" | Sales | ✓ Auto |
| `ascend-pricing` | `three-col-pricing` | $2,500/year · ROI example · savings table by route | Sales | ✓ Auto |
| `ascend-pilot` | `content` | 60-90 days, 50-100 cardholders, zero integration | Partnership | ✓ Auto |
| `ascend-pilot-scale` | `two-col-text` | Phase 1 (Pilot) → Phase 2 (Scale) | Partnership | ✓ Auto |
| `ascend-trusted-by` | `logo-wall` | Ramp, GymShark, Left Lane, Bessemer, Tiger 21, R360, Bitkraft, GV | All | ✓ Auto |
| `ascend-team` | `team-grid` | 9 leadership + stat pill | Sales · Investor | ✓ Auto |
| `ascend-matrix` | `matrix` | Ascend vs agency vs DIY (5 features) | Sales · Capabilities | ✓ Auto |
| `ascend-closing-zach` | `cta-contacts` | Zach + Chloe + Mike | All | ✓ Auto |
| `ascend-closing-photo` | `closing-photo` | "Thank you" + photo | All | ✓ Auto |
| `ascend-next-steps` | `content` | Share portal → confirm pilot → terms in 1 week → launch in 30 days | Partnership | ✎ Fill |
| `webinar-cover` | `cover-speakers` | Midnight BG, wordmark + title + subtitle + speaker cards | Webinar | ✎ Fill |
| `webinar-closing-qa` | `closing-photo` | "Questions?" + sky photo | Webinar | ✓ Auto |
| `webinar-travel-levers` | `three-col-numbered` | 3 levers: credit card strategy, points optimization, consolidator access | Webinar (Travel) | ✓ Auto |
| `webinar-card-matrix` | `matrix` | AMEX MR vs Chase UR vs Cash back (5 features) | Webinar (Travel) | ✓ Auto |
| `webinar-amex-partners` | `logo-wall` ×2 | 15 AMEX MR transfer partners (airlines + hotels) | Webinar (Travel) | ✓ Auto |
| `webinar-chase-partners` | `logo-wall` | 9 Chase UR transfer partners | Webinar (Travel) | ✓ Auto |
| `webinar-amex-rebate` | `results` | Platinum 35% vs Centurion 50% rebate comparison | Webinar (Travel) | ✓ Auto |
| `webinar-chase-boost` | `results` | Sapphire Preferred vs Reserve Points Boost | Webinar (Travel) | ✓ Auto |

> **Part A vs Part B:** `✓ Auto` blocks go straight into the outline with no operator input. `✎ Fill` blocks appear in Part A but flag the operator to supply project-specific content. Everything else the operator provides from scratch belongs to Part B.

---

## Global Blocks

Blocks that can appear in ANY Ascend deck type. Always offered.

### `ascend-metrics`
**Slide type:** `four-col-metrics`
**Description:** Savings metrics by route type

```markdown
## four-col-metrics
# Save more on every trip
- pill: Business Class | value: 35% | subtitle: Average savings | desc: on business and first class fares.
- pill: Long-Haul | value: 20% | subtitle: Average savings | desc: other long-haul premium routes.
- pill: Last-Minute | value: 62% | subtitle: Average savings | desc: on last-minute business class.
- pill: Fees | value: 0 | subtitle: Booking fees | desc: or hidden charges.
```

### `ascend-response-metrics`
**Slide type:** `four-col-metrics`
**Description:** Operational performance numbers

```markdown
## four-col-metrics
# A 24/7 travel team, not a booking tool
- pill: Response | value: 22s | subtitle: Average response time | desc: day or night, weekends, holidays.
- pill: Savings | value: 35% | subtitle: Average savings | desc: on business and first class fares.
- pill: Proactive | value: 98% | subtitle: Proactive handling | desc: of disruptions actioned before the member notices.
- pill: Team | value: 70+ | subtitle: Travel experts | desc: across fourteen time zones and 21 countries.
```

### `ascend-process`
**Slide type:** `three-col-steps`
**Description:** 3-step booking process (card layout)

```markdown
## three-col-steps
# Text. Approve. Done.
- step: 01 | name: Text | desc: Send us your travel plans on WhatsApp. Dates, destinations, preferences. One message is all we need.
- step: 02 | name: Approve | desc: Within 60 minutes, we send personalized options with transparent pricing. You review and approve.
- step: 03 | name: Done | desc: We book everything, monitor your journey, and handle any changes. You travel with complete peace of mind.
```

### `ascend-process-list`
**Slide type:** `split-image-list`
**Description:** 4-row numbered list version of the process

```markdown
## split-image-list
variant: light
photo: Assets/Imagery/traveler-businessman-suitcase.jpg
- 01 | Real humans. No chatbots, portals or hold music.
- 02 | Book flights, hotels, and ground transport from one WhatsApp group.
- 03 | Save an average of 35% on business and first class.
- 04 | We monitor every leg and fix problems before you notice.
```

### `ascend-why`
**Slide type:** `content`
**Description:** 4 reasons to choose Ascend

```markdown
## content
# 70+ experts, 14 time zones, zero markups
- Under 60-second responses on every request
- Major FinTech launching travel concierge in Q2 with Ascend
- 24/7 coverage with no gaps across 14 time zones
- We never mark up above direct booking prices
```

### `ascend-closing-zach`
**Slide type:** `cta-contacts`
**Description:** Standard CTA with contacts

```markdown
## cta-contacts
# Ready to make travel effortless?
- name: Zach Resnick | email: zach@joinascend.com
- name: Chloe Rose Mitchell | email: chloe@joinascend.com
- name: Mike Finneran | email: mike@joinascend.com
```

### `ascend-closing-photo`
**Slide type:** `closing-photo`
**Description:** Thank you closing slide

```markdown
## closing-photo
# Thank you
photo: Assets/Imagery/traveler-man-blue-sky.jpg
```

### `ascend-trusted-by`
**Slide type:** `logo-wall`
**Description:** Client/partner trust signals

```markdown
## logo-wall
eyebrow: Trusted by
# Executives who move fast and expect the best
- src: Assets/logos/ramp.png | alt: Ramp
- src: Assets/logos/gymshark.png | alt: GymShark
- src: Assets/logos/left-lane.png | alt: Left Lane
- src: Assets/logos/bessemer.png | alt: Bessemer
- src: Assets/logos/tiger-21.png | alt: Tiger 21
- src: Assets/logos/r360.png | alt: R360
- src: Assets/logos/bitkraft.png | alt: Bitkraft
- src: Assets/logos/gv.png | alt: GV
```

> **Note:** Update logo paths when assets are added to the package.

---

## Sales Deck Blocks

For decks where Ascend is selling to an individual prospect.

### `ascend-bitkraft`
**Slide type:** `three-col-testimonials`
**Description:** 3 case studies with amounts and quotes

```markdown
## three-col-testimonials
# Real savings from real members
- tier: Enterprise | amount: $127,000 | saved: Saved for Bitkraft | detail: Bitkraft Ventures: $127,000 saved over 6 months, 47 bookings, 32% average savings. | quote: The time we save on travel coordination is time we spend with founders. That's the real ROI.
- tier: Enterprise | amount: $42,000 | saved: Saved for Charlotte Tilbury | detail: Charlotte Tilbury: $42,000 saved over 3 months, 18 bookings. | quote: I'm not buying cheaper travel — I'm buying calm.
- tier: Individual | amount: $18,500 | saved: Saved for Individual executive | detail: $18,500 saved over 12 months, 14 trips, 38% average savings. | quote: It's become my default travel brain.
```

### `ascend-comparison`
**Slide type:** `two-col-comparison`
**Description:** "Is Ascend right for you?" split

```markdown
## two-col-comparison
# Is Ascend right for you?
left:
  photo: Assets/Imagery/traveler-airport-stride.jpg
  subtitle: Ascend is for you if you
  checks:
  - Fly frequently (6+ trips per year).
  - Value reliability, precision, and speed.
  - Prefer real humans over apps or call centers.
  - Expect issues to be solved before you know they exist.
right:
  photo: Assets/Imagery/traveler-mobile-phone.jpg
  subtitle: Ascend isn't for you if you
  checks:
  - Fly infrequently.
  - Enjoy searching for fares yourself.
  - Prefer self-service comparison sites.
  muted: true
```

### `ascend-pricing`
**Slide type:** `three-col-pricing`
**Description:** Individual membership pricing + ROI + savings table

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
  cta: Apply now
roi:
  title: ROI example
  pill: Payback in 2-3 trips
  amount: $4,000
  label: Savings
  details: 2 transatlantic business class trips: $4,000 saved. | Membership cost: $2,500. | Net benefit: $1,500+ in year one.
  footer: Most members pay back their membership within 2-3 trips.
savings:
  heading: Savings by route and cabin
  columns: Route Type | Business/First | Economy
  rows:
  - US > Europe | 35% average | 5-10%
  - Other long-haul | 20% average | 3-8%
  - Last-minute (any route) | Up to 62% | 10-15%
```

### `ascend-team`
**Slide type:** `team-grid`
**Description:** Leadership team + stat pill

```markdown
## team-grid
# Real people. Available 24/7.
Your dedicated team includes:
members:
- name: Zach Resnick | role: Founder & CEO | photo: Assets/Headshots/Zach Rensick.jpeg
- name: Cameron Resnick | role: CXO | photo: Assets/Headshots/Cameron Resnick.jpeg
- name: Omar Ismail | role: COO | photo: Assets/Headshots/Omar Ismail.jpeg
- name: Chloe Rose Mitchell | role: Head of Strategic Growth | photo: Assets/Headshots/Chloe Rose Mitchell.jpeg
- name: Mike Finneran | role: Account Executive | photo: Assets/Headshots/Mike Finneran.png
- name: Israel Stern | role: Director of Flights | photo: Assets/Headshots/Israel Stern.jpeg
---
- name: Maleeha | role: Head of Concierge
- name: Deeksha | role: Head of Product
- name: Dave | role: Chief of Staff
- name: Nishit | role: Head of People
stat: +60 team members across four time zones ensuring 24/7 coverage
```

### `ascend-matrix`
**Slide type:** `matrix`
**Description:** Ascend vs traditional agency vs DIY booking

```markdown
## matrix
# How we compare
featured: Ascend
columns: Traditional agency | DIY booking
- row: Response time | Under 60 seconds | 24-48 hours | Self-service
- row: Pricing | Proprietary rates | Retail + markup | Retail
- row: Support | 24/7 WhatsApp | Business hours | Email only
- row: Rebooking | Proactive | On request | Self-service
- row: Booking fees | $0 | $25-75 per ticket | $0
```

---

## Partnership Deck Blocks

For decks where Ascend is proposing a B2B partnership or white-label relationship.

### `ascend-pilot`
**Slide type:** `content`
**Description:** Pilot terms boilerplate

```markdown
## content
# Launch in 30 days with zero engineering lift

- 60-90 day pilot with 50-100 top-tier members
- Ascend handles flights, changes, cancellations, disruptions
- Members interact through your existing channel
- Full visibility into bookings and interactions
- Zero integration work from your engineering team
```

### `ascend-pilot-scale`
**Slide type:** `two-col-text`
**Description:** Phase 1 (Pilot) → Phase 2 (Scale)

```markdown
## two-col-text
# What getting started looks like
left_title: Phase 1 — Pilot
left:
- 60 to 90 days, 50-100 top-tier members
- Flights, changes, cancellations, disruptions
- Members interact through existing channel
- Full visibility into bookings and interactions
- Zero engineering work required
right_title: Phase 2 — Scale
right:
- Expand to broader member tiers
- Deeper integration into app experience
- Custom reporting and analytics
- Co-branded communications and dedicated phone line
```

### `ascend-fintech-case`
**Slide type:** `content`
**Description:** FinTech partnership proof point

```markdown
## content
# A major FinTech is already launching with Ascend

A FinTech with over $1B in annual card volume is launching travel concierge as a cardholder benefit in Q2 2026. White-label, zero engineering lift on their side. Ascend powers everything behind the scenes.
```

### `ascend-next-steps`
**Slide type:** `content`
**Description:** Partnership next steps (requires fill)

```markdown
## content
# Let's get started

- [Partner contact] shares backend portal details
- [Partner] confirms or modifies pilot structure
- Ascend delivers terms within one week
- Pilot launches with [X] top-tier members within 30 days
```

> **Requires fill:** Replace `[Partner contact]`, `[Partner]`, and `[X]` with deal-specific values.

---

## Webinar Blocks

For educational presentations, webinars, and thought-leadership decks. Different tone from sales — informational, not persuasive.

### `webinar-cover`
**Slide type:** `cover-speakers`
**Description:** Webinar cover with speakers (requires fill)

```markdown
## cover-speakers
# [Webinar title]
[Subtitle — topic framing]
speakers:
- name: [Speaker 1] | role: [Title] | photo: Assets/Headshots/[file]
- name: [Speaker 2] | role: [Title] | photo: Assets/Headshots/[file]
```

> **Requires fill:** Topic, subtitle, speaker names/roles/photos. The `cover-speakers` slide type uses Midnight BG with centered wordmark, title, subtitle, and speaker photo cards.

### `webinar-closing-qa`
**Slide type:** `closing-photo`
**Description:** "Questions?" closing for webinars

```markdown
## closing-photo
# Questions?
photo: Assets/Imagery/traveler-man-blue-sky.jpg
```

---

## Webinar Blocks — Travel Optimization Topic

Reusable content from the "Maximizing Corporate and Personal Travel" webinar. Use when the topic is credit cards, points strategy, or consolidator access.

### `webinar-travel-levers`
**Slide type:** `three-col-numbered`
**Description:** 3 optimization levers most travelers miss

```markdown
## three-col-numbered
# 3 levers most travelers miss
- number: 01 | desc: Credit card strategy. Choose cards that earn 3-5x on travel and stack category bonuses for $250K+ annual spend.
- number: 02 | desc: Points optimization. Transfer points to airline programs at peak value instead of redeeming at fixed rates.
- number: 03 | desc: Consolidator access. Below-retail fares on premium cabins through industry inventory most travelers never see.
```

### `webinar-card-matrix`
**Slide type:** `matrix`
**Description:** AMEX MR vs Chase UR vs Cash back comparison

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

### `webinar-amex-partners`
**Slide type:** `logo-wall` (2 slides)
**Description:** AMEX Membership Rewards transfer partners (15 total, split across 2 slides)

```markdown
## logo-wall
eyebrow: AMEX Membership Rewards
# Transfer partners
data-cols: 4
- src: Assets/Airline logos/AMEX membership rewards/ana-mileage-club.png | alt: ANA Mileage Club
- src: Assets/Airline logos/AMEX membership rewards/singapore-krisflyer.png | alt: Singapore Airlines KrisFlyer
- src: Assets/Airline logos/AMEX membership rewards/british-airways.png | alt: British Airways Executive Club
- src: Assets/Airline logos/AMEX membership rewards/delta-skymiles.png | alt: Delta SkyMiles
- src: Assets/Airline logos/AMEX membership rewards/flying-blue.png | alt: Air France-KLM Flying Blue
- src: Assets/Airline logos/AMEX membership rewards/emirates-skywards.png | alt: Emirates Skywards
- src: Assets/Airline logos/AMEX membership rewards/jetblue-trueblue.png | alt: JetBlue TrueBlue
- src: Assets/Airline logos/AMEX membership rewards/cathay-pacific.png | alt: Cathay Pacific Asia Miles

---

## logo-wall
eyebrow: AMEX Membership Rewards
# Transfer partners (cont.)
data-cols: 4
- src: Assets/Airline logos/AMEX membership rewards/aeroplan.png | alt: Aeroplan
- src: Assets/Airline logos/AMEX membership rewards/lifemiles.png | alt: Avianca LifeMiles
- src: Assets/Airline logos/AMEX membership rewards/hawaiian-miles.png | alt: Hawaiian Miles
- src: Assets/Airline logos/AMEX membership rewards/qantas-frequent-flyer.png | alt: Qantas Frequent Flyer
- src: Assets/Airline logos/AMEX membership rewards/velocity-frequent-flyer.png | alt: Velocity Frequent Flyer
- src: Assets/Airline logos/AMEX membership rewards/hilton-honors.png | alt: Hilton Honors
- src: Assets/Airline logos/AMEX membership rewards/marriott-bonvoy.png | alt: Marriott Bonvoy
```

### `webinar-chase-partners`
**Slide type:** `logo-wall`
**Description:** Chase Ultimate Rewards transfer partners

```markdown
## logo-wall
eyebrow: Chase Ultimate Rewards
# Transfer partners
data-cols: 3
- src: Assets/Airline logos/Chase ultimate rewards/united.png | alt: United MileagePlus
- src: Assets/Airline logos/Chase ultimate rewards/british-airways.png | alt: British Airways
- src: Assets/Airline logos/Chase ultimate rewards/singapore-airlines.png | alt: Singapore Airlines
- src: Assets/Airline logos/Chase ultimate rewards/virgin-atlantic.png | alt: Virgin Atlantic
- src: Assets/Airline logos/Chase ultimate rewards/emirates.png | alt: Emirates
- src: Assets/Airline logos/Chase ultimate rewards/hyatt.png | alt: Hyatt
- src: Assets/Airline logos/Chase ultimate rewards/ihg.png | alt: IHG Hotels & Resorts
- src: Assets/Airline logos/Chase ultimate rewards/marriott.png | alt: Marriott
- src: Assets/Airline logos/Chase ultimate rewards/chase.png | alt: Chase
```

### `webinar-amex-rebate`
**Slide type:** `results`
**Description:** AMEX Platinum vs Centurion airline rebate

```markdown
## results
# AMEX airline rebate: 35% vs 50%
- label: Business Platinum | value: 35% | unit: Rebate on 1 selected airline | delta: Up to 1M MR pts/year
- label: Business Centurion | value: 50% | unit: Rebate on airline purchases | delta: +43% higher return
```

### `webinar-chase-boost`
**Slide type:** `results`
**Description:** Chase Sapphire Preferred vs Reserve Points Boost

```markdown
## results
# Chase Points Boost: up to 100%
- label: Sapphire Preferred / Ink | value: 100% | unit: Maximum Points Boost | delta: $95 annual fee
- label: Sapphire Reserve | value: 100% | unit: Maximum Points Boost | delta: 3x travel earn + $300 credit
```

---

## How `/deck-brief` Uses This File

1. Q1 determines the deck type + detects Ascend as client → loads this file
2. Q3 Part A presents the matching blocks as a checklist:

**Sales Deck checklist:**
> - [x] `ascend-response-metrics` — 22s, 35%, 98%, 70+ team
> - [x] `ascend-process` — Text → Approve → Done
> - [x] `ascend-bitkraft` — 3 cases ($127K, $42K, $18.5K)
> - [x] `ascend-comparison` — "Is Ascend right for you?"
> - [x] `ascend-pricing` — $2,500/year + ROI + savings table
> - [x] `ascend-team` — 9 leadership + stat
> - [ ] `ascend-matrix` — vs agency vs DIY
> - [x] `ascend-closing-zach` — Zach + Chloe + Mike

**Partnership Deck checklist:**
> - [x] `ascend-response-metrics` — 22s, 35%, 98%, 70+ team
> - [x] `ascend-process-list` — 4-row numbered process
> - [x] `ascend-bitkraft` — 3 cases
> - [x] `ascend-pilot-scale` — Phase 1 → Phase 2
> - [x] `ascend-fintech-case` — $1B+ FinTech launching Q2
> - [x] `ascend-why` — Speed, scale, coverage, economics
> - [ ] `ascend-pricing` — exclude if discussing live
> - [x] `ascend-next-steps` — ✎ Fill partner-specific details
> - [x] `ascend-closing-zach` — Zach + Chloe + Mike

**Investor Deck checklist:**
> - [x] `ascend-response-metrics` — 22s, 35%, 98%, 70+ team
> - [x] `ascend-bitkraft` — 3 cases
> - [x] `ascend-fintech-case` — $1B+ FinTech
> - [x] `ascend-team` — 9 leadership
> - [x] `ascend-trusted-by` — 8 logos
> - [x] `ascend-matrix` — competitive comparison
> - [x] `ascend-closing-zach` — contacts

**Webinar Deck checklist:**
> - [x] `webinar-cover` — ✎ Fill topic, subtitle, speakers
> - [x] `webinar-travel-levers` — 3 optimization levers (if travel topic)
> - [x] `webinar-card-matrix` — AMEX vs Chase vs Cash back (if travel topic)
> - [x] `webinar-amex-partners` — 15 AMEX transfer partners (if travel topic)
> - [x] `webinar-chase-partners` — 9 Chase transfer partners (if travel topic)
> - [x] `webinar-amex-rebate` — Platinum vs Centurion (if travel topic)
> - [x] `webinar-chase-boost` — Sapphire Preferred vs Reserve (if travel topic)
> - [x] `webinar-closing-qa` — "Questions?"

3. Q3 Part B asks only for deal-specific content not covered by blocks
4. Confirmed blocks are injected as-is into the `.md` outline
5. Headlines can be overridden if the operator's through-line (Q2) demands it

---

## Block Selection by Deck Type

| Deck Type | Blocks to offer |
|---|---|
| Sales | `ascend-response-metrics`, `ascend-process`, `ascend-bitkraft`, `ascend-comparison`, `ascend-pricing`, `ascend-team`, `ascend-matrix`, `ascend-trusted-by`, `ascend-closing-zach`, `ascend-closing-photo` |
| Partnership | `ascend-response-metrics`, `ascend-process-list`, `ascend-bitkraft`, `ascend-pilot`, `ascend-pilot-scale`, `ascend-fintech-case`, `ascend-why`, `ascend-next-steps`, `ascend-trusted-by`, `ascend-closing-zach`, `ascend-closing-photo` |
| Investor | `ascend-response-metrics`, `ascend-bitkraft`, `ascend-fintech-case`, `ascend-team`, `ascend-trusted-by`, `ascend-matrix`, `ascend-closing-zach`, `ascend-closing-photo` |
| Capabilities | `ascend-response-metrics`, `ascend-process`, `ascend-metrics`, `ascend-bitkraft`, `ascend-matrix`, `ascend-trusted-by`, `ascend-closing-zach`, `ascend-closing-photo` |
| Webinar | `webinar-cover`, topic-specific blocks (e.g., `webinar-travel-*` for travel optimization), `webinar-closing-qa` |

---

*ascend-deck-blocks v1.1 — The Creative Lever for Ascend*
