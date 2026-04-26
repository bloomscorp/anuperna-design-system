# Input

Input fields are custom-designed components, independent of Angular Material. They follow the brand's visual language — clean full borders, static labels above, and Mulish throughout.

---

## Anatomy

Every input is composed of four parts:

```
Label              ← always visible above the field
┌─────────────────────────────┐
│ Placeholder / Value         │  ← the input field itself
└─────────────────────────────┘
Helper text or error message  ← below the field, optional
```

| Part | Typography | Color |
|---|---|---|
| Label | Mulish, 12px, 500, uppercase, 0.08em letter-spacing | `#2E2E2E` |
| Input value | Mulish, 16px, 400 | `#2E2E2E` |
| Placeholder | Mulish, 16px, 400 | `#BCBFD2` |
| Helper text | Mulish, 12px, 400 | `#BCBFD2` |
| Error message | Mulish, 12px, 400 | `#C9A0A0` |

Spacing:
- Label to input field: `8px`
- Input field to helper/error text: `4px`
- Between form groups: `20px`

---

## States

| State | Border | Background | Notes |
|---|---|---|---|
| Default | `1px solid #BCBFD2` | `#FFFFFF` | Resting state |
| Focus | `1px solid #AAC9BA` | `#FFFFFF` | Sage foreground signals active |
| Filled | `1px solid #BCBFD2` | `#FFFFFF` | Same as default |
| Error | `1px solid #C9A0A0` | `#FFFFFF` | Error message shown below |
| Disabled | `1px solid #BCBFD2` | `#EAEBF1` | Mist background, `cursor: not-allowed` |
| Success | `1px solid #9FC6A6` | `#FFFFFF` | Optional, for validated fields |

All border transitions use `0.2s ease-in-out`.

---

## Sizes

| Size | Height | Horizontal padding | Use |
|---|---|---|---|
| Default | 40px | 16px | All standard form fields |
| Large | 48px | 20px | Prominent forms — login, checkout, hero search |

Textarea height is not fixed — it starts at a minimum of `96px` (approximately 3 lines) and grows with content.

---

## Variants

### Text input

The standard single-line input.

```html
<div class="fb-field">
  <label class="fb-label">Full Name</label>
  <input type="text" class="fb-input" placeholder="Enter your full name" />
</div>
```

### Password input

Includes a show/hide toggle using a Material Symbol icon.

```html
<div class="fb-field">
  <label class="fb-label">Password</label>
  <div class="fb-input-wrapper">
    <input type="password" class="fb-input" placeholder="Enter your password" />
    <button class="fb-input-icon-btn" type="button" aria-label="Toggle password visibility">
      <span class="material-symbols-outlined">visibility</span>
    </button>
  </div>
</div>
```

### Textarea

Multi-line input. Label and states are identical to text input.

```html
<div class="fb-field">
  <label class="fb-label">Message</label>
  <textarea class="fb-input fb-textarea" placeholder="Write your message here"></textarea>
</div>
```

### Search input

Includes a search icon on the left. Used for product search, filter search.

```html
<div class="fb-field">
  <div class="fb-input-wrapper">
    <span class="fb-input-icon material-symbols-outlined">search</span>
    <input type="search" class="fb-input fb-input--with-icon" placeholder="Search products" />
  </div>
</div>
```

### With helper text

```html
<div class="fb-field">
  <label class="fb-label">Email Address</label>
  <input type="email" class="fb-input" placeholder="you@example.com" />
  <span class="fb-helper-text">We'll use this to send your order confirmation.</span>
</div>
```

### With error

```html
<div class="fb-field fb-field--error">
  <label class="fb-label">Email Address</label>
  <input type="email" class="fb-input" placeholder="you@example.com" />
  <span class="fb-error-text">Please enter a valid email address.</span>
</div>
```

---

## CSS Reference

```css
/* Field wrapper */
.fb-field {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
  margin-bottom: 20px;
}

/* Label */
.fb-label {
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: #2E2E2E;
}

/* Input */
.fb-input {
  width: 100%;
  height: 40px;
  padding: 0 16px;
  background-color: #FFFFFF;
  border: 1px solid #BCBFD2;
  border-radius: 3px;
  font-family: "Mulish", sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #2E2E2E;
  outline: none;
  transition: border-color 0.2s ease-in-out, background-color 0.2s ease-in-out;
  appearance: none;
}

.fb-input::placeholder {
  color: #BCBFD2;
}

.fb-input:focus {
  border-color: #AAC9BA;
}

.fb-input:disabled {
  background-color: #EAEBF1;
  cursor: not-allowed;
}

/* Large size */
.fb-input--lg {
  height: 48px;
  padding: 0 20px;
}

/* Textarea */
.fb-textarea {
  height: auto;
  min-height: 96px;
  padding: 12px 16px;
  resize: vertical;
  line-height: 1.6;
}

/* Input wrapper (for icon or toggle) */
.fb-input-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.fb-input-wrapper .fb-input {
  width: 100%;
}

/* Left icon (e.g. search) */
.fb-input-icon {
  position: absolute;
  left: 12px;
  font-size: 20px;
  color: #BCBFD2;
  pointer-events: none;
}

.fb-input--with-icon {
  padding-left: 44px;
}

/* Right icon button (e.g. password toggle) */
.fb-input-icon-btn {
  position: absolute;
  right: 12px;
  background: none;
  border: none;
  cursor: pointer;
  color: #BCBFD2;
  display: flex;
  align-items: center;
  padding: 0;
  transition: color 0.2s ease-in-out;
}

.fb-input-icon-btn:hover {
  color: #2E2E2E;
}

/* Helper text */
.fb-helper-text {
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: #BCBFD2;
  margin-top: -4px;
}

/* Error state */
.fb-field--error .fb-input {
  border-color: #C9A0A0;
}

.fb-error-text {
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: #C9A0A0;
  margin-top: -4px;
}
```

---

## Usage Rules

- Always include a visible label. Do not rely on placeholder text as a label — placeholders disappear on input and hurt accessibility.
- Labels are always uppercase at 12px. Do not use sentence case or larger sizes for labels.
- Use helper text to provide format hints (e.g. "DD/MM/YYYY") before the user interacts, not after an error.
- Show error text only after the user has interacted with the field (on blur or on form submit), never on initial load.
- Inputs, textareas, and search fields all share the same border, background, and focus rules. Do not create one-off variations.
- Do not use Angular Material `mat-form-field` for new input components. Use these custom classes instead.
