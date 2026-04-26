# Badge & Tag

Badges and tags are both small labelling elements but serve different purposes. **Badges** are compact status or count indicators — non-interactive, always short. **Tags** are category or attribute labels — slightly larger, and may be dismissible. Both draw from the brand's pastel color families.

---

## Badge

### When to use

- Product status: "New", "Sale", "Sold Out", "Featured"
- Order status: "Processing", "Shipped", "Delivered"
- Count indicators: number of items in a cart, unread notifications
- Certification or attribute markers on product listings

### Anatomy

| Part | Spec |
|---|---|
| Height | 20px |
| Horizontal padding | `8px` |
| Font | Mulish, 11px, 500, uppercase, 0.06em letter-spacing |
| Border radius | `3px` |
| Min width (count badge) | `20px` |

### Color variants

| Variant | Background | Text | Use |
|---|---|---|---|
| Neutral | `#EAEBF1` | `#2E2E2E` | Default, general labels |
| Rose | `#F9F4F5` | `#D5B3B9` | Decorative, warm labels |
| Sage | `#E9F1ED` | `#AAC9BA` | Positive, natural labels |
| Lavender | `#EBE9F2` | `#BFB9D6` | Soft, considered labels |
| Mist | `#EAEBF1` | `#BCBFD2` | Neutral, minimal labels |
| Success | `#E9F5EA` | `#9FC6A6` | Confirmed, completed, active |
| Warning | `#F5F0E0` | `#C9B080` | Pending, requires attention |
| Error | `#F5EAEA` | `#C9A0A0` | Rejected, failed, out of stock |
| Dark | `#2E2E2E` | `#FFFFFF` | High emphasis, featured |

### HTML Structure

```html
<!-- Standard badge -->
<span class="fb-badge fb-badge--sage">New Arrival</span>

<!-- Status badges -->
<span class="fb-badge fb-badge--success">Shipped</span>
<span class="fb-badge fb-badge--error">Sold Out</span>
<span class="fb-badge fb-badge--warning">Processing</span>

<!-- Count badge -->
<span class="fb-badge fb-badge--dark fb-badge--count">4</span>
```

---

## Tag

### When to use

- Product category labels: "Fabric", "Homeware", "Apparel"
- Selected filter indicators (dismissible)
- Craft technique markers: "Handwoven", "Block Print", "Natural Dye"
- Attribute chips on product detail pages

### Anatomy

| Part | Spec |
|---|---|
| Height | 28px |
| Horizontal padding | `12px` |
| Font | Mulish, 12px, 500, uppercase, 0.06em letter-spacing |
| Border radius | `100px` (pill) |
| Icon size (optional) | 14px, Material Symbol, left of label |
| Dismiss icon | `close` Material Symbol, 14px, right of label |
| Gap between icon and label | `4px` |

### Color variants

Tags use the same color set as badges but appear on a pill-shaped element. In most product contexts, Sage and Neutral are the primary choices.

| Variant | Background | Text | Border |
|---|---|---|---|
| Neutral | `#EAEBF1` | `#2E2E2E` | none |
| Rose | `#F9F4F5` | `#D5B3B9` | none |
| Sage | `#E9F1ED` | `#AAC9BA` | none |
| Lavender | `#EBE9F2` | `#BFB9D6` | none |
| Mist | `#EAEBF1` | `#BCBFD2` | none |
| Outlined | `transparent` | `#2E2E2E` | `1px solid #BCBFD2` |

### HTML Structure

```html
<!-- Standard tag -->
<span class="fb-tag fb-tag--sage">Handwoven</span>

<!-- Tag with leading icon -->
<span class="fb-tag fb-tag--neutral">
  <span class="material-symbols-outlined">eco</span>
  Natural Dye
</span>

<!-- Dismissible tag (selected filter) -->
<span class="fb-tag fb-tag--sage fb-tag--dismissible">
  Sage
  <button class="fb-tag__dismiss" aria-label="Remove Sage filter">
    <span class="material-symbols-outlined">close</span>
  </button>
</span>

<!-- Outlined tag -->
<span class="fb-tag fb-tag--outlined">Block Print</span>
```

---

## CSS Reference

```css
/* ─── Badge ─── */

.fb-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  height: 20px;
  padding: 0 8px;
  border-radius: 3px;
  font-family: "Mulish", sans-serif;
  font-size: 11px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  white-space: nowrap;
  line-height: 1;
}

/* Count badge — square when single digit, pill when multi-digit */
.fb-badge--count {
  min-width: 20px;
  padding: 0 6px;
  border-radius: 100px;
}

/* Badge color variants */
.fb-badge--neutral   { background-color: #EAEBF1; color: #2E2E2E; }
.fb-badge--rose      { background-color: #F9F4F5; color: #D5B3B9; }
.fb-badge--sage      { background-color: #E9F1ED; color: #AAC9BA; }
.fb-badge--lavender  { background-color: #EBE9F2; color: #BFB9D6; }
.fb-badge--mist      { background-color: #EAEBF1; color: #BCBFD2; }
.fb-badge--success   { background-color: #E9F5EA; color: #9FC6A6; }
.fb-badge--warning   { background-color: #F5F0E0; color: #C9B080; }
.fb-badge--error     { background-color: #F5EAEA; color: #C9A0A0; }
.fb-badge--dark      { background-color: #2E2E2E; color: #FFFFFF; }

/* ─── Tag ─── */

.fb-tag {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  height: 28px;
  padding: 0 12px;
  border-radius: 100px;
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  white-space: nowrap;
  line-height: 1;
}

.fb-tag .material-symbols-outlined {
  font-size: 14px;
}

/* Tag color variants */
.fb-tag--neutral   { background-color: #EAEBF1; color: #2E2E2E; }
.fb-tag--rose      { background-color: #F9F4F5; color: #D5B3B9; }
.fb-tag--sage      { background-color: #E9F1ED; color: #AAC9BA; }
.fb-tag--lavender  { background-color: #EBE9F2; color: #BFB9D6; }
.fb-tag--mist      { background-color: #EAEBF1; color: #BCBFD2; }
.fb-tag--outlined  {
  background-color: transparent;
  color: #2E2E2E;
  border: 1px solid #BCBFD2;
  padding: 0 11px;
}

/* Dismissible tag */
.fb-tag--dismissible {
  padding-right: 6px;
}

.fb-tag__dismiss {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
  color: inherit;
  opacity: 0.6;
  margin-left: 2px;
  transition: opacity 0.2s ease-in-out;
}

.fb-tag__dismiss:hover {
  opacity: 1;
}

.fb-tag__dismiss .material-symbols-outlined {
  font-size: 14px;
}

/* ─── Tag group (wrapping row of tags) ─── */

.fb-tag-group {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
```

---

## Usage Rules

- Badges are always non-interactive. Do not add click handlers to a badge — use a tag or button instead.
- Tags may be interactive (dismissible) but only in filter or selection contexts.
- Keep badge text to 1–2 words maximum. If the label is longer, use a tag.
- Do not use more than two different badge color variants in the same visual cluster — it creates noise.
- Semantic colors (success, warning, error) are reserved for actual status communication. Do not use them decoratively.
- Use the Dark badge sparingly — only for the single most important status on a product (e.g. "Featured" or "New").
- Tag groups should use a single color family within one context (e.g. all category tags in Neutral, all selected filters in Sage).
