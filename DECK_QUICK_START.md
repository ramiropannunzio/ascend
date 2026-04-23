# Ascend Deck System — Quick Start

> You ask for a deck in plain language. The system builds it.
> This page tells you how to get the best results with the least effort.

---

## Before you start — gather these 3 things

The system already knows Ascend's core stats, cases, and proof points (they're pre-loaded as "blocks" — see below). You don't need to retype any of that.

What you DO need to bring is what's **unique to this deal:**

| # | What | Why | Example |
|---|---|---|---|
| 1 | **Audience + context** — who, what they care about, why now | Determines slide sequence, tone, and which blocks to include | "Kerry, VP Partnerships at Bilt. They're looking for a travel benefit for top-tier cardholders. Zero engineering lift is the key concern." |
| 2 | **The one message** — if they remember one thing, what is it | Becomes the through-line that every headline reinforces | "Ascend runs your travel ops behind the scenes, 24/7, no integration needed" |
| 3 | **The ask** — what should they do after the last slide | The CTA. Be specific. | "Schedule a pilot scoping call with Zach this week" |

**That's it.** The stats (22s response, 35% savings, 98% proactive), the cases (Bitkraft, Charlotte Tilbury), the pilot structure, the pricing — all of that is already in the system. You'll confirm which pieces to include via a checklist.

**When to add your own numbers:** If you have deal-specific data that's not in the blocks — a custom quote from this prospect, a savings projection for their specific travel volume, a pilot timeline that differs from the standard 60-90 days — include it. Deal-specific data always beats generic blocks.

---

## How to ask for a deck

Open Claude Code in the `Slides/` folder and describe what you need. Examples:

**Good — gives the system everything it needs:**
> "Partnership deck for Bilt. Zach presents to their VP Partnerships. Pilot angle: 60-90 days, 50-100 top-tier cardholders, zero engineering lift. Key stats: 22s response, 35% savings, $127K saved for Bitkraft. CTA: schedule pilot scoping call."

**Fine — system fills gaps from existing blocks:**
> "Sales deck for an individual membership prospect. High-net-worth frequent flyer, 10+ trips/year. Focus on savings and white-glove service."

**Too vague — will produce generic output:**
> "Make me a deck for a meeting tomorrow."

The system will ask you 4 questions. Answer them all in one message — don't drip-feed.

---

## The 4 questions

| # | Question | What to answer | Tip |
|---|---|---|---|
| Q1 | Who and what type of deck? | Audience name + deck type (sales, partnership, capabilities, investor) + who presents | Include seniority of the audience — it changes the headline style |
| Q2 | What's the one message? | The single takeaway | Write it as a headline, not a description. "We save 35% on every trip" not "We want to show our value proposition" |
| Q3 | Confirm blocks + add unique content | Check the pre-loaded blocks, then add deal-specific data | Untick blocks that don't apply. Add any metrics, quotes, or context that's unique to this deal |
| Q4 | Constraints? | Slide count, things to exclude, deadline | "Max 12 slides, no pricing slide — we'll discuss verbally" |

---

## What are "blocks"?

Pre-written slide content that Ascend reuses across decks. The system knows all of it — you never need to retype these numbers.

**What's already in the system:**

| Block | Content inside |
|---|---|
| Core metrics | 22s avg response, 35% savings, 98% proactive handling, 70+ team, 14 time zones |
| Bitkraft case | $127K saved, 47 bookings, 6 months, 32% avg savings |
| Charlotte Tilbury case | $42K saved, 18 executive bookings, 3 months |
| Individual exec case | $18,500 saved, 14 trips, 12 months, 38% avg savings |
| FinTech partner case | $1B+ annual card volume, launching Q2 2026 |
| 3-step process | Text → Approve → Done (with descriptions) |
| Pilot structure | 60-90 days, 50-100 cardholders, zero integration |
| Pricing | $2,500/year individual, ROI example, savings table by route |
| Why Ascend | Speed, proven at scale, 24/7 coverage, aligned economics |
| Trusted-by logos | Ramp, GymShark, Left Lane, Bessemer, Tiger 21, R360, Bitkraft, GV |
| Team grid | Leadership names + roles |
| Competitive matrix | Ascend vs traditional agency vs DIY booking |

When you ask for a deck, the system presents these as a checklist:

> - [x] Core metrics (22s, 35%, 98%)
> - [x] Bitkraft case ($127K)
> - [x] Pilot structure (60-90 days)
> - [ ] Pricing ($2,500/year) ← unticked because we'll discuss live
> - [x] Why Ascend
>
> Untick what doesn't apply.

**Your job:** confirm the checklist + add anything deal-specific that's not listed above.

---

## After the deck is generated

You'll get:
1. A **slide plan table** — quick overview of every slide, its type, and headline
2. The **full outline** — ready to be assembled into HTML

Review the plan first. Common adjustments:
- "Swap slides 4 and 5"
- "Remove the pricing slide — we'll discuss live"
- "Change the headline on slide 3 to focus on time saved, not cost"
- "Add a case study slide for Charlotte Tilbury between results and CTA"

Once approved, the outline gets assembled into an HTML deck. Open in Chrome, Cmd+P → PDF.

---

## Tips for better decks

**Headlines are takeaways, not labels.**
| Don't | Do |
|---|---|
| Our Results | Members save $127K in 6 months |
| How It Works | One message. We handle the rest. |
| Pricing | Unlimited trips. Zero booking fees. |
| The Team | 70+ experts across 14 time zones |

**Numbers > adjectives.**
"35% average savings on business class" beats "significant cost reduction on premium travel."

**One idea per slide.**
If you're explaining two things, you need two slides. The system enforces this, but better input = fewer splits.

**Less is more.**
A 10-slide deck that lands > an 18-slide deck that drifts. Default target: 12 slides.

---

## Reference prompts — copy, adapt, paste

### Partnership deck

```
Partnership deck for Bilt. Zach presents to Kerry (VP Partnerships).

Angle: Ascend operates as Bilt's travel concierge behind the scenes.
Zero engineering lift, white-label, members interact through Bilt's
existing advisor channel.

Include blocks: core metrics, Bitkraft case, Charlotte Tilbury case,
pilot structure, why Ascend. Exclude: pricing (discuss live), FAQ.

Deal-specific (not in blocks):
- Bilt's top-tier cardholders travel internationally, spend more per
  trip, expect white-glove. They notice when experiences fall short.
- Scale phase: deeper integration into Bilt app, custom reporting,
  co-branded comms, dedicated phone line.
- Economics: custom pricing based on volume, zero setup fees,
  detailed proposal within one week of pilot alignment.

CTA: Confirm pilot structure. Ascend delivers terms within one week.
Launch in 30 days.

Max 12 slides.
```

**What makes this work:** Audience with name and title, clear angle, explicit block selection (no retyping stats), deal-specific context that blocks DON'T cover (Bilt's cardholder profile, scale phase details, custom economics), concrete CTA with timeline.

---

### Sales deck — individual membership

```
Sales deck for an individual prospect. High-net-worth executive,
flies transatlantic 8-10 times/year, currently books through
a mix of Amex Travel and direct.

Message: Stop spending hours searching. One message, options
in 60 minutes.

Include blocks: core metrics, 3-step process, pricing,
individual exec case. Exclude: team grid, pilot structure,
partnership-specific slides.

Deal-specific:
- This person's pain: spends 2+ hours per trip comparing fares
  across Amex Travel, Google Flights, and airline direct. No
  proactive support when things go wrong.
- They fly SFO-LHR regularly — use the route example.

CTA: Apply for membership — Zach's email.

10 slides max.
```

**What makes this work:** Specific prospect profile (not just "individual"), their current workflow (Amex Travel + direct), explicit block selection + exclusions, one deal-specific insight (the SFO-LHR route), tight slide cap.

---

### Investor deck

```
Investor update deck for Q2 board meeting. Omar presents to
the board + lead investor.

Message: Ascend is scaling — FinTech partnership launching Q2,
pipeline of 3 enterprise deals, unit economics improving.

Include blocks: core metrics, Bitkraft case, FinTech case,
team grid, trusted-by logos, competitive matrix.

Deal-specific (board-only context, not in blocks):
- 3 enterprise deals in pipeline, combined potential: $200K ARR
- Unit economics: CAC down 40% QoQ, LTV/CAC now 4.2x
- Q2-Q3 roadmap: FinTech launch (May), hire 15 concierges
  (June), enterprise self-serve portal MVP (August)
- The ask: approve Q2 budget for partnership team expansion

Include a timeline slide for the Q2-Q3 roadmap.

14 slides. Matrix as appendix.
```

**What makes this work:** Context (board meeting, not a cold pitch), block selection for proof points, forward-looking numbers that blocks DON'T have (pipeline ARR, unit economics, hiring plan), specific internal CTA (budget approval).

---

### Capabilities overview

```
General capabilities deck — no specific prospect. Use as a
leave-behind after intro calls.

Message: Ascend is a 24/7 travel concierge that saves time
and money for frequent travelers and their companies.

Include blocks: core metrics, 3-step process, competitive matrix,
trusted-by logos. Exclude: pricing, pilot structure, FAQ.

Deal-specific: None — this is a generic overview. Cover all
three angles briefly:
1. Individual — convenience + savings
2. Enterprise — managed travel for teams
3. Partnership — white-label concierge as cardholder benefit

Use one testimonial per angle if possible (1 enterprise case,
1 individual case, 1 partner mention).

CTA: "Let's find the right fit — book a call with Zach or Chloe."

10 slides. Broad, not deep.
```

**What makes this work:** Clear purpose (leave-behind), block selection for proof, explicit exclusions, structured ask (3 angles), soft CTA appropriate for the context.

---

### Adapting a prompt

Start from the reference prompt closest to your need, then:

1. **Replace** the audience, angle, and CTA
2. **Swap** the proof points for ones relevant to this deal
3. **Add** any deal-specific context the blocks don't cover
4. **Remove** anything that doesn't apply

The system does the rest — sequence, headlines, formatting, density checks.

---

## Common deck types — summary

| Type | Key input needed | Typical slide count |
|---|---|---|
| **Sales** (individual prospect) | Prospect profile, travel frequency, pain points, relevant case | 10-14 |
| **Partnership** (B2B) | Partner name, integration angle, pilot structure, mutual value | 10-12 |
| **Investor** | Market size, traction metrics, team, financials, ask | 12-15 |
| **Capabilities** (general) | Service overview, differentiators, proof points | 8-10 |
| **Webinar / Educational** | Topic, speaker names + roles + photos, audience context | 8-12 |

---

## File structure

```
Slides/
├── ascend-deck-template.html   ← Starter kit (30 types + variants). Duplicate to create new decks.
├── ascend-sales-deck.html      ← Production sales deck (live, 34 slides)
├── ascend-deck.css             ← Shared by all decks. Don't edit unless changing the system.
├── ASCEND_DECK_GUIDE.md        ← Full technical reference (slide types, parsing rules, density limits)
├── DECK_QUICK_START.md         ← This file
└── References/                 ← Figma Slides PNGs + PDF references
```

---

*Quick Start v1.2 — The Creative Lever for Ascend*
