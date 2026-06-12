# DESIGN.md — The Clean Cycle AZ

Design specification for the landing page redesign.
Written before any HTML. All code defers to this file.

---

## 0. Brief summary

The Clean Cycle AZ is a family-owned residential and commercial cleaning company
serving Gilbert, Chandler, Queen Creek, Mesa, and the broader East Valley. Five-plus
years in business, 100+ regular customers, licensed/bonded/insured, eco-friendly
products. The tone is: a neighbor you trust, not a faceless franchise.

The page must convert first-time visitors into quote requests. It must also
communicate reliability to the "I've been burned before" homeowner — the customer
who tried a cheap Groupon cleaner and now wants proof before they hand over a key.

---

## 1. Color system

Six named tokens derived from the two brand anchors.
Hex values are canonical here; OKLCH equivalents for CSS are noted inline.

### Anchor colors

| Token | Hex | OKLCH approx. | Role |
|---|---|---|---|
| `--color-navy` | `#1B365D` | `oklch(26% 0.075 250)` | Primary text, CTA fills, nav bg on scroll |
| `--color-teal` | `#2ABFBF` | `oklch(72% 0.115 196)` | Accent — checkmarks, links, focus rings, active state |

### Derived colors

| Token | Hex | OKLCH approx. | Derivation + Role |
|---|---|---|---|
| `--color-cream` | `#F8F4EE` | `oklch(96.5% 0.012 82)` | Paper surface. Warm off-white, hue pulled toward the sandy warmth of Arizona sun rather than clinical white. All default section backgrounds. |
| `--color-cloud` | `#EAF5F5` | `oklch(94% 0.018 196)` | Secondary surface. Very light teal tint — used for alternating sections (trust strip, pricing band) so the page breathes without going cold grey. |
| `--color-slate` | `#4A6B8A` | `oklch(46% 0.065 250)` | Mid-navy. Secondary text, muted labels, placeholder text, caption color. |
| `--color-sand` | `#CEC6B4` | `oklch(80% 0.018 82)` | Rule/border. Warm greige — section dividers, card borders, table rules. Never pure grey. |

### State derivatives (not standalone tokens, applied as modifiers)

| State | Value | Notes |
|---|---|---|
| Teal hover | `#1FA8A8` | 12% darker — still warm, not muddy |
| Teal active (pressed) | `#178F8F` | 20% darker |
| Navy hover | `#14284A` | 12% darker |
| Disabled background | `#C2CDD6` | Desaturated slate — signals unavailable without harsh grey |
| Disabled text | `#8E9FAC` | 60% lightness of slate |
| Modal overlay | `rgba(27, 54, 93, 0.72)` | Navy at 72% — dark enough to focus the modal, warm enough to not feel hostile |
| Focus ring | `#2ABFBF` at `outline: 2px solid` + `outline-offset: 2px` | Teal matches brand, 3:1+ contrast on cream and cloud |

### Anti-slop check
Would I pick navy + teal for a fintech? A fintech would use navy + teal as a "trust + innovation"
pairing — yes, this is a risk. What makes it non-fintech here:
- The cream paper (not white) anchors it in domesticity, not banking
- The cloud secondary surface (teal-tinted backgrounds) is unusual in fintech
- The sand rule color signals "home, warmth" not "interface"
- Typography and the signature element (§5) will pull it further away

---

## 2. Typography

### Two faces. Both from Google Fonts.

#### Display: Fraunces (variable)
**URL**: `https://fonts.google.com/specimen/Fraunces`
**Weights loaded**: 300, 600, 700

**Why this face for this client:**
Fraunces is a variable "wonky" optical serif with a hidden personality — at large display
sizes it reads authoritative; at smaller heading sizes its optical axis shifts and it
softens. That range exactly mirrors The Clean Cycle's positioning: serious enough to
earn trust, warm enough to feel like a neighbor.

The face was designed with the feel of a hand-set printer. That register says "craft,
care, made by human hands" — which is what cleaning IS. A family that cleans your home
with attention.

It does NOT say fintech. It does NOT say SaaS. It says: someone made this with pride.

**Usage**: h1, h2, section titles, pricing plan names, blockquote pull-quotes.
Weight 700 for hero headline. Weight 600 for section heads. Weight 300 for large
decorative numerals (trust stats). Letter-spacing: `-0.025em` at display, `-0.015em` at heading.

#### Body: IBM Plex Sans (complete family)
**URL**: `https://fonts.google.com/specimen/IBM+Plex+Sans`
**Weights loaded**: 400, 500, 600

**Why this face for this client:**
IBM Plex Sans was designed for one purpose: information density at small sizes in
technical documentation. For a cleaning landing page with checklist tables, pricing
rows, and service descriptions that need to be scannable on a phone screen — this is
exactly the right body face.

It has a gentle quirk (the angled terminals, the slightly narrow lowercase) that keeps
it from feeling like Inter or Roboto, while remaining utterly readable at 14px.
The "structured warmth" of Plex sits well against Fraunces's expressiveness.

Would I use IBM Plex Sans for a SaaS? Possibly — but a SaaS would pair it with a
modern grotesque display, not a wonky serif. The Fraunces/Plex Sans pairing is
specific to "skilled trade + reliable" and does not exist in SaaS design vocabulary. ✓

**Usage**: All body copy, UI labels, form fields, table cells, nav links, footer.
Weight 400 for prose. Weight 500 for UI labels and nav. Weight 600 for button text
and emphasis.

### Scale (major-third ratio, 1.25)
```
--text-xs:      0.64rem   (10px)   — legal, micro labels
--text-sm:      0.80rem   (13px)   — captions, checklist fine print
--text-base:    1.00rem   (16px)   — body prose
--text-md:      1.25rem   (20px)   — intro lede, large UI labels
--text-lg:      1.5625rem (25px)   — card headings, sub-section titles
--text-xl:      1.9531rem (31px)   — h3, section sub-heads
--text-2xl:     2.4414rem (39px)   — h2 section titles
--text-display: clamp(2.75rem, 5vw + 1rem, 4.5rem)  — hero h1 only
```

---

## 3. Layout system

### Grid
12-column, 24px gutters at ≥1024px. 16px gutters at 768px. Full fluid below 768px.

```
--grid-cols:     12
--grid-gutter:   1.5rem   (24px at ≥1024)
--grid-gutter-m: 1rem     (16px at 768)
--max-width:     1280px   (content)
--max-width-text: 65ch    (prose containers)
--page-inset:    clamp(1rem, 4vw, 5rem)  (left/right page padding)
```

### Breakpoints
```
xs:  320px   — smallest supported phone
sm:  768px   — tablet portrait, mobile nav collapses
md:  1024px  — tablet landscape, two-column layouts activate
lg:  1280px  — desktop, full 12-column grid
```

### Section spacing rhythm
Section padding is deliberately uneven — this is not a template.

```
--section-pad-hero:    5rem 0 4rem    (top-heavy: pulls into page)
--section-pad-default: 4.5rem 0 5rem  (slightly bottom-heavy: drops into next)
--section-pad-tight:   2.5rem 0 3rem  (trust strip, mobile bar)
--section-pad-flush:   0              (full-bleed sections that manage their own space)
```

### Asymmetric section layouts (minimum 2)

**Layout A — Services section (40 / 60 split)**
```
grid-template-columns: 2fr 3fr
```
Left column (40%): section label, section headline in Fraunces 600, 2-line intro
copy, a single teal "learn more" text-link at the bottom. Vertically centered in
the column. Sticky at `md+`.

Right column (60%): 2×2 service card grid. Cards are NOT equal — the first card
(Standard Clean) spans 2 columns at `md` as the hero card, the remaining 3 fill
the grid beneath. This is not 4 equal tiles.

**Layout B — Why Choose Us (reversed 60 / 40 split)**
```
grid-template-columns: 3fr 2fr
```
Left column (60%): A full-bleed photograph of a clean Arizona home interior (warm
light, Saltillo tile or wood tones — not a sterile white room). The photo bleeds
to the page edge on the left, breaking the grid intentionally.

Right column (40%): Numbered trust list — 5 items, each with a large Fraunces 300
numeral in navy, a short heading in Fraunces 600, and a 2-line explanation in
IBM Plex 400. No icons (icon tells — gate 30). Numbers only.

At `sm`, both layouts collapse to single column. Layout B places photo second
(copy leads on mobile).

### Not centred
Hero CTA and headline: left-aligned. Not centred.
Service cards section head: left-aligned with left margin breathing room.
Footer: left-aligned statement + right-aligned contact info (flex space-between).
Only the trust strip (§4) uses centred treatment, and only because it's a
horizontal carousel strip where centering serves the symmetry.

---

## 4. Component inventory

Each component gets one sentence of visual treatment — the "first draft of the
render" that code must match.

**Navbar**
Transparent with navy wordmark in Fraunces 600 on page-load; on scroll past 80px
it morphs into a floating pill (navy fill, cream text, teal CTA button), centered
in the viewport with `max-width: 900px` and `border-radius: 9999px` — NOT a full-
width bar. Reference: N5 (floating pill) from component cookbook.

**Hero**
Left-aligned asymmetric split: large Fraunces 700 headline (≤7 words) in navy on
the left two-thirds; right one-third holds an inline booking intake form (3 fields:
service type, address/zip, preferred date) with a teal CTA button. The signature
Cycle Mark (§5) sits as a decorative arc behind the CTA area. Hero background is
cream with a subtle half-circle teal shape bleeding off the top-right edge —
motivated decoration, not random. No full-screen photo. No `min-height: 100vh`.

**Trust strip**
Full-bleed navy background, single horizontal row: "Licensed · Bonded · Insured ·
5+ Years · 100+ East Valley Families · Eco-Friendly Products" — each item separated
by the 24px small Cycle Mark ornament in teal. Items in IBM Plex 500 all-caps cream
text, key numbers in Fraunces 300 cream (slightly oversized, tabular). Subtle left-
scroll marquee on mobile only.

**Service card**
Horizontal card (image thumbnail left, content right) on desktop; stacked on mobile.
Left edge has a 3px teal accent stroke (not a thick side-border — 3px only). Service
name in Fraunces 600, short description in IBM Plex 400. A "What's included" text
link that expands a checklist drawer inline (no separate modal). Background: cream;
on hover, lifts to cloud background. No shadow on default state — `box-shadow` only
on hover (1px hairline + whisper lift).

**Checklist table**
Two-column comparison: Standard Clean vs Deep Clean. Table rows in alternating cream /
cloud. First column has service item in IBM Plex 400. Second column (Standard) has
teal checkmark SVG or em-dash. Third column (Deep) has teal checkmark. Header row
in navy with cream text, Fraunces 600 for column heads. Table has `border-collapse:
collapse`, 1px sand borders. No rounded corners — tables are not cards.

**Pricing tab**
CSS-only `<input type="radio">` pattern for Residential / Commercial / Airbnb.
Three tabs; active tab: navy fill, cream text; inactive: cream fill, slate text,
sand border. Tab strip sits above the pricing table. Tabs use IBM Plex 500, not
all-caps. The radio inputs stay in normal flow (zero size, opacity 0) to prevent
scroll-jump — per gate 53.

**Pricing table**
Three pricing tiers as cards: Essential / Standard / Deep. Middle card (Standard)
is the recommended tier — navy fill, cream text, teal "Most Popular" badge at top.
Left and right cards: cream fill, navy text, sand border. Price in Fraunces 700
(tabular nums). Included items as IBM Plex 400 checkmark list. CTA button at bottom
of each card. Cards do NOT have equal heights — they size to content. At `sm`, stack
vertically; recommended card appears first.

**Review embed**
Pull-quote style: reviewer name in IBM Plex 600, location in IBM Plex 400 slate, star
rating as 5 teal SVG stars (one icon library only — Heroicons), quote text in Fraunces
300 italic (body prose only — italic permitted here per gate 38a which restricts italic
headings, not body quotes). Left border: 3px teal rule. Background: cloud. Three
reviews in a horizontal row at `md+`; single stacked at `sm`.

**Booking/Quote form**
Full inline form (not hidden behind a CTA): Name, Phone, Email, Service Type
(select), Home Size (select), Message (optional textarea), Submit. At `md+`, Name +
Phone on one row (grid 1fr 1fr), Email full-width, Service + Home Size on one row,
Message full-width. 44px input height minimum. Teal focus ring (`outline: 2px solid
var(--color-teal)`, `outline-offset: 2px`). Error state: border-color changes to
`#C0392B` (readable red); helper-text slot always reserves `min-height: 1lh` so
errors don't cause layout shift. Disabled state uses all three signals: opacity 0.55
+ `cursor: not-allowed` + native `disabled` attribute.

**Popup modal**
Triggered by "Get Free Quote" CTA in nav (mobile-primary). Contains a condensed
3-field version of the booking form. Navy overlay at 72% opacity. Modal panel: cream
background, `border-radius: 12px`, navy close button top-right. Focus trap on open;
Escape closes. Modal is NOT triggered on page load — only on user action.

**Footer**
Statement-style (Ft5): Large Fraunces 300 tagline left ("A clean home is a calm home.")
with navy text. Right column: address, phone, service area list in IBM Plex 400 small.
Bottom row: copyright + license info in IBM Plex 400 `--text-sm`. Background: navy.
All footer text: cream. Teal for links and phone number (hover: underline in teal).
No 4-column link grid. No social-icon row (they don't have active social worth linking).

**Mobile sticky bar**
Bottom-anchored on `sm` and below only. Contains: phone number (IBM Plex 600, cream)
on the left, "Book Now" CTA button (teal fill, navy text) on the right. Navy background.
Height: 56px. `position: fixed; bottom: 0; z-index: var(--z-sticky)`. Hides at `md+`.
Critically: `padding-bottom: env(safe-area-inset-bottom)` for iPhone home bar.

---

## 5. Signature element — The Cycle Mark

**The ONE decision that makes this page specific to The Clean Cycle AZ.**

A hand-drawn-quality SVG arc: 300° (not a closed circle), drawn as a single
`<path>` stroke in teal (`stroke: var(--color-teal)`), no fill, `stroke-width: 3`,
`stroke-linecap: round`. The arc is open at the lower-right — it suggests motion,
sweep, progress, and the idea that the cycle completes when you book. It's not
animated. It is static, confident, and unmistakably connected to:

1. The **brand name** — "Clean Cycle" → a cycle, literally
2. The **act of cleaning** — the sweep of a squeegee or mop across a surface
3. The **washing machine drum** — the circle of a cleaning cycle
4. **Arizona reliability** — like a sundial arc, it suggests a dependable rhythm that
   returns on schedule

**Where it appears — exactly three places:**
- **Hero**: 80px diameter, placed behind and to the right of the hero CTA button as
  a composition anchor. It makes the CTA feel "endorsed," like a quality stamp
  being completed.
- **Trust strip**: 20px diameter, used as the separator between each trust item
  instead of a dot or pipe character. Feels deliberate, not decorative.
- **Booking confirmation / form section heading**: 48px diameter, appearing left of
  the section heading "Ready for a cleaner home?" — implies the cycle is about
  to begin.

**What it is NOT:**
Not an animated spinner. Not a loading indicator. Not a logo. Not used on every
section. Not the same as the teal blob background many services use. Not a gradient.

**Anti-slop test**: Would I use a 300° open-arc SVG derived from the brand name for
a fintech? No. A fintech would use a closed circle (progress), a graph arc, or an
animated ring. This specific element only works when the company is NAMED "cycle"
and the work involves circular acts (cleaning schedules, recurring visits, machine
cycles). It fails the slop test — which means it passes. ✓

---

## 6. Anti-slop audit

Each major choice below is tested against the question: "Would I make this exact
same choice for a fintech or a SaaS startup?"

| Choice | Fintech/SaaS? | Verdict |
|---|---|---|
| Navy + teal color pairing | Possible — but fintech navy is darker (#0F2040), colder, no cream paper | Warm cream paper + cloud tint differentiates it. Keep. |
| Fraunces display face | Possible in premium fintech editorial — but not at wt 300 for numerals | Weight 300 numerals + warm serif = domestic, not financial. Keep. |
| IBM Plex Sans body | Developer tools, SaaS docs — yes | The PAIRING with Fraunces, the cleaning content, and the cream paper removes the tech feel. Monitor in code. |
| Cream + cloud surfaces | SaaS would use #F9FAFB (cool) not #F8F4EE (warm, sandy) | The hue angle (82 = warm sand) is what separates it. Enforce the hue angle. |
| Asymmetric 40/60 service layout | Common in SaaS feature sections | The content (service cards with checklists) is the differentiator, not the layout proportion. |
| Floating pill nav | SaaS agencies use this constantly | It works functionally; the navy fill + Fraunces wordmark prevents SaaS feel. If it reads generic in code, fall back to N6 (newspaper-masthead style). |
| Checklist comparison table | Strong SaaS pricing tell | In SaaS, checklists mean features. Here they mean "exactly what we clean." The table content makes it specific. |
| Cycle Mark ornament | CANNOT work for fintech or SaaS | Specific to brand name + cleaning act. ✓ |
| Footer with large tagline | Editorial/luxury — not SaaS | Family business voice, not product voice. Keep. |

**Revised after audit**: The biggest risk is the hero. An asymmetric left-headline +
right-form layout with a floating pill nav is close to SaaS hero territory. The
differentiators that must survive into code:
- Fraunces 700 in navy (not a modern grotesque)
- Cream background (not white)
- Booking form has home-specific fields (service type, home size)
- Cycle Mark arc behind the form area
- NO abstract background shapes other than the motivated teal half-circle at top-right

---

## 7. Competitor analysis — Fresh Finish AZ

**Source**: freshfinishaz.com (Scottsdale, Phoenix Metro competitor)

**What works (steal the conversion pattern, not the visual):**

- **Inline booking flow**: Service → day → time selection in the hero. High-intent
  visitors can start the booking without scrolling. The Clean Cycle AZ should embed
  a 3-field quote intake in the hero (not a modal) for the same reason.
- **Flat-rate pricing signal**: Explicitly calling out flat-rate pricing removes the
  "will they charge more on the day?" objection. Include this as a trust signal in
  the pricing section.
- **100% happiness guarantee**: Explicit, named guarantee. The Clean Cycle AZ should
  carry this as a named element — not buried in a paragraph, but as a visual badge
  in the trust strip.
- **Service type separation**: Distinct pages/sections for Standard / Deep / Move-Out
  / Airbnb. Visitors self-segment. The pricing tab system in §4 serves this.
- **Licensed/bonded/insured**: Surface it high on the page. The "I've been burned"
  homeowner needs to see this in the first scroll.

**What doesn't work (do the opposite):**

- **Generic palette**: Blue + white with no secondary surface color. Feels like any
  service business website. No warmth, no personality, no sense of "local family."
  → Our solution: cream surfaces + cloud tints + warm sand rules.
- **Centered everything**: Every section stacks on a centered axis. The page reads
  flat — there's no compositional tension or hierarchy of attention.
  → Our solution: left-aligned hero, asymmetric service/trust sections.
- **3-equal-column card grid**: Services presented as 3 identical icon-above-text
  tiles. This is the AI default and looks machine-generated.
  → Our solution: horizontal service cards, with the hero service card spanning full
  width in the grid.
- **No visual personality**: The page could belong to a pest control company, a lawn
  service, or a plumber. Nothing specific to cleaning or to Arizona.
  → Our solution: Cycle Mark, warm desert-toned palette, Fraunces headings that feel
  handcrafted.
- **Generic stock photos**: Sterile white kitchen with dramatic light. Feels curated,
  not local.
  → Our solution: Request photos from the client — actual homes they've cleaned in
  Gilbert/Chandler (warm interiors, Saltillo tile, AZ architecture). If stock must
  be used, brief toward warm-toned, occupied-feeling homes, not empty white boxes.

**Summary**: Fresh Finish AZ gets the conversion funnel right (inline booking, service
segmentation, explicit guarantees) but leaves all personality on the table. The Clean
Cycle AZ should match their conversion architecture and surpass their visual quality.

---

## 8. CSS token reference (for implementation)

```css
:root {
  /* Colors */
  --color-navy:     #1B365D;
  --color-teal:     #2ABFBF;
  --color-cream:    #F8F4EE;
  --color-cloud:    #EAF5F5;
  --color-slate:    #4A6B8A;
  --color-sand:     #CEC6B4;

  /* Hover / state (applied contextually, not standalone tokens) */
  --color-teal-hover:    #1FA8A8;
  --color-teal-active:   #178F8F;
  --color-navy-hover:    #14284A;
  --color-disabled-bg:   #C2CDD6;
  --color-disabled-text: #8E9FAC;
  --color-overlay:       rgba(27, 54, 93, 0.72);

  /* Typography */
  --font-display: "Fraunces", ui-serif, Georgia, serif;
  --font-body:    "IBM Plex Sans", ui-sans-serif, system-ui, sans-serif;

  /* Type scale — major third (1.25) */
  --text-xs:      0.64rem;
  --text-sm:      0.80rem;
  --text-base:    1.00rem;
  --text-md:      1.25rem;
  --text-lg:      1.5625rem;
  --text-xl:      1.9531rem;
  --text-2xl:     2.4414rem;
  --text-display: clamp(2.75rem, 5vw + 1rem, 4.5rem);

  /* Spacing — 4pt scale */
  --space-3xs: 0.125rem;   /*  2px */
  --space-2xs: 0.25rem;    /*  4px */
  --space-xs:  0.5rem;     /*  8px */
  --space-sm:  0.75rem;    /* 12px */
  --space-md:  1rem;       /* 16px */
  --space-lg:  1.5rem;     /* 24px */
  --space-xl:  2.5rem;     /* 40px */
  --space-2xl: 4rem;       /* 64px */
  --space-3xl: 6rem;       /* 96px */
  --space-4xl: 9rem;       /* 144px */

  /* Layout */
  --max-width:      1280px;
  --max-width-text: 65ch;
  --page-inset:     clamp(1rem, 4vw, 5rem);
  --banner-height:  64px;   /* nav height for sticky offsets */

  /* Z-index scale */
  --z-base:        1;
  --z-raised:      10;
  --z-dropdown:    100;
  --z-sticky:      200;
  --z-sticky-nav:  300;
  --z-modal:       400;
  --z-toast:       500;

  /* Motion */
  --ease-out:  cubic-bezier(0.16, 1, 0.3, 1);
  --dur-fast:  180ms;
  --dur-base:  240ms;
  --dur-slow:  320ms;

  /* Radius */
  --radius-card:  8px;
  --radius-pill:  9999px;
  --radius-input: 6px;
  --radius-modal: 12px;
}
```

---

## 9. Open questions for the client

These must be answered before the hero and service sections can be finalized.

1. **Photos**: Do you have real photos of homes you've cleaned in Gilbert/Chandler/AZ?
   If not, what stock direction should we take? (Warm interiors? Before/after shots?)
2. **Services list**: The confirmed list from the site is Standard, Deep, Move-Out,
   Airbnb/Short-Term Rental, Commercial — is this complete? Any specialty services
   (post-reno, holiday prep)?
3. **Pricing**: Are prices on the current site current? Will they be displayed on
   the new page, or is it quote-only?
4. **Social proof**: How many Google reviews? Can we use exact review text with
   permission? (Required before the review section can be populated)
5. **Guarantee**: Do you offer a named guarantee (re-clean within 24h, refund policy)?
   This needs a real commitment statement, not marketing copy.
6. **Service area**: The current site lists 9 cities. Should the landing page target
   a primary city (Gilbert) or all cities equally?

---

*Spec complete. No HTML written. Implementation begins in Phase 2.*
