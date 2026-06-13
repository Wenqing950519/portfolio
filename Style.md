# Portfolio Style Guide

This document defines the visual system for the portfolio program and the project detail pages.

## Core Mood

The site should feel like a crafted portfolio deck: editorial, warm, strategic, and slightly playful. It should avoid generic SaaS glassmorphism and instead use paper-like surfaces, dense typography, angled color planes, and collectible card interactions.

Keywords:

- Editorial portfolio
- Tarot card / collectible card reveal
- Cream paper, deep green ink, coral accent
- Structured but not corporate
- Energetic proof-of-work storytelling

## Color System

Use these tokens as the source of truth:

```css
--paper: #f6efe4;
--paper-2: #fffaf0;
--ink: #15241f;
--muted: #607067;
--forest: #20493b;
--forest-2: #163227;
--coral: #e87b5f;
--ochre: #d8a54a;
--blue: #345edb;
--mint: #9bc8bd;
--line: rgba(21,36,31,.16);
```

Usage:

- `paper` is the global page background.
- `paper-2` is used for cards, panels, and readable surfaces.
- `forest` and `forest-2` are primary dark blocks and text anchors.
- `coral` is the main action/accent color.
- `blue`, `ochre`, and `mint` are supporting project-card colors.
- Avoid one-note palettes. Every major section should include at least one warm accent and one dark anchor.

## Typography

Font stack:

```css
font-family: 'Inter','Noto Sans TC',-apple-system,'PingFang TC','Microsoft JhengHei',sans-serif;
```

Rules:

- Hero titles use heavy weight, tight line-height, and no negative letter spacing.
- Section labels are small uppercase-style markers with a coral rule.
- Body copy should remain readable and calm: 14-17px, muted green-gray, generous line-height.
- Buttons and tags use strong font weight to feel like labels on a designed artifact.

## Global Layout

The site uses:

- Fixed floating nav with paper background and subtle border.
- Cream grid/noise background.
- Full-width sections with constrained inner content.
- No nested cards. Use cards only for actual repeated items, panels, and project artifacts.

Hero pattern:

- Left side: name, short description, CTA buttons.
- Right side: layered portfolio-window composition.
- After hero: a centered scroll cue, not a data strip.

## Project Card System

Cards represent selected works and behave like a tarot spread.

Structure:

- `.work-rail` holds all project cards.
- `.project-window` is the card.
- `.project-top` is the color field/art area.
- `.project-tag`, title, description, meta chips, and optional link label sit inside the card.

Desktop behavior:

- Cards overlap in a fan.
- JavaScript computes `--fan-rot`, `--fan-y`, and `--fan-z` based on card count.
- Hover/focus lifts the card upward, scales slightly, and brings it to the top.

Mobile behavior:

- Cards become a single readable column.
- No overlap.
- Hover/focus still gives a small upward lift when available.

Adding cards:

- Add a new item in `window.SITE_CONTENT.work.items`.
- The fan layout recalculates automatically.
- Use `link: "project-page.html"` for internal detail pages.
- Use `link: "https://..."` for external links.
- Internal links open in the same tab; external links open in a new tab.

## Detail Page System

Project detail pages should not reuse the homepage card layout. They should use a separate editorial service-page structure inspired by minimal Japanese portfolio pages:

- Lots of cream negative space.
- Small top navigation, not the floating card nav from the homepage.
- Oversized hero title with one italic word.
- A right-side abstract visual block.
- Circular/rotating decorative text may be used sparingly.
- Content sections use numbered rows, alternating image/color block and text.
- Detail links use a thin horizontal rule followed by small `View Detail` text.

Only the color distribution should connect back to the main interface: cream base, deep green text, coral accent, blue geometric field, ochre small block.

Recommended structure:

1. Minimal top nav
   - Brand/name on the left.
   - Small text links on the right.
   - No heavy container or floating card treatment.

2. Editorial hero
   - Huge title, for example `ATCC Case.`
   - One short bold Japanese/Chinese-style project sentence.
   - Small muted English descriptor.
   - One dark rectangular CTA.
   - Right-side abstract color image/card.

3. Contribution/service section
   - Header in uppercase English, such as `CONTRIBUTION`.
   - Intro paragraph.
   - Numbered rows: `01`, `02`, `03`, `04`.
   - Rows alternate visual block/text alignment.
   - Each row explains one concrete contribution.

4. Process section
   - Same row system.
   - Use shorter process labels: Research, Strategy, Prototype, Pitch.

5. Impact section
   - Sparse metrics, not boxed stat cards unless needed.
   - Use horizontal rules and strong numbers.

6. Closing reflection
   - A quiet text block with top/bottom rules.
   - Return button back to works.

## Detail Page Visual Blocks

Use these blocks consistently:

- `top-nav`: small detail-page nav.
- `hero`: large opening section.
- `visual-stage`: right-side visual container.
- `visual-card`: abstract project image/color block.
- `section-head`: uppercase section heading area.
- `service-row`: alternating numbered detail row.
- `service-art`: abstract image/color block.
- `service-copy`: row text content.
- `view-line`: thin line plus label link.
- `impact`: sparse result metric area.

Style:

- Avoid boxed dashboards.
- Avoid repeating homepage tarot-card shapes inside detail pages.
- Keep corners sharp.
- Prefer whitespace and alignment over heavy borders.
- Use shadows only on visual blocks or CTA buttons.
- Use decorative geometry instead of stock imagery when no real project screenshots exist.

## Content Writing Rules

Cards:

- 1 short tag
- 1 strong title
- 1 concise paragraph
- 2-4 meta chips
- Optional link label

Detail pages:

- Use first-person sparingly.
- Prefer concrete contribution statements.
- Separate role, process, result, and reflection.
- Avoid vague claims like "responsible for everything" unless followed by specifics.

Example contribution wording:

- Market analysis and competitor framing
- Strategy proposal and MVP concept
- Pitch deck structure and live presentation
- Enterprise visit and feedback synthesis

## Admin Workflow

The content source is `content.js`.

To edit normal cards:

1. Open `admin.html`.
2. Edit or add items in the Work section.
3. Save back to `content.js`.
4. Refresh `index.html`.

To add a project detail page:

1. Create a new HTML file, for example `finance-labs.html`.
2. Follow the Detail Page System above.
3. In `admin.html`, set that card's link to the file name.
4. Set the link label to something like `查看專案`.

The current homepage reads the Chinese fields. English fields remain in `content.js` for a future bilingual version.
