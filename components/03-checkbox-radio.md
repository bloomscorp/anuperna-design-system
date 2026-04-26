# Checkbox & Radio

Checkboxes and radio buttons are custom-designed components that replace Angular Material's `mat-checkbox` and `mat-radio`. Both use native HTML inputs hidden visually, with a custom control element styled via CSS. Sage is the active/selected color, consistent with the primary button.

---

## Checkbox

### Anatomy

```
☑  Label text
↑
Control (16×16px)
```

| Part | Spec |
|---|---|
| Control size | 16×16px |
| Border (default) | `1px solid #BCBFD2` |
| Border radius | `3px` |
| Background (default) | `#FFFFFF` |
| Background (checked) | `#AAC9BA` |
| Border (checked) | `1px solid #AAC9BA` |
| Checkmark | White, CSS-drawn |
| Label font | Mulish, 14px, 400, `#2E2E2E` |
| Gap between control and label | `8px` |

### States

| State | Border | Background | Notes |
|---|---|---|---|
| Default | `1px solid #BCBFD2` | `#FFFFFF` | Unchecked resting state |
| Hover | `1px solid #AAC9BA` | `#FFFFFF` | Signals interactivity |
| Focus | `1px solid #AAC9BA` + `outline: 2px solid #E9F1ED` | `#FFFFFF` | Keyboard focus ring using Sage background |
| Checked | `1px solid #AAC9BA` | `#AAC9BA` | White checkmark inside |
| Indeterminate | `1px solid #AAC9BA` | `#AAC9BA` | Horizontal white line inside |
| Disabled unchecked | `1px solid #BCBFD2` | `#EAEBF1` | `cursor: not-allowed`, label opacity 0.4 |
| Disabled checked | `1px solid #AAC9BA` | `#AAC9BA` opacity 0.4 | `cursor: not-allowed` |
| Error | `1px solid #C9A0A0` | `#FFFFFF` | When required and unselected on submit |

### HTML Structure

```html
<label class="fb-checkbox">
  <input type="checkbox" class="fb-checkbox__input" />
  <span class="fb-checkbox__control"></span>
  <span class="fb-checkbox__label">Label text</span>
</label>
```

### With error

```html
<div class="fb-checkbox-group fb-checkbox-group--error">
  <label class="fb-checkbox">
    <input type="checkbox" class="fb-checkbox__input" />
    <span class="fb-checkbox__control"></span>
    <span class="fb-checkbox__label">I agree to the terms</span>
  </label>
  <span class="fb-error-text">You must accept the terms to continue.</span>
</div>
```

---

## Radio

### Anatomy

```
◉  Option one
○  Option two
○  Option three
```

| Part | Spec |
|---|---|
| Control size | 16×16px |
| Border radius | `50%` |
| Border (default) | `1px solid #BCBFD2` |
| Background (default) | `#FFFFFF` |
| Border (selected) | `1px solid #AAC9BA` |
| Inner dot (selected) | `8×8px`, `#AAC9BA` |
| Label font | Mulish, 14px, 400, `#2E2E2E` |
| Gap between control and label | `8px` |

### States

| State | Border | Inner dot | Notes |
|---|---|---|---|
| Default | `1px solid #BCBFD2` | None | |
| Hover | `1px solid #AAC9BA` | None | |
| Focus | `1px solid #AAC9BA` + `outline: 2px solid #E9F1ED` | None | |
| Selected | `1px solid #AAC9BA` | `#AAC9BA`, 8×8px | |
| Disabled unselected | `1px solid #BCBFD2` | None | `cursor: not-allowed`, label opacity 0.4 |
| Disabled selected | `1px solid #AAC9BA` opacity 0.4 | `#AAC9BA` opacity 0.4 | |
| Error | `1px solid #C9A0A0` | None | When required group has no selection |

### HTML Structure

```html
<label class="fb-radio">
  <input type="radio" name="group-name" class="fb-radio__input" />
  <span class="fb-radio__control"></span>
  <span class="fb-radio__label">Option one</span>
</label>
```

---

## Group Layout

### Vertical (default)

Use for most forms — easier to scan, especially with longer labels.

```html
<div class="fb-control-group">
  <span class="fb-label">Preferred contact method</span>
  <label class="fb-radio"> ... </label>
  <label class="fb-radio"> ... </label>
  <label class="fb-radio"> ... </label>
</div>
```

### Horizontal

Use only when there are 2–3 short options and space permits.

```html
<div class="fb-control-group fb-control-group--inline">
  <label class="fb-checkbox"> ... </label>
  <label class="fb-checkbox"> ... </label>
</div>
```

---

## CSS Reference

```css
/* ─── Shared ─── */

.fb-checkbox,
.fb-radio {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  user-select: none;
}

/* Hide native input, keep it accessible */
.fb-checkbox__input,
.fb-radio__input {
  position: absolute;
  opacity: 0;
  width: 0;
  height: 0;
  pointer-events: none;
}

.fb-checkbox__label,
.fb-radio__label {
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #2E2E2E;
}

/* ─── Checkbox ─── */

.fb-checkbox__control {
  position: relative;
  width: 16px;
  height: 16px;
  min-width: 16px;
  background-color: #FFFFFF;
  border: 1px solid #BCBFD2;
  border-radius: 3px;
  transition: all 0.2s ease-in-out;
}

.fb-checkbox:hover .fb-checkbox__control {
  border-color: #AAC9BA;
}

.fb-checkbox__input:focus-visible + .fb-checkbox__control {
  border-color: #AAC9BA;
  outline: 2px solid #E9F1ED;
  outline-offset: 2px;
}

.fb-checkbox__input:checked + .fb-checkbox__control {
  background-color: #AAC9BA;
  border-color: #AAC9BA;
}

/* Checkmark */
.fb-checkbox__input:checked + .fb-checkbox__control::after {
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

/* Indeterminate */
.fb-checkbox__input:indeterminate + .fb-checkbox__control {
  background-color: #AAC9BA;
  border-color: #AAC9BA;
}

.fb-checkbox__input:indeterminate + .fb-checkbox__control::after {
  content: '';
  position: absolute;
  left: 3px;
  top: 6px;
  width: 8px;
  height: 2px;
  background: #FFFFFF;
}

/* Disabled */
.fb-checkbox__input:disabled ~ .fb-checkbox__control {
  background-color: #EAEBF1;
  cursor: not-allowed;
}

.fb-checkbox__input:disabled ~ .fb-checkbox__label {
  opacity: 0.4;
}

.fb-checkbox:has(.fb-checkbox__input:disabled) {
  cursor: not-allowed;
}

/* ─── Radio ─── */

.fb-radio__control {
  position: relative;
  width: 16px;
  height: 16px;
  min-width: 16px;
  background-color: #FFFFFF;
  border: 1px solid #BCBFD2;
  border-radius: 50%;
  transition: all 0.2s ease-in-out;
}

.fb-radio:hover .fb-radio__control {
  border-color: #AAC9BA;
}

.fb-radio__input:focus-visible + .fb-radio__control {
  border-color: #AAC9BA;
  outline: 2px solid #E9F1ED;
  outline-offset: 2px;
}

.fb-radio__input:checked + .fb-radio__control {
  border-color: #AAC9BA;
}

/* Inner dot */
.fb-radio__input:checked + .fb-radio__control::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background-color: #AAC9BA;
}

/* Disabled */
.fb-radio__input:disabled ~ .fb-radio__control {
  background-color: #EAEBF1;
  cursor: not-allowed;
}

.fb-radio__input:disabled ~ .fb-radio__label {
  opacity: 0.4;
}

.fb-radio:has(.fb-radio__input:disabled) {
  cursor: not-allowed;
}

/* ─── Error state ─── */

.fb-checkbox-group--error .fb-checkbox__control,
.fb-control-group--error .fb-radio__control {
  border-color: #C9A0A0;
}

/* ─── Group layout ─── */

.fb-control-group {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.fb-control-group .fb-label {
  margin-bottom: 4px;
}

.fb-control-group--inline {
  flex-direction: row;
  flex-wrap: wrap;
  gap: 20px;
}
```

---

## Usage Rules

- Radio buttons must always be grouped under a shared `name` attribute so only one can be selected at a time.
- Checkboxes are independent — each has its own value and can be checked without affecting others.
- Always place a group label (`fb-label`) above a set of radios or checkboxes so the question is clear.
- Horizontal layout is limited to 2–3 short options. Beyond that, use vertical.
- Show error text at the group level (below all options), not on each individual control.
- Do not use Angular Material `mat-checkbox` or `mat-radio` for new components. Use these custom classes instead.
