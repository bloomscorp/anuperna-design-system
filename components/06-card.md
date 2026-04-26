# Card

The card is a contained surface that groups related content. It is the base molecule from which more specific cards (product card, editorial card, metric card) are composed. Cards do not have a fixed width — they fill their grid column.

---

## Anatomy

```
┌────────────────────────────────┐
│                                │  ← Image area (optional)
│         [image]                │
│                                │
├────────────────────────────────┤
│ Badge / category label         │  ← Card header (optional)
│ Title                          │
├────────────────────────────────┤
│ Body text or content           │  ← Card body
│                                │
├────────────────────────────────┤
│ [Action]           [Action]    │  ← Card footer (optional)
└────────────────────────────────┘
```

| Part | Spec |
|---|---|
| Border radius | `6px` |
| Default padding (no image) | `24px` |
| Compact padding | `16px` |
| Image — aspect ratio (product) | `3:4` portrait |
| Image — aspect ratio (editorial) | `16:9` landscape |
| Image — aspect ratio (square) | `1:1` |
| Image fit | `object-fit: cover` |
| Gap between header, body, footer | `16px` |

---

## Variants

### Elevated
White background with a soft shadow. Use on white or near-white page backgrounds where the card needs to lift off the surface.

- Background: `#FFFFFF`
- Border: none
- Shadow: `0 2px 8px rgba(0, 0, 0, 0.06)`

### Outlined
White background with a subtle border. Use when shadow would feel too heavy — dense grids, tables of cards.

- Background: `#FFFFFF`
- Border: `1px solid #EAEBF1`
- Shadow: none

### Surface
Tinted pastel background, no border or shadow. Use to create section-level groupings or to colour-code content by type. Choose the surface that fits the surrounding section.

| Surface | Background |
|---|---|
| Rose | `#F9F4F5` |
| Sage | `#E9F1ED` |
| Lavender | `#EBE9F2` |
| Mist | `#EAEBF1` |

---

## Interactive State

Cards that are clickable (link to a detail page) have a hover state. Cards that are purely informational do not.

| State | Elevated | Outlined | Surface |
|---|---|---|---|
| Hover | Shadow deepens to `0 6px 20px rgba(0, 0, 0, 0.10)` | Border becomes `1px solid #AAC9BA` | Background darkens to the matching foreground pastel at 10% opacity — use `filter: brightness(0.97)` |
| Transition | `all 0.2s ease-in-out` | `all 0.2s ease-in-out` | `all 0.2s ease-in-out` |
| Cursor | `pointer` | `pointer` | `pointer` |

---

## Compositions

### Feature card
Used on landing pages to describe a capability, service, or value proposition. Icon + title + short description. No image, no footer.

```html
<div class="fb-card fb-card--surface fb-card--sage">
  <div class="fb-card__body">
    <span class="material-symbols-outlined fb-card__icon">handshake</span>
    <h3 class="fb-card__title">Wholesale Partners Program</h3>
    <p class="fb-card__text">
      Trade pricing, custom development support, and dedicated account management for B2B partners.
    </p>
  </div>
</div>
```

### Editorial card
Used for press mentions, blog posts, or news items. Landscape image + category tag + title + excerpt.

```html
<div class="fb-card fb-card--outlined">
  <div class="fb-card__image fb-card__image--landscape">
    <img src="article-image.jpg" alt="Article title" />
  </div>
  <div class="fb-card__body">
    <div class="fb-card__header">
      <span class="fb-badge fb-badge--neutral">Press</span>
    </div>
    <h3 class="fb-card__title">Anuprerna featured in Meaningful Business</h3>
    <p class="fb-card__text">
      Recognised for sustainable manufacturing practices and fair trade commitments across the supply chain.
    </p>
  </div>
  <div class="fb-card__footer">
    <button class="btn-ghost">
      Read More
      <span class="btn-ghost-arrow"></span>
    </button>
  </div>
</div>
```

### Metric card
Used for impact numbers, stats, or key figures. No image, large number as the focal point.

```html
<div class="fb-card fb-card--surface fb-card--lavender">
  <div class="fb-card__body fb-card__body--center">
    <span class="fb-card__metric">12,400</span>
    <p class="fb-card__text">Artisan hours supported this year</p>
  </div>
</div>
```

---

## CSS Reference

```css
/* ─── Base card ─── */

.fb-card {
  display: flex;
  flex-direction: column;
  border-radius: 6px;
  overflow: hidden;
  transition: all 0.2s ease-in-out;
}

/* ─── Variants ─── */

.fb-card--elevated {
  background-color: #FFFFFF;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
}

.fb-card--elevated:is(a, [role="button"], [tabindex]):hover {
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.10);
  cursor: pointer;
}

.fb-card--outlined {
  background-color: #FFFFFF;
  border: 1px solid #EAEBF1;
}

.fb-card--outlined:is(a, [role="button"], [tabindex]):hover {
  border-color: #AAC9BA;
  cursor: pointer;
}

/* Surface variants */
.fb-card--surface { border: none; box-shadow: none; }
.fb-card--rose      { background-color: #F9F4F5; }
.fb-card--sage      { background-color: #E9F1ED; }
.fb-card--lavender  { background-color: #EBE9F2; }
.fb-card--mist      { background-color: #EAEBF1; }

.fb-card--surface:is(a, [role="button"], [tabindex]):hover {
  filter: brightness(0.97);
  cursor: pointer;
}

/* ─── Image area ─── */

.fb-card__image {
  width: 100%;
  overflow: hidden;
  flex-shrink: 0;
}

.fb-card__image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.4s ease-in-out;
}

.fb-card:hover .fb-card__image img {
  transform: scale(1.03);
}

/* Aspect ratios */
.fb-card__image--portrait   { aspect-ratio: 3 / 4; }
.fb-card__image--landscape  { aspect-ratio: 16 / 9; }
.fb-card__image--square     { aspect-ratio: 1 / 1; }

/* ─── Body ─── */

.fb-card__body {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 24px;
  flex: 1;
}

.fb-card__body--center {
  align-items: center;
  text-align: center;
}

.fb-card__body--compact {
  padding: 16px;
}

/* ─── Header (inside body) ─── */

.fb-card__header {
  display: flex;
  align-items: center;
  gap: 8px;
}

/* ─── Content ─── */

.fb-card__icon {
  font-size: 24px;
  color: #AAC9BA;
}

.fb-card__title {
  font-family: "Mulish", sans-serif;
  font-size: 20px;
  font-weight: 600;
  color: #2E2E2E;
  line-height: 1.35;
  margin: 0;
}

.fb-card__text {
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #2E2E2E;
  line-height: 1.6;
  margin: 0;
}

.fb-card__metric {
  font-family: "DM Serif Text", serif;
  font-size: 40px;
  font-weight: 400;
  color: #2E2E2E;
  line-height: 1.2;
}

/* ─── Footer ─── */

.fb-card__footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 24px 24px;
  gap: 12px;
}

.fb-card__footer--compact {
  padding: 0 16px 16px;
}
```

---

## Usage Rules

- Use **Elevated** on white page backgrounds, **Outlined** in dense grids, **Surface** when the card background should contribute to section-level colour coding.
- Do not mix card variants within the same grid. A row of cards should all be the same variant.
- Image zoom (`scale(1.03)` on hover) only applies to cards that are clickable. Do not animate images on static informational cards.
- The card title always uses H3 typography (Mulish, 20px, 600). Do not use DM Serif Text for card titles — reserve the serif for Display and H1.
- The metric card is the only context where DM Serif Text appears below H1 size, because the number functions as a display element, not a heading.
- Card footers should contain at most two actions — one primary/ghost and one secondary.
- Do not put padding directly on `.fb-card`. Padding lives on `.fb-card__body` and `.fb-card__footer` so the image can bleed edge-to-edge.
