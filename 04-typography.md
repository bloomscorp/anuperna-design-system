# Typography

Anuprerna's typography pairs two typefaces. DM Serif Text brings warmth and editorial character to hero and display moments. Mulish handles all functional text — headings, body, labels — with a clean, friendly legibility. Inter is available via the font loader but is not assigned a role in this design system.

---

## Typefaces

### DM Serif Text
A classical serif used exclusively for display and editorial contexts. It carries emotional weight and signals craft and quality. Only one weight is available — 400 Regular — so it should never be simulated as bold.

**Use for:** Display text, H1 page titles, pull quotes, hero headlines.

### Mulish
The primary typeface for all functional and body text. Its variable weight axis (200–1000) provides flexibility for creating hierarchy within a single font family.

**Use for:** H2 through H4 headings, body copy, labels, captions, navigation, buttons, and all UI text.

---

## Loading

Both typefaces are loaded via Google Fonts.

**Mulish**
```
https://fonts.googleapis.com/css2?family=Mulish:ital,wght@0,200..1000;1,200..1000&display=swap
```

**DM Serif Text**
```
https://fonts.googleapis.com/css2?family=DM+Serif+Text&display=swap
```

**CSS usage for Mulish (primary font):**
```css
.fb-font-primary {
  font-family: "Mulish", sans-serif;
  font-optical-sizing: auto;
  font-style: normal;
}
```

---

## Type Scale

| Token | Font | Size | Weight | Line Height | Usage |
|---|---|---|---|---|---|
| Display | DM Serif Text | 40px | 400 | 1.2 | Hero headlines, carousel headers |
| H1 | DM Serif Text | 32px | 400 | 1.25 | Page titles |
| H2 | Mulish | 26px | 700 | 1.3 | Section headings |
| H3 | Mulish | 20px | 600 | 1.35 | Card headings, sub-sections |
| H4 | Mulish | 17px | 600 | 1.4 | Grouped labels, minor headings |
| Body | Mulish | 16px | 400 | 1.6 | All body copy, product descriptions |
| Body Small | Mulish | 14px | 400 | 1.6 | Supporting text, secondary descriptions |
| Label | Mulish | 12px | 500 | 1.4 | Tags, form labels, navigation items |
| Caption | Mulish | 11px | 400 | 1.4 | Image captions, footnotes |

---

## Weights in Use

From Mulish's available range, only four weights are actively used:

| Weight | Value | Used for |
|---|---|---|
| Regular | 400 | Body, Body Small, Caption |
| Medium | 500 | Label |
| Semi Bold | 600 | H3, H4 |
| Bold | 700 | H2 |

Weights outside this set (200, 300, 800, 900) are available but not part of the standard scale. Avoid using them without a specific design rationale.

---

## Italic Usage

Mulish supports italic at all weights. Italics are appropriate for:
- Emphasis within body copy
- Pull quotes when DM Serif Text is not used
- Foreign words or titles of works

DM Serif Text does not have an italic variant and should never be artificially slanted.

---

## Usage Rules

- Display and H1 always use DM Serif Text. Do not substitute Mulish for these levels.
- Never use DM Serif Text below H1. It is not designed for body-text sizes.
- Text color is always `#2E2E2E`. Do not use surface pastel colors for text.
- Do not use weight 400 for headings — headings at H2 and below always use 600 or 700.
- Avoid mixing more than two type scales within a single card or content block.
