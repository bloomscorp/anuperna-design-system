# Button

Buttons trigger actions. Anuprerna uses three button variants — Primary, Secondary, and Ghost — each suited to a different level of emphasis. Sage is the default color for primary buttons, but all four brand color families are available as variants.

---

## Variants

### Primary
A filled button for the most important action on a screen. Uses the foreground pastel color as the background with `#2E2E2E` text.

- Background: `#AAC9BA` (Sage foreground, default)
- Text: `#2E2E2E`
- Border: none
- Border radius: `3px`

### Secondary
An outlined button for supporting actions that sit alongside a primary button. Does not compete visually with the primary.

- Background: transparent
- Text: `#2E2E2E`
- Border: `1px solid #2E2E2E`
- Border radius: `3px`
- Hover: fills to `#2E2E2E` background with white text

### Ghost
A minimal text + animated arrow button for soft CTAs — "Discover More", "Read More", navigational prompts. No background or border. Already in use across the site as `.fb_animate_icon_button`.

- Background: none
- Text: `#2E2E2E`, uppercase, 13px
- Arrow: animated on hover (see CSS reference)

---

## Color Families

Primary buttons are available in all four brand color families. Use the variant that matches the surface or section the button sits on.

| Variant | Background | Text |
|---|---|---|
| Sage (default) | `#AAC9BA` | `#2E2E2E` |
| Rose | `#D5B3B9` | `#2E2E2E` |
| Lavender | `#BFB9D6` | `#2E2E2E` |
| Mist | `#BCBFD2` | `#2E2E2E` |

Secondary and Ghost buttons do not have color variants — they always use `#2E2E2E`.

---

## Sizes

All sizes use Mulish at uppercase weight. Height is fixed; width is determined by content and horizontal padding.

| Size | Height | Padding (horizontal) | Font size | Font weight |
|---|---|---|---|---|
| Small | 32px | 12px | 12px | 500 |
| Default | 40px | 20px | 12px | 500 |
| Large | 48px | 24px | 14px | 500 |

Button text is always uppercase with `0.08em` letter spacing.

---

## States

| State | Primary | Secondary | Ghost |
|---|---|---|---|
| Default | Filled pastel | Outlined | Text + arrow |
| Hover | `brightness(0.93)` | Fills `#2E2E2E`, text white | Arrow animates right |
| Active | `brightness(0.87)` | Same as hover | — |
| Disabled | `opacity: 0.4`, `cursor: not-allowed` | `opacity: 0.4`, `cursor: not-allowed` | `opacity: 0.4`, `cursor: not-allowed` |

---

## CSS Reference

### Primary button

```css
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  height: 40px;
  padding: 0 20px;
  border: 1px solid transparent;
  border-radius: 3px;
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

/* Variants */
.btn-primary          { background-color: #AAC9BA; color: #2E2E2E; }
.btn-primary.btn-rose { background-color: #D5B3B9; color: #2E2E2E; }
.btn-primary.btn-lavender { background-color: #BFB9D6; color: #2E2E2E; }
.btn-primary.btn-mist { background-color: #BCBFD2; color: #2E2E2E; }

.btn-primary:hover  { filter: brightness(0.93); }
.btn-primary:active { filter: brightness(0.87); }

/* Sizes */
.btn-sm { height: 32px; padding: 0 12px; font-size: 12px; }
.btn-lg { height: 48px; padding: 0 24px; font-size: 14px; }

/* Disabled */
.btn:disabled,
.btn[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
  pointer-events: none;
}
```

### Secondary button

```css
.btn-secondary {
  background-color: transparent;
  color: #2E2E2E;
  border: 1px solid #2E2E2E;
}

.btn-secondary:hover {
  background-color: #2E2E2E;
  color: #FFFFFF;
}
```

### Ghost button

```css
.btn-ghost {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 5px 24px 5px 0;
  background: none;
  border: none;
  font-family: "Mulish", sans-serif;
  font-size: 13px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #2E2E2E;
  cursor: pointer;
  transition: all 0.5s;
  width: max-content;
}

.btn-ghost:hover {
  padding: 5px 4px 5px 5px;
}

/* Arrow element inside .btn-ghost */
.btn-ghost .btn-ghost-arrow {
  width: 20px;
  height: 0.5px;
  position: relative;
  border-bottom: 0.5px solid #2E2E2E;
  transition: all 0.7s;
}

.btn-ghost .btn-ghost-arrow::before {
  content: '';
  position: absolute;
  left: 0;
  top: -3.5px;
  width: 7px;
  height: 7px;
  transform: rotate(45deg);
  border: 0.5px solid #2E2E2E;
  transition: all 0.5s;
  opacity: 1;
}

.btn-ghost:hover .btn-ghost-arrow {
  border-color: #2E2E2E;
}

.btn-ghost:hover .btn-ghost-arrow::before {
  left: 13px;
  opacity: 0;
  transition: all 0.1s;
}
```

### Ghost button HTML structure

```html
<button class="btn-ghost">
  Discover More
  <span class="btn-ghost-arrow"></span>
</button>
```

---

## Usage Rules

- Use only one Primary button per view. Multiple primary buttons dilute emphasis.
- Primary and Secondary may appear together — Primary on the left, Secondary on the right, or stacked on mobile.
- Ghost buttons are for navigation and soft discovery prompts, not destructive or form-submit actions.
- Do not use Primary buttons on their matching pastel surface (e.g. a Sage primary button on a Sage background). Use a contrasting surface or switch to Secondary.
- Destructive actions (delete, remove, cancel order) use the Secondary button style with Error semantic color: border `#C9A0A0`, text `#C9A0A0`, hover fills `#C9A0A0` with white text.
