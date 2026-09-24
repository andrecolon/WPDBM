# Page Spec — Dream Book Marketing One-Pager

Source: `docs/assets/reference-full-page.webp`. Colors are estimated by eye from the screenshot
and labeled `(est.)` — swap in exact brand hex codes if/when a brand guide shows up. Copy is
transcribed verbatim; treat it as final unless told otherwise.

## Global design tokens (set once in Elementor Site Settings)

**Colors**
| Token | Hex (est.) | Used for |
|---|---|---|
| Ink / Black | `#151515` | headlines, body text, footer bar, nav |
| Cyan accent | `#3FC1E0` | "DISCOVERED" headline word, button shadow offsets, tag pills |
| Dark section bg | `#1E1E1E` | quote band, "Don't wait" band |
| Gold / CTA bg | `#E9C36C` | bottom "Have a book to market?" band |
| Body gray | `#4A4A4A` | paragraph copy on white sections |
| Off-white bg | `#FFFFFF` | default page background |
| Muted gray (dark-section body) | `#B8B8B8` | paragraph text inside dark sections |

**Type**
Two families are in play — get exact font files from the designer/brand guide if this is a
redesign of an existing live site; otherwise these are the closest free substitutes:

- **Display / heavy headlines** (hero H1, dark-section headlines, gold CTA headline): a bold
  condensed/compressed grotesk. Closest Google Fonts: `Archivo Black` or `Anton` for weight,
  `Archivo Expanded 800` if less condensed is needed. Used at very large sizes, tight
  line-height, all-caps in the hero.
- **Secondary headlines** ("A complete marketing mix…", "Meet Darcy Hughes."): a plain rounded
  grotesk, sentence case. Closest: `Inter` (600) or system `Helvetica Neue`.
- **Serif italic** (intro line "You dreamed it. You wrote it…", pull quotes): closest: `PT Serif`
  italic or `Georgia` italic, bold weight for the intro line.
- **Serif body copy** (paragraphs under the hero, bio paragraph): same serif family, regular
  weight, not italic.
- **Labels / nav / buttons / overlines**: the display sans, small size, uppercase, letter-spaced
  (e.g. `INDEPENDENT BOOK MARKETING · SINCE 2016`, `WHAT WE DO`, `EXPERIENCED GUIDANCE`).

**Spacing**: generous white space between sections (~80–120px vertical padding per section on
desktop); content max-width appears constrained to roughly 1140–1200px, centered.

---

## Section-by-section

### 1. Header / nav
- Logo left: "DBM" stacked over "DREAM BOOK MARKETING" (small), black.
- Nav center-right: `SERVICES` `APPROACH` `ABOUT` — small caps, black, no underline.
- Button right: `LET'S MARKET YOUR BOOK →` — black bg, white text, small cyan bottom-right
  border/shadow offset (the "offset box" effect appears throughout — a solid cyan rectangle sits
  behind-and-offset from black-bg buttons).
- Thin black hairline rule under the whole header.
- Elementor: Header section, `Flexbox container`, sticky optional (not clearly sticky in the
  screenshot — default to static unless asked).

### 2. Hero
- Eyebrow: `INDEPENDENT BOOK MARKETING · SINCE 2016` — small bold uppercase, letter-spaced.
- H1, two lines, tight leading, all-caps, display font, ~64–72px desktop:
  - Line 1 (black): `YOUR BOOK IS PUBLISHED.`
  - Line 2 (cyan accent): `NOW LET'S GET IT DISCOVERED.`
- Right-aligned (or below on mobile) copy block:
  - Bold serif italic lead: `You dreamed it. You wrote it. You published it.`
  - Serif paragraph: `Now comes the part that too many authors are expected to figure out on their own: how to get the right readers to find it.`
  - Serif paragraph: `Dream Book Marketing helps authors and independent publishers turn a finished book into a strategic, professional marketing campaign — without wasting time and money on promotion that doesn't make sense for the book.`
  - Serif paragraph: `From Amazon optimization and book launches to podcast outreach, awards, reviews, websites, advertising, and long-term promotion, we create a plan around your book, your audience, and your goals.`
  - Button: `LET'S MARKET YOUR BOOK →` (same black/cyan-offset style as header button).
- Elementor: two-column layout (headline left ~55%, copy right ~45%) or stacked with headline
  full-width above copy block, depending on how close to the screenshot's exact grid you want —
  screenshot shows headline occupying left ~45% width with copy stacked to its right/below.

### 3. Stats bar
- Full-width, 3-column bordered box (thin gray/black hairline borders between + around cells).
- Each cell: big bold black number + small caption, e.g.:
  - `70` — `BOOK AWARDS EARNED`
  - `#1` — `NEW RELEASE RESULTS`
  - `10+` — `YEARS OF EXPERIENCE`
- White background, sits directly under hero.

### 4. Quote band (dark)
- Full-width dark section (`#1E1E1E` est.), two-column, thin vertical divider between.
- Column 1: serif italic quote, white/light text —
  `"So many of our dreams at first seem impossible, then they seem improbable, and then, when we summon the will, they soon become inevitable."`
  Attribution below, small uppercase: `— CHRISTOPHER REEVE`
- Column 2: serif italic quote —
  `"No matter what people tell you, words and ideas can change the world."`
  Attribution: `— JOHN KEATING, DEAD POETS SOCIETY`

### 5. "What we do" — services grid
- Small overline label: `WHAT WE DO`
- Headline (secondary/rounded font, sentence case, large):
  `A complete marketing mix, built around your book.`
- 6-cell bordered grid, 3 columns × 2 rows, thin hairline borders, numbered `01`–`06` small at
  top-left of each cell:
  1. **BOOK REVIEWS** — Professional reviews you can use on your cover, website, social media, and Amazon page.
  2. **AWARD CONTESTS** — Strategic contest selection and submission support to build authority and author credibility.
  3. **TESTIMONIALS** — Outreach to experts, colleagues, and trusted voices whose endorsements strengthen your launch.
  4. **SOCIAL MEDIA** — Connect with specialists who can turn the right platforms into meaningful exposure for your book.
  5. **AUTHOR WEBSITES** — A professional home for your book, biography, launch news, and clear purchase information.
  6. **PROMOTIONAL DESIGN** — Postcards, bookmarks, posters, flyers, business cards, and ads made to travel.
  - Each cell ends with a small underlined link: `EXPLORE SERVICE →`

### 6. "Don't wait until publication day" (dark)
- Same dark bg as section 4. Overline: `A SMARTER LAUNCH`
- Headline, white, secondary font: `Don't wait until publication day.`
- 3-column bordered grid (dark gray hairline borders), each cell:
  - Small cyan pill/tag top-left (looks like a short label — screenshot shows abbreviations,
    likely `01` / `02` / `03` or short words like `WHO` / `WHY` / `WHEN` — verify exact tag text
    against the live screenshot at full resolution before building; transcribe precisely once
    confirmed).
  - Bold white sub-headline
  - Small light-gray paragraph
  1. **CHOOSE YOUR CHANNELS** — Build a balanced plan across reviews, social media, websites, PR, events, and outreach.
  2. **GIVE PEOPLE A REASON TO CARE** — Reach bloggers, influencers, experts, and early readers who can amplify the story.
  3. **START BEFORE LAUNCH** — Establish your author presence and audience months before the book becomes available.

### 7. Bio — "Meet Darcy Hughes"
- Overline: `EXPERIENCED GUIDANCE`
- Headline (secondary font): `Meet Darcy Hughes.`
- Left: square-ish headshot photo (needs source file — see SETUP.md).
- Right: serif paragraph —
  `Darcy brings a background in development and marketing from New York's Fashion Institute of Technology, followed by years of research, brand promotion, event management, Amazon optimization, and bookstore, media, distributor, and library outreach.`
  `She works with every author to find the marketing opportunities that fit their niche, goals, and budget.`

### 8. CTA band (gold)
- Full-width gold/mustard bg (`#E9C36C` est.).
- Large black display headline: `HAVE A BOOK TO MARKET?`
- Paragraph, mixed regular/bold: `Whether you're preparing to launch, trying to revive a book that's already published, or simply wondering **what you should be doing next**, we can help you create a plan.`
- Button: `TELL US ABOUT YOUR BOOK →` — white bg, black border/text, small black offset shadow
  (inverse of the black buttons elsewhere).
- Right-aligned contact block: name (`Susan Shankin` per screenshot — verify spelling/role
  against source) + email link below it.

### 9. Footer
- Thin black bar, 3-column small text:
  - Left: `DBM / DREAM BOOK MARKETING`
  - Center: `POWERED BY PRECOCITY PRESS`
  - Right: `© 2024` (confirm/update year at build time)

---

## Open items before pixel-accurate build

- Confirm exact tag text in section 6's three pill labels (image resolution made them small).
- Confirm contact name/role in section 8.
- Real logo, headshot, and brand hex/fonts per `docs/SETUP.md` §6.
- Confirm whether this is a rebuild of an existing live DBM site (the footer references
  "Precocity Press" as a platform, suggesting the current site may already be live somewhere) —
  if so, treat that live site as the authoritative source for anything ambiguous here, not just
  this screenshot.
