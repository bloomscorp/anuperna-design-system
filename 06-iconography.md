# Iconography

All icons in Anuprerna's interface use **Material Symbols Outlined** — the modern, variable-font version of Google's Material Icons. This is the single approved icon source. Icons from other libraries, custom SVG icons assembled ad hoc, and emojis used as UI icons are not permitted in product interfaces.

---

## Why a single library

Using icons from multiple sources creates visual inconsistency — different stroke weights, optical sizes, and metaphors sitting side by side. Material Symbols Outlined provides a large, well-maintained set that covers almost every UI need, and its variable font axes allow fine-grained control over weight and size without loading multiple font files.

---

## Loading

Material Symbols Outlined is loaded via Google Fonts:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined" />
```

The base CSS class already in use:

```css
.material-symbols-outlined {
  font-family: 'Material Symbols Outlined', sans-serif;
}
```

Usage in HTML:

```html
<span class="material-symbols-outlined">search</span>
```

---

## Variant

Always use the **Outlined** variant. Do not use Material Icons Filled, Rounded, or Sharp — these are separate font families and produce a different visual weight that conflicts with the Outlined style.

---

## Sizes

Icon sizes are fixed to four values that align with the spacing scale and typography scale:

| Size | Value | Usage |
|---|---|---|
| Small | 16px | Inline icons within body text, tags, labels |
| Default | 20px | Standard UI icons — buttons, inputs, navigation items |
| Medium | 24px | Standalone icons, list items, card actions |
| Large | 32px | Feature icons, empty states, section markers |

Set icon size via `font-size`:

```css
.material-symbols-outlined {
  font-size: 20px; /* default */
}
```

Do not use arbitrary sizes outside this set.

---

## Color

Icons follow the same color rules as text:

| Context | Color |
|---|---|
| Default (on white or any light surface) | `#2E2E2E` |
| On a colored surface, decorative or accent | Matching foreground pastel (e.g. `#D5B3B9` on a Rose surface) |
| Disabled state | `#BCBFD2` (Mist foreground) |

Icons should never use the light pastel background colors — they will not have sufficient contrast against white or any surface.

---

## Optical size axis

Material Symbols supports an `opsz` axis that fine-tunes rendering at different sizes. Set it to match the rendered size:

```css
.material-symbols-outlined {
  font-variation-settings: 'opsz' 20;
}
```

For the four defined sizes, use `opsz` values of `16`, `20`, `24`, and `40` respectively.

---

## Emoji policy

Emojis are permitted only in editorial content — blog posts, product descriptions, marketing copy — where they serve an expressive or illustrative purpose. They are not permitted as functional UI icons (navigation, actions, status indicators, form elements). If no suitable Material Symbol exists for a UI need, raise it as a design decision rather than substituting an emoji.

---

## Exceptions

Custom SVG icons may be used only when Material Symbols does not provide a suitable metaphor for a brand-specific concept (e.g. a craft or textile-specific symbol). Any such exception must be documented here with the icon name, its SVG source, and the specific contexts where it applies. Ad hoc one-off SVGs that are not documented are not permitted.
