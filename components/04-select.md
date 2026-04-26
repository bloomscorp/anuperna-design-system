# Select

The select component is a fully custom dropdown that replaces the native `<select>` element. It shares the same visual language as the input — static label above, full border, `3px` border radius, Mulish throughout. Two variants exist: single-select and multi-select.

---

## Anatomy

```
Label
┌─────────────────────────── ↕ ┐   ← trigger
│ Placeholder or selected value │
└───────────────────────────────┘
┌───────────────────────────────┐
│ Option one                    │   ← dropdown panel (open state)
│ Option two               ✓   │   ← selected option
│ Option three                  │
└───────────────────────────────┘
```

| Part | Spec |
|---|---|
| Label | Mulish, 12px, 500, uppercase, 0.08em letter-spacing, `#2E2E2E` |
| Trigger height | 40px (default), 48px (large) |
| Trigger border | `1px solid #BCBFD2` |
| Trigger border radius | `3px` |
| Trigger background | `#FFFFFF` |
| Placeholder text | Mulish, 16px, 400, `#BCBFD2` |
| Selected value text | Mulish, 16px, 400, `#2E2E2E` |
| Arrow icon | `expand_more` (Material Symbol, 20px, `#BCBFD2`) |
| Option height | 40px |
| Option font | Mulish, 14px, 400, `#2E2E2E` |
| Option padding | `0 16px` |
| Panel border | `1px solid #AAC9BA` |
| Panel border radius | `3px` |
| Panel shadow | `0 4px 12px rgba(0, 0, 0, 0.08)` |
| Panel max height | `240px` (scrollable beyond) |
| Gap between label and trigger | `8px` |

---

## States

### Trigger states

| State | Border | Arrow color | Notes |
|---|---|---|---|
| Default | `1px solid #BCBFD2` | `#BCBFD2` | |
| Hover | `1px solid #AAC9BA` | `#AAC9BA` | |
| Open | `1px solid #AAC9BA` | `#AAC9BA` | Arrow rotates 180° |
| Filled | `1px solid #BCBFD2` | `#BCBFD2` | Shows selected value |
| Disabled | `1px solid #BCBFD2` | `#BCBFD2` | Background `#EAEBF1`, `cursor: not-allowed` |
| Error | `1px solid #C9A0A0` | `#C9A0A0` | Error message shown below |

### Option states

| State | Background | Text |
|---|---|---|
| Default | `#FFFFFF` | `#2E2E2E` |
| Hover | `#E9F1ED` | `#2E2E2E` |
| Selected | `#E9F1ED` | `#2E2E2E` + checkmark icon |
| Disabled | `#FFFFFF` | `#BCBFD2`, `cursor: not-allowed` |

---

## Variants

### Single select

One option can be selected at a time. The trigger shows the selected value. A checkmark appears next to the selected option in the open panel.

```html
<div class="fb-field">
  <label class="fb-label">Fabric Type</label>
  <div class="fb-select" role="combobox" aria-expanded="false" aria-haspopup="listbox">
    <div class="fb-select__trigger">
      <span class="fb-select__value fb-select__placeholder">Select a fabric type</span>
      <span class="fb-select__arrow material-symbols-outlined">expand_more</span>
    </div>
    <div class="fb-select__panel" role="listbox">
      <div class="fb-select__option" role="option" aria-selected="false">Handwoven Cotton</div>
      <div class="fb-select__option fb-select__option--selected" role="option" aria-selected="true">
        Natural Linen
        <span class="fb-select__check material-symbols-outlined">check</span>
      </div>
      <div class="fb-select__option" role="option" aria-selected="false">Raw Silk</div>
      <div class="fb-select__option fb-select__option--disabled" role="option" aria-disabled="true">Polyester</div>
    </div>
  </div>
</div>
```

### Multi-select

Multiple options can be selected. The trigger shows a count of selected items once more than one is chosen. Options use checkboxes inside the panel.

```html
<div class="fb-field">
  <label class="fb-label">Colour Families</label>
  <div class="fb-select fb-select--multi" role="combobox" aria-expanded="false" aria-haspopup="listbox" aria-multiselectable="true">
    <div class="fb-select__trigger">
      <span class="fb-select__value fb-select__placeholder">Select colours</span>
      <span class="fb-select__arrow material-symbols-outlined">expand_more</span>
    </div>
    <div class="fb-select__panel" role="listbox">
      <div class="fb-select__option fb-select__option--checkable" role="option" aria-selected="false">
        <span class="fb-select__checkbox"></span>
        Rose
      </div>
      <div class="fb-select__option fb-select__option--checkable fb-select__option--selected" role="option" aria-selected="true">
        <span class="fb-select__checkbox fb-select__checkbox--checked"></span>
        Sage
      </div>
      <div class="fb-select__option fb-select__option--checkable" role="option" aria-selected="false">
        <span class="fb-select__checkbox"></span>
        Lavender
      </div>
    </div>
  </div>
</div>
```

When items are selected, the trigger updates:
- **1 item**: show the item name — `"Sage"`
- **2+ items**: show a count — `"3 selected"`

### With error

```html
<div class="fb-field fb-field--error">
  <label class="fb-label">Delivery Country</label>
  <div class="fb-select"> ... </div>
  <span class="fb-error-text">Please select a delivery country.</span>
</div>
```

---

## Sizes

| Size | Trigger height | Font size | Padding |
|---|---|---|---|
| Default | 40px | 16px | `0 16px` |
| Large | 48px | 16px | `0 20px` |

---

## CSS Reference

```css
/* ─── Field wrapper (shared with input) ─── */
/* Uses .fb-field, .fb-label, .fb-error-text from 02-input */

/* ─── Select trigger ─── */

.fb-select {
  position: relative;
  width: 100%;
}

.fb-select__trigger {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 40px;
  padding: 0 16px;
  background-color: #FFFFFF;
  border: 1px solid #BCBFD2;
  border-radius: 3px;
  cursor: pointer;
  transition: border-color 0.2s ease-in-out;
  user-select: none;
}

.fb-select:hover .fb-select__trigger,
.fb-select.fb-select--open .fb-select__trigger {
  border-color: #AAC9BA;
}

.fb-select--open .fb-select__trigger {
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}

.fb-select__value {
  font-family: "Mulish", sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #2E2E2E;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.fb-select__placeholder {
  color: #BCBFD2;
}

.fb-select__arrow {
  font-size: 20px;
  color: #BCBFD2;
  transition: transform 0.2s ease-in-out, color 0.2s ease-in-out;
  flex-shrink: 0;
}

.fb-select--open .fb-select__arrow,
.fb-select:hover .fb-select__arrow {
  color: #AAC9BA;
}

.fb-select--open .fb-select__arrow {
  transform: rotate(180deg);
}

/* Large size */
.fb-select--lg .fb-select__trigger {
  height: 48px;
  padding: 0 20px;
}

/* Disabled */
.fb-select--disabled .fb-select__trigger {
  background-color: #EAEBF1;
  cursor: not-allowed;
}

/* Error */
.fb-field--error .fb-select__trigger {
  border-color: #C9A0A0;
}

/* ─── Dropdown panel ─── */

.fb-select__panel {
  display: none;
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background-color: #FFFFFF;
  border: 1px solid #AAC9BA;
  border-top: none;
  border-bottom-left-radius: 3px;
  border-bottom-right-radius: 3px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  max-height: 240px;
  overflow-y: auto;
  z-index: 100;
}

.fb-select--open .fb-select__panel {
  display: block;
}

/* ─── Options ─── */

.fb-select__option {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 40px;
  padding: 0 16px;
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #2E2E2E;
  cursor: pointer;
  transition: background-color 0.15s ease-in-out;
}

.fb-select__option:hover {
  background-color: #E9F1ED;
}

.fb-select__option--selected {
  background-color: #E9F1ED;
}

.fb-select__option--disabled {
  color: #BCBFD2;
  cursor: not-allowed;
}

.fb-select__option--disabled:hover {
  background-color: transparent;
}

.fb-select__check {
  font-size: 16px;
  color: #AAC9BA;
}

/* ─── Multi-select checkboxes inside options ─── */

.fb-select__option--checkable {
  gap: 10px;
  justify-content: flex-start;
}

.fb-select__checkbox {
  width: 16px;
  height: 16px;
  min-width: 16px;
  border: 1px solid #BCBFD2;
  border-radius: 3px;
  background: #FFFFFF;
  position: relative;
  transition: all 0.2s ease-in-out;
}

.fb-select__checkbox--checked {
  background-color: #AAC9BA;
  border-color: #AAC9BA;
}

.fb-select__checkbox--checked::after {
  content: '';
  position: absolute;
  left: 4px;
  top: 1px;
  width: 5px;
  height: 9px;
  border: 2px solid #FFFFFF;
  border-top: none;
  border-left: none;
  transform: rotate(45deg);
}

/* ─── Panel scrollbar ─── */

.fb-select__panel::-webkit-scrollbar {
  width: 4px;
}

.fb-select__panel::-webkit-scrollbar-track {
  background: #F9F4F5;
  border-radius: 4px;
}

.fb-select__panel::-webkit-scrollbar-thumb {
  background: #AAC9BA;
  border-radius: 4px;
}
```

---

## Keyboard Behaviour

| Key | Action |
|---|---|
| `Enter` / `Space` | Open or close the panel; select focused option |
| `ArrowDown` | Move focus to next option |
| `ArrowUp` | Move focus to previous option |
| `Escape` | Close the panel without changing selection |
| `Tab` | Close the panel and move focus to next field |

Implement this behaviour in the component's JavaScript. The `aria-expanded`, `aria-selected`, and `role` attributes in the HTML structure must be kept in sync with the open/selected state.

---

## Usage Rules

- Always include a label. Do not use the placeholder as the only identifier of what the field is for.
- Use single-select for exclusive choices (one category, one country, one size).
- Use multi-select for additive filters (colour families, fabric types, certifications).
- For lists longer than 10 options, consider adding a search input inside the panel.
- Do not use native `<select>` elements in new UI. Use this component for visual and behavioural consistency.
- Keep option labels short. If a label exceeds the panel width, it will truncate — write labels that work within ~250px.
