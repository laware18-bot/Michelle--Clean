# The Clean Cycle AZ — Website Redesign Project

## PROJECT OVERVIEW
Build a single-page HTML website from scratch for The Clean Cycle AZ, a residential cleaning company in Gilbert, Arizona. The page must convert visitors into leads and look like it was designed by a professional human studio — NOT by AI.

**Output:** One single `index.html` file with all CSS and JS embedded inline. Compatible with GoHighLevel (GHL) custom pages. No external CSS/JS files. No React. No build tools. Plain HTML/CSS/JS only.

**Domain:** thecleancycleaz.com (existing, hosted on GHL)

---

## CLIENT CONTEXT
- **Business:** The Clean Cycle AZ — residential & commercial cleaning
- **Owner:** Michele
- **Location:** Gilbert, Arizona (serves East Valley: Gilbert, Chandler, Mesa, Scottsdale, Phoenix, Queen Creek)
- **Phone:** (602) 610-0059
- **Logo:** https://assets.cdn.filesafe.space/yClPU8JfUYTPBosdlZfn/media/67293b5fce0095653cb8d153.png
- **GBP Rating:** 4.9 stars on Google
- **Recurring clients:** 25+ East Valley families
- **Frequency options:** Weekly, Bi-Weekly, or Monthly

---

## SERVICES (exactly 5 — no more, no less)

1. **Residential Cleaning** — Weekly, bi-weekly & monthly recurring cleaning
2. **Deep Cleaning** — Intensive one-time cleaning for homes needing extra attention
3. **Move In / Move Out Cleaning** — Full clean for transitions, deposit recovery
4. **Short Term Rental Cleaning** — Fast turnovers between guests (DO NOT say "Airbnb" anywhere)
5. **Post-Construction Cleanup** — Dust, debris, paint removal after renovations

**REMOVED:** Power Washing — DO NOT include this service anywhere on the page.
**REMOVED:** "Remodeling Cleaning" — consolidated into Post-Construction.

---

## PRICING DATA

### Standard Cleaning (Recurring)
| Home Size (sqft) | Weekly | Bi-Weekly | Monthly |
|---|---|---|---|
| 0–749 | $110 | $115 | $140 |
| 750–999 | $120 | $130 | $155 |
| 1,000–1,249 | $130 | $145 | $170 |
| 1,250–1,499 | $140 | $160 | $190 |
| 1,500–1,799 | $155 | $175 | $210 |
| 1,800–2,099 | $165 | $195 | $230 |
| 2,100–2,399 | $175 | $210 | $250 |
| 2,400–2,699 | $190 | $225 | $270 |
| 2,700–2,999 | $205 | $240 | $290 |
| 3,000–3,299 | $220 | $255 | $315 |
| 3,300–3,599 | $235 | $270 | $340 |
| 3,600–3,899 | $250 | $285 | $365 |
| 3,900–4,199 | $265 | $300 | $390 |
| 4,200–4,499 | $280 | $315 | $415 |
| 4,500–4,999 | $295 | $330 | $440 |
| 5,000–5,299 | $310 | $345 | $465 |

### Deep Cleaning
| Home Size (sqft) | Price |
|---|---|
| 0–749 | $170 |
| 750–999 | $185 |
| 1,000–1,249 | $205 |
| 1,250–1,499 | $225 |
| 1,500–1,799 | $245 |
| 1,800–2,099 | $290 |
| 2,100–2,399 | $320 |
| 2,400–2,699 | $375 |
| 2,700–2,999 | $435 |
| 3,000–3,299 | $500 |
| 3,300–3,599 | $570 |
| 3,600–3,899 | $620 |
| 3,900–4,199 | $680 |

### Move Out Cleaning
| Home Size (sqft) | Price |
|---|---|
| 0–749 | $197 |
| 750–999 | $217 |
| 1,000–1,249 | $239 |
| 1,250–1,499 | $265 |
| 1,500–1,799 | $289 |
| 1,800–2,099 | $340 |
| 2,100–2,399 | $375 |
| 2,400–2,699 | $440 |
| 2,700–2,999 | $510 |
| 3,000–3,299 | $590 |
| 3,300–3,599 | $670 |
| 3,600–3,899 | $730 |
| 3,900–4,199 | $800 |

### Short Term Rental Turnover
| Beds | Up to 1,500 sqft | 1,501–2,000 sqft | 2,001–2,500 sqft |
|---|---|---|---|
| 1–2 Beds | $135 | $150 | $165 |
| 3 Beds | $150 | $170 | $190 |
| 4 Beds | $175 | $195 | $220 |
| 5 Beds | $225 | $255 | $290 |
| 6 Beds | $275 | $310 | $350 |

Note: 6+ beds or 2,500+ sqft require custom quote.

**PRICING DISPLAY RULE:** On the public page, show prices as "Starting at $X" using the lowest price in each category. The full detailed tables are shown in a tabbed expandable section.

---

## PAGE SECTIONS (in order, top to bottom)

### 1. NAVBAR (sticky)
- Logo (left)
- Nav links: Home | Services | Pricing | Reviews | Contact
- Phone number visible on desktop: (602) 610-0059
- "Book Now" CTA button (scrolls to quote form)
- Mobile: hamburger menu
- Sticky on scroll with subtle shadow

### 2. HERO
- Full-width background image (clean, bright Arizona home interior — NOT the ugly current one)
- Dark overlay on image for text readability
- Headline (bold, large, white)
- Subheadline mentioning service areas
- Trust strip below headline: "4.9 ⭐ Google Rating | Licensed & Insured | Weekly, Bi-Weekly & Monthly Plans"
- Primary CTA: "Get $50 Off Your First Cleaning" (triggers popup modal)
- Secondary CTA: "View Our Services ↓" (scrolls down)
- Phone number visible

### 3. SERVICES SECTION
- 5 service cards in responsive grid
- Each card: icon + title + 3 short bullets + "Learn More" link
- Clean white cards with subtle shadow
- NO Power Washing. NO "Airbnb" text anywhere.

### 4. SERVICE CHECKLISTS (like FreshFinish)
- Tabbed interface: Kitchen | Bathroom | Bedrooms | Common Areas
- Each tab shows a table with columns: Task | Standard | Deep | Move In/Out
- Checkmarks (✓) and X marks (✗) for each task per service type
- This shows transparency and justifies pricing
- Reference: https://freshfinishaz.com/services/ for the exact pattern

### 5. PRICING SECTION
- Tabbed by service type: Standard | Deep | Move Out | Short Term Rental
- Show "Starting at $X" prominently for each service
- Below the "Starting at" headline, show the full pricing table by square footage
- First 6-8 rows visible, remaining rows behind a "See all sizes" toggle
- Tables scroll horizontally on mobile
- CTA banner below: "Not sure which service? We'll help." + Get a Free Quote button

### 6. REVIEWS SECTION
- Header: "What Our Clients Say"
- Badge: "4.9 ⭐⭐⭐⭐⭐ on Google"
- GHL reviews widget embed:
  `<iframe src="https://app.thecleancycleaz.com/reputation/widgets/review_widget/yClPU8JfUYTPBosdlZfn?widgetId=67d48f08104179349f9c7813" width="100%" height="600" frameborder="0" style="border:none;"></iframe>`
- "See All Reviews on Google" link button

### 7. QUOTE FORM
- Dark background section (navy)
- Heading: "Get Your Free Quote in 24 Hours"
- 6 fields exactly:
  1. Full Name (text, required)
  2. Phone Number (tel, required)
  3. Email Address (email, required)
  4. Zip Code (text, required, maxlength 5)
  5. Service Type (dropdown: Residential Cleaning | Deep Cleaning | Move In/Move Out | Short Term Rental | Commercial Cleaning | Post-Construction Cleanup)
  6. Message / Notes (textarea, optional)
- Submit button: "Request My Free Quote →"
- Form id="quote-form-main" with data-ghl-form="true"
- DO NOT include: square feet field, street address field

### 8. FOOTER
- Dark navy background
- 4 columns: Company Info | Services | Service Areas | Quick Links
- Phone, email placeholder, logo
- Copyright 2025 + "Licensed & Insured"

### 9. POPUP MODAL — $50 OFF LEAD MAGNET
- Triggers after 3 seconds on page load
- Also triggered by hero CTA button click
- Design: matches The Perfect Clean popup layout EXACTLY but in Clean Cycle brand colors
- Small sparkle/star icon at top center
- Heading: "Get $50 Off Your First Cleaning!"
- Subtext: "Join 25+ East Valley families who trust us with their homes every week."
- 3 form fields:
  1. Full Name * (required)
  2. Phone Number * (required)
  3. Email Address * (required)
- CTA button: "Claim My $50 Off"
- Small disclaimer: "By submitting, you agree to receive promotional communications."
- X close button top-right
- localStorage prevents re-showing same session
- Form id="popup-lead-form" with data-ghl-form="true"

### 10. LIVE CHAT WIDGET (placeholder)
- Add placeholder comment before </body>:
  `<!-- TODO: Replace with GHL Live Chat widget embed code from GoHighLevel > Sites > Chat Widget -->`
- Add a simple floating chat icon button (bottom-right) that links to tel:(602)610-0059 as temporary fallback

### 11. STICKY MOBILE BAR (mobile only)
- Fixed bottom bar, visible only on screens < 768px
- Two buttons side by side: "📞 Call Now" (tel link) + "📋 Get Quote" (scrolls to form)
- Semi-transparent background, subtle shadow

---

## DESIGN REFERENCES

### Primary reference (structure + credibility elements):
- https://freshfinishaz.com/ — clean layout, trust badges, reviews, service cards with icons, booking section

### Secondary reference (popup + pricing):
- https://theperfectclean.com/ — $50 off popup, pricing by sqft, lead magnet approach

### Current site (what to improve from):
- https://www.thecleancycleaz.com/home — use existing logo and brand foundation, but redesign everything else

---

## BRAND GUIDELINES

### Colors
- Primary Navy: #1B365D (from logo)
- Accent Teal: #2ABFBF (from logo accent)
- White: #FFFFFF
- Light Background: #F7F9FC
- Dark Text: #1A1A2E
- Warm Gray: #6B7280
- Success Green: #10B981 (for checkmarks)
- Footer Dark: #0F2440

### Typography
DO NOT use: Inter, Roboto, Arial, Space Grotesk, system fonts.
Choose a distinctive but professional pairing appropriate for a local service business. Consider:
- Display: Something with warmth and authority (Playfair Display, DM Serif Display, Lora, or similar serif)
- Body: Something clean and highly readable (DM Sans, Source Sans 3, Outfit, or similar sans-serif)
- Utility: Same as body but at smaller weights for labels/captions

### Imagery
- Use high-quality photos of clean, bright Arizona-style home interiors
- Unsplash free images are acceptable
- NO generic stock photos with fake smiling people in cleaning uniforms
- Show results, not workers: sparkling kitchens, organized spaces, bright bathrooms

---

## ANTI-SLOP RULES (CRITICAL)

The page MUST NOT look AI-generated. Specifically avoid:
1. Everything centered symmetrically — use asymmetric layouts where appropriate
2. Uniform padding/spacing everywhere — vary the rhythm between sections
3. Gradient backgrounds (especially purple, pink, or blue-to-purple gradients)
4. Numbered markers (01, 02, 03) unless content is actually sequential
5. Generic headlines like "Unlock the power of..." or "Transform your..."
6. Emoji as bullet points in body content
7. Cards with colored left border as the only visual device
8. Cookie-cutter hero with big text + subtitle + button centered on gradient
9. Same card layout repeated for every section
10. Decorative elements that serve no informational purpose

What TO do instead:
- Mix text-left/image-right with image-left/text-right layouts
- Use real content and specific Arizona/East Valley references
- Let whitespace do the work instead of borders and dividers
- Make the pricing table the hero of the pricing section (it IS the content)
- Use one bold design decision (the "signature") and keep everything else quiet

---

## TECHNICAL REQUIREMENTS

- Single `index.html` file, all CSS in `<style>`, all JS in `<script>`
- Google Fonts loaded via `<link>` in `<head>`
- CSS custom properties (variables) for all colors and fonts
- Mobile-first responsive design (320px → 1440px)
- Smooth scroll for anchor links
- No external dependencies except Google Fonts
- Forms must have proper validation (required fields, email format, phone format)
- All images via external URLs (Unsplash or existing CDN assets)
- Comment `<!-- GHL CUSTOM PAGE -->` at top of file
- `<meta charset="utf-8">` and `<meta name="viewport" content="width=device-width, initial-scale=1">`
