# Form Group

A form group is a layout molecule that organises form fields — inputs, selects, checkboxes, radios — into a structured, consistent form. It defines spacing between fields, multi-column layouts, section groupings, and action areas. Individual field components are documented in their own files; this document covers how they are composed together.

---

## Field Spacing

| Gap | Value | Context |
|---|---|---|
| Between fields in the same group | `20px` | Consistent with grid gap |
| Between form sections | `40px` | Gives sections clear visual separation |
| Section title to first field | `16px` | |
| Field label to input | `8px` | Defined in individual field components |

---

## Layout Patterns

### Single column
Default layout. Each field takes the full width of the form. Use for simple forms — login, contact, checkout address.

```html
<div class="fb-form">
  <div class="fb-field">
    <label class="fb-label">Full Name</label>
    <input type="text" class="fb-input" placeholder="Enter your full name" />
  </div>
  <div class="fb-field">
    <label class="fb-label">Email Address</label>
    <input type="email" class="fb-input" placeholder="you@example.com" />
  </div>
  <div class="fb-field">
    <label class="fb-label">Message</label>
    <textarea class="fb-input fb-textarea" placeholder="Write your message"></textarea>
  </div>
</div>
```

### Two column
Two fields sit side by side. Use for pairs of related fields — first name + last name, city + postcode, quantity + unit.

```html
<div class="fb-form">
  <div class="fb-field-row">
    <div class="fb-field">
      <label class="fb-label">First Name</label>
      <input type="text" class="fb-input" placeholder="First name" />
    </div>
    <div class="fb-field">
      <label class="fb-label">Last Name</label>
      <input type="text" class="fb-input" placeholder="Last name" />
    </div>
  </div>
  <div class="fb-field">
    <label class="fb-label">Email Address</label>
    <input type="email" class="fb-input" placeholder="you@example.com" />
  </div>
</div>
```

### Three column
Three fields per row. Use only for compact, data-entry-heavy forms where fields are short (e.g. dimensions: length, width, height).

```html
<div class="fb-field-row fb-field-row--3">
  <div class="fb-field">
    <label class="fb-label">Length (cm)</label>
    <input type="number" class="fb-input" />
  </div>
  <div class="fb-field">
    <label class="fb-label">Width (cm)</label>
    <input type="number" class="fb-input" />
  </div>
  <div class="fb-field">
    <label class="fb-label">Height (cm)</label>
    <input type="number" class="fb-input" />
  </div>
</div>
```

### Mixed
Combine full-width and multi-column rows as needed. Each `.fb-field-row` handles its own column layout independently.

---

## Form Sections

Large forms benefit from being divided into named sections — shipping details, personal information, order preferences. Each section has an optional title and description.

```html
<form class="fb-form">

  <div class="fb-form-section">
    <div class="fb-form-section__header">
      <h4 class="fb-form-section__title">Personal Information</h4>
      <p class="fb-form-section__description">Used for your account and order communications.</p>
    </div>
    <div class="fb-field-row">
      <div class="fb-field"> ... </div>
      <div class="fb-field"> ... </div>
    </div>
    <div class="fb-field"> ... </div>
  </div>

  <div class="fb-form-section">
    <div class="fb-form-section__header">
      <h4 class="fb-form-section__title">Shipping Address</h4>
    </div>
    <div class="fb-field"> ... </div>
    <div class="fb-field-row">
      <div class="fb-field"> ... </div>
      <div class="fb-field"> ... </div>
    </div>
  </div>

  <div class="fb-form-actions">
    <button type="button" class="btn btn-secondary">Cancel</button>
    <button type="submit" class="btn btn-primary">Save Details</button>
  </div>

</form>
```

---

## Form Actions

The action area holds the form's submit and cancel buttons. It always sits at the bottom of the form.

| Layout | Rule |
|---|---|
| Desktop | Right-aligned, buttons in a row. Primary button on the right. |
| Mobile | Full-width stacked buttons. Primary button on top. |

```html
<div class="fb-form-actions">
  <button type="button" class="btn btn-secondary">Cancel</button>
  <button type="submit" class="btn btn-primary">Submit Order</button>
</div>
```

---

## Inline form
A compact single-row form — typically a search bar or a newsletter signup — where label, input, and button sit on the same line.

```html
<div class="fb-form-inline">
  <div class="fb-input-wrapper">
    <span class="fb-input-icon material-symbols-outlined">search</span>
    <input type="search" class="fb-input fb-input--with-icon" placeholder="Search products" />
  </div>
  <button class="btn btn-primary">Search</button>
</div>
```

---

## CSS Reference

```css
/* ─── Form container ─── */

.fb-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 100%;
}

/* ─── Field row (multi-column) ─── */

.fb-field-row {
  display: flex;
  gap: 20px;
  width: 100%;
}

.fb-field-row .fb-field {
  flex: 1;
  margin-bottom: 0; /* gap handles spacing inside a row */
}

/* Three column */
.fb-field-row--3 .fb-field {
  flex: 1;
  min-width: 0; /* prevents overflow on small containers */
}

/* Collapse to single column on mobile */
@media (max-width: 768px) {
  .fb-field-row {
    flex-direction: column;
  }
}

/* ─── Form section ─── */

.fb-form-section {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.fb-form-section + .fb-form-section {
  padding-top: 40px;
  border-top: 1px solid #EAEBF1;
}

.fb-form-section__header {
  display: flex;
  flex-direction: column;
  gap: 4px;
  padding-bottom: 16px;
  border-bottom: 1px solid #EAEBF1;
}

.fb-form-section__title {
  font-family: "Mulish", sans-serif;
  font-size: 17px;
  font-weight: 600;
  color: #2E2E2E;
  margin: 0;
  line-height: 1.4;
}

.fb-form-section__description {
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #BCBFD2;
  margin: 0;
  line-height: 1.6;
}

/* ─── Form actions ─── */

.fb-form-actions {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 12px;
  padding-top: 20px;
  border-top: 1px solid #EAEBF1;
}

@media (max-width: 768px) {
  .fb-form-actions {
    flex-direction: column-reverse;
    align-items: stretch;
  }

  .fb-form-actions .btn {
    width: 100%;
    justify-content: center;
  }
}

/* ─── Inline form ─── */

.fb-form-inline {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
}

.fb-form-inline .fb-input-wrapper {
  flex: 1;
}

@media (max-width: 768px) {
  .fb-form-inline {
    flex-direction: column;
    align-items: stretch;
  }

  .fb-form-inline .btn {
    width: 100%;
    justify-content: center;
  }
}
```

---

## Usage Rules

- Never use three-column rows on mobile. The `fb-field-row` collapses to single column at 768px automatically, but three-column rows should also be manually reviewed at tablet width.
- Every form section that follows another must have a visible separator — the `border-top` on `.fb-form-section + .fb-form-section` handles this automatically.
- The form action area always has its own `border-top` to visually separate the controls from the fields.
- Do not put a form section title on every section. Use section titles only when a form is long enough (5+ fields) that grouping genuinely helps orientation.
- Primary submit action always goes on the right (desktop) or top (mobile). Cancel or back actions go left or below.
- Avoid disabling the submit button to indicate an incomplete form — instead, validate on submit and show inline error messages on the relevant fields.
