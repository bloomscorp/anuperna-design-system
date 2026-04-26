# Product Card

The product card is Anuprerna's primary commerce organism. It displays enough information for a buyer to evaluate a product without visiting the detail page, while directing them toward customisation rather than a direct purchase. It is built on the base Card molecule (`06-card.md`).

Products at Anuprerna cannot be added to a cart directly — every order requires customisation. The card's CTAs reflect this.

---

## Anatomy

```
┌─────────────────────────────────────┐
│                                     │
│          Hero / Hover image         │  ← image zone
│                                     │
├─────────────────────────────────────┤
│ [Stock badge]          [♡ Wishlist] │  ← status row
│ Category label                      │
│ Product name                        │
│                                     │
│ ₹ 420 / meter                       │  ← pricing block
│ bulk order @ ₹ 380 / meter          │  ← logged in only
│ 🔒 Log in for bulk pricing           │  ← logged out only
│                                     │
│ [Customise & Order →] [Sample]      │  ← CTA row
├─────────────────────────────────────┤
│ ○ ○ ○  +5          (related zone)  │  ← related products or swatch CTA
└─────────────────────────────────────┘
```

---

## Zones

### Image zone

| Property | Value |
|---|---|
| Aspect ratio | `3:4` (portrait) |
| Default image | Hero product shot |
| Hover image | Secondary / texture shot, crossfade `0.4s ease-in-out` |
| Object fit | `cover` |
| Border radius | `6px 6px 0 0` |

### Status row

Left: stock status badge. Right: wishlist icon button.

**Stock badge variants:**

| Status | Badge variant | Label |
|---|---|---|
| In Stock | Sage | In Stock |
| Out of Stock | Error | Out of Stock |
| Made to Order | Warning | Made to Order |

**Wishlist button:**
- Icon: `favorite_border` (default) → `favorite` (wishlisted)
- Size: 20px, color `#BCBFD2` default, `#D5B3B9` (Rose foreground) when active
- No background, no border — icon button only
- Accessible label: `aria-label="Add to wishlist"` / `"Remove from wishlist"`

### Category label

- Component: Tag, Neutral variant, non-dismissible
- Positioned directly below the status row

### Product name

- Typography: Mulish, 17px, 600 (H4 token)
- Color: `#2E2E2E`
- Max 2 lines, truncate with ellipsis beyond that

### Pricing block

**Price per meter:**
- Typography: Mulish, 16px, 400 (Body)
- Format: `{currency symbol} {amount} / meter`
- Currency is derived from the user's selected currency (site-wide)

**Bulk pricing row (logged in):**
- Typography: Mulish, 12px, 500 (Label)
- Color: `#AAC9BA` (Sage foreground) — visually distinct from retail price
- Format: `bulk order @ {currency symbol} {amount} / meter`

**Bulk pricing prompt (logged out):**
- Icon: `lock` Material Symbol, 14px, `#BCBFD2`
- Typography: Mulish, 12px, 400, `#BCBFD2`
- Text: `Log in for bulk pricing`
- Displayed as an inline text link — not a button, so it does not compete with the CTAs
- On click: redirects to login

### CTA row

Two CTAs sit side by side. On narrow cards (mobile single-column), they stack.

| CTA | Component | Action |
|---|---|---|
| Customise & Order | Ghost button (primary) | Opens product detail page / configurator |
| Request Sample | Outlined button, small | Opens sample request flow |

### Related products zone

Fixed height zone (`52px`) at the bottom of the card. Always occupied — either by related product circles or by a swatch CTA.

**With related products:**

- Up to 3 circular thumbnails, `36px` diameter
- `object-fit: cover`, `border-radius: 50%`
- Border: `1.5px solid #EAEBF1` default, `1.5px solid #AAC9BA` on hover
- Overlap: `-8px` left margin on each subsequent circle (stacked effect)
- On hover: shows product name as a tooltip
- On click: navigates to that related product

**Overflow counter:**
- Same `36px` circle, background `#EAEBF1`, text `#2E2E2E`
- Typography: Mulish, 11px, 500
- Format: `+{n}` (e.g. `+5`)
- On click: expands a small dropdown panel listing all related products

**Without related products:**
- Shows a `Request a Swatch` ghost button in place of the circles
- This ensures card height is consistent across the grid

---

## States

### Default card
All elements visible as described above.

### Logged-in card
Bulk pricing value shown instead of the login prompt.

### Out of Stock card
- Stock badge: Error (`Out of Stock`)
- `Customise & Order` CTA is replaced with `Notify Me` (outlined button)
- `Request Sample` CTA remains visible

### Made to Order card
- Stock badge: Warning (`Made to Order`)
- CTA remains `Customise & Order` — made-to-order products can still be configured
- Optionally show a lead time note in Body Small beneath the price: e.g. `Ships in 4–6 weeks`

---

## HTML Structure

```html
<div class="fb-card fb-card--elevated fb-product-card">

  <!-- Image zone -->
  <div class="fb-card__image fb-card__image--portrait fb-product-card__image">
    <img class="fb-product-card__img-default" src="product-hero.jpg" alt="Natural Linen, Sage" />
    <img class="fb-product-card__img-hover" src="product-texture.jpg" alt="" aria-hidden="true" />
  </div>

  <div class="fb-card__body">

    <!-- Status row -->
    <div class="fb-product-card__status-row">
      <span class="fb-badge fb-badge--sage">In Stock</span>
      <button class="fb-product-card__wishlist" aria-label="Add to wishlist">
        <span class="material-symbols-outlined">favorite_border</span>
      </button>
    </div>

    <!-- Category -->
    <span class="fb-tag fb-tag--neutral">Fabric</span>

    <!-- Product name -->
    <h3 class="fb-product-card__name">Natural Linen — Sage Handwoven</h3>

    <!-- Pricing block -->
    <div class="fb-product-card__pricing">
      <span class="fb-product-card__price">₹ 420 / meter</span>

      <!-- Logged in: bulk price -->
      <span class="fb-product-card__bulk-price">
        bulk order @ ₹ 380 / meter
      </span>

      <!-- Logged out: bulk price prompt -->
      <a href="/login" class="fb-product-card__bulk-prompt">
        <span class="material-symbols-outlined">lock</span>
        Log in for bulk pricing
      </a>
    </div>

    <!-- CTAs -->
    <div class="fb-product-card__ctas">
      <button class="btn-ghost">
        Customise & Order
        <span class="btn-ghost-arrow"></span>
      </button>
      <button class="btn btn-secondary btn-sm">Request Sample</button>
    </div>

  </div>

  <!-- Related products zone -->
  <div class="fb-product-card__related">

    <!-- With related products -->
    <div class="fb-product-card__related-circles">
      <a href="/product/1" class="fb-product-card__circle" title="Block Print Cotton">
        <img src="related-1.jpg" alt="Block Print Cotton" />
      </a>
      <a href="/product/2" class="fb-product-card__circle" title="Raw Silk Ivory">
        <img src="related-2.jpg" alt="Raw Silk Ivory" />
      </a>
      <a href="/product/3" class="fb-product-card__circle" title="Hemp Natural">
        <img src="related-3.jpg" alt="Hemp Natural" />
      </a>
      <button class="fb-product-card__circle fb-product-card__overflow" aria-label="Show 5 more related products">
        +5
      </button>
    </div>

    <!-- Without related products (use one or the other) -->
    <button class="btn-ghost fb-product-card__swatch-cta">
      Request a Swatch
      <span class="btn-ghost-arrow"></span>
    </button>

  </div>

</div>
```

---

## CSS Reference

```css
/* ─── Product card ─── */

.fb-product-card {
  position: relative;
}

/* ─── Image zone ─── */

.fb-product-card__image {
  position: relative;
}

.fb-product-card__img-default,
.fb-product-card__img-hover {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: opacity 0.4s ease-in-out;
}

.fb-product-card__img-hover {
  opacity: 0;
}

.fb-product-card:hover .fb-product-card__img-default {
  opacity: 0;
}

.fb-product-card:hover .fb-product-card__img-hover {
  opacity: 1;
}

/* ─── Status row ─── */

.fb-product-card__status-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.fb-product-card__wishlist {
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
  color: #BCBFD2;
  display: flex;
  align-items: center;
  transition: color 0.2s ease-in-out;
}

.fb-product-card__wishlist:hover,
.fb-product-card__wishlist--active {
  color: #D5B3B9;
}

.fb-product-card__wishlist .material-symbols-outlined {
  font-size: 20px;
}

/* ─── Product name ─── */

.fb-product-card__name {
  font-family: "Mulish", sans-serif;
  font-size: 17px;
  font-weight: 600;
  color: #2E2E2E;
  line-height: 1.4;
  margin: 0;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* ─── Pricing block ─── */

.fb-product-card__pricing {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.fb-product-card__price {
  font-family: "Mulish", sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #2E2E2E;
}

.fb-product-card__bulk-price {
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 500;
  color: #AAC9BA;
  text-transform: uppercase;
  letter-spacing: 0.04em;
}

.fb-product-card__bulk-prompt {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: #BCBFD2;
  text-decoration: none;
  transition: color 0.2s ease-in-out;
}

.fb-product-card__bulk-prompt:hover {
  color: #2E2E2E;
}

.fb-product-card__bulk-prompt .material-symbols-outlined {
  font-size: 14px;
}

/* ─── CTAs ─── */

.fb-product-card__ctas {
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
}

/* ─── Related products zone ─── */

.fb-product-card__related {
  min-height: 52px;
  display: flex;
  align-items: center;
  padding: 0 24px 20px;
}

.fb-product-card__related-circles {
  display: flex;
  align-items: center;
}

.fb-product-card__circle {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  overflow: hidden;
  border: 1.5px solid #EAEBF1;
  margin-left: -8px;
  transition: border-color 0.2s ease-in-out;
  cursor: pointer;
  display: block;
  flex-shrink: 0;
}

.fb-product-card__related-circles .fb-product-card__circle:first-child {
  margin-left: 0;
}

.fb-product-card__circle img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.fb-product-card__circle:hover {
  border-color: #AAC9BA;
  z-index: 1;
  position: relative;
}

.fb-product-card__overflow {
  background-color: #EAEBF1;
  border: 1.5px solid #EAEBF1;
  font-family: "Mulish", sans-serif;
  font-size: 11px;
  font-weight: 500;
  color: #2E2E2E;
  display: flex;
  align-items: center;
  justify-content: center;
}

.fb-product-card__overflow:hover {
  background-color: #E9F1ED;
  border-color: #AAC9BA;
}

.fb-product-card__swatch-cta {
  font-size: 12px;
}
```

---

## Usage Rules

- Never use "Add to Cart" or "Buy Now" on a product card. Every product requires customisation before ordering.
- The `Customise & Order` CTA is always present unless the product is Out of Stock, in which case it is replaced by `Notify Me`.
- `Request Sample` is always available regardless of stock status.
- Bulk pricing is conditionally rendered server-side — do not show a skeleton or empty space where it would appear. Logged-out users always see the login prompt; logged-in users always see the value.
- Product name truncates at 2 lines. Do not let long names break the card height — use `-webkit-line-clamp`.
- The related products zone always has a minimum height of `52px`. Cards without related products show `Request a Swatch` in this zone to maintain consistent card heights across the grid.
- Do not show more than 3 related product circles. Overflow beyond 3 is always shown as a `+{n}` counter.
- Wishlist state (filled vs. outline heart) must be persisted and synced with the user's account. Do not use local-only state for wishlist.
