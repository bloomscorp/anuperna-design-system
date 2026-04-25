# Spacing

Anuprerna's spacing system is built on a **4px base unit**. All spacing values are multiples of 4, which aligns with Tailwind's default scale and keeps layouts consistent across components and pages.

---

## Spacing Scale

| Token | Value | Tailwind equivalent | Common usage |
|---|---|---|---|
| `space-1` | 4px | `p-1` / `m-1` | Micro gaps, icon-to-label spacing |
| `space-2` | 8px | `p-2` / `m-2` | Badge padding, tight element gaps |
| `space-3` | 12px | `p-3` / `m-3` | Compact element spacing, tag padding |
| `space-4` | 16px | `p-4` / `m-4` | Base unit, input padding, small card padding |
| `space-5` | 20px | `p-5` / `m-5` | Component gaps, grid column gaps |
| `space-6` | 24px | `p-6` / `m-6` | Card padding, form group spacing |
| `space-8` | 32px | `p-8` / `m-8` | Section sub-spacing, large card padding |
| `space-10` | 40px | `p-10` / `m-10` | Section vertical padding |
| `space-12` | 48px | `p-12` / `m-12` | Large section spacing |
| `space-16` | 64px | `p-16` / `m-16` | Major vertical rhythm between page sections |

Values outside this scale (e.g. 5px, 7px, 29px) should not be used in new work. If an existing component uses an off-scale value, migrate it to the nearest token when refactoring.

---

## Page Layout

### Container

All page content sits inside a centered container with a maximum width and horizontal padding.

| Property | Desktop | Mobile |
|---|---|---|
| Max width | `1400px` | — |
| Horizontal padding | `50px` (`space-12` approx.) | `16px` (`space-4`) |
| Alignment | `margin: 0 auto` | — |

```css
.page-container {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 50px;
}

@media (max-width: 768px) {
  .page-container {
    padding: 0 16px;
  }
}
```

---

## Breakpoints

| Name | Range | Typical use |
|---|---|---|
| Mobile | `< 768px` | Single-column layouts, stacked navigation |
| Tablet | `768px – 999px` | Transitional layouts, 2-column grids |
| Desktop | `≥ 1000px` | Full multi-column layouts, expanded navigation |

---

## Grid System

The grid uses a **20px gap** (`space-5`) as the standard column and row gap. Column counts vary by breakpoint and context.

| Breakpoint | Default columns | Notes |
|---|---|---|
| Mobile | 1 | Full-width stacked |
| Tablet | 2 | Side-by-side pairs |
| Desktop | 4 | Standard product/card grid |

These are defaults. Specific components (e.g. a featured section or a blog listing) may use a 2 or 3-column desktop layout — define the exception in the component's own documentation.

### Standard card grid example

```css
.card-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card-item {
  width: calc(25% - 20px); /* 4 columns on desktop */
}

@media (max-width: 999px) {
  .card-item {
    width: calc(50% - 20px); /* 2 columns on tablet */
  }
}

@media (max-width: 768px) {
  .card-item {
    width: 100%; /* 1 column on mobile */
  }
}
```

---

## Vertical Rhythm

Page sections should breathe. Use these values for top/bottom padding on full-width sections:

| Context | Value | Token |
|---|---|---|
| Tight section (e.g. a thin banner) | 24px | `space-6` |
| Standard section | 40px | `space-10` |
| Hero or feature section | 64px | `space-16` |

---

## Navigation

The top navigation occupies a fixed height that page content must account for.

| State | Height |
|---|---|
| Expanded (homepage) | `300px` |
| Collapsed / scrolled | `70px` |

Page content on non-homepage routes should have a `margin-top` of `70px` to clear the fixed navigation bar.
