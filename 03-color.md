# Color

Anuprerna's color language is built around softness and calm. The palette uses desaturated pastels as its primary surface colors, paired with slightly deeper variants of the same hues for foreground elements. Text always uses a near-black tone to ensure readability across all surfaces.

---

## Surface Colors

Each color in the palette exists as a light/dark pair sharing the same hue. The light variant is used for backgrounds and containers; the dark variant is used for foreground UI elements such as borders, icons, badges, and interactive states.

### White
The base canvas. Used as the default page and component background.

| Role | Hex |
|---|---|
| Base | `#FFFFFF` |

---

### Rose

| Role | Hex | Usage |
|---|---|---|
| Background | `#F9F4F5` | Page sections, cards, tinted containers |
| Foreground | `#D5B3B9` | Borders, icons, tags, active states on Rose surfaces |

---

### Sage

| Role | Hex | Usage |
|---|---|---|
| Background | `#E9F1ED` | Page sections, cards, tinted containers |
| Foreground | `#AAC9BA` | Borders, icons, tags, active states on Sage surfaces |

---

### Lavender

| Role | Hex | Usage |
|---|---|---|
| Background | `#EBE9F2` | Page sections, cards, tinted containers |
| Foreground | `#BFB9D6` | Borders, icons, tags, active states on Lavender surfaces |

---

### Mist

| Role | Hex | Usage |
|---|---|---|
| Background | `#EAEBF1` | Page sections, cards, tinted containers |
| Foreground | `#BCBFD2` | Borders, icons, tags, active states on Mist surfaces |

---

## Text Color

There is a single text color used across all surfaces. The surface pastel colors are never used for text.

| Role | Hex | Usage |
|---|---|---|
| Primary Text | `#2E2E2E` | All body text, headings, labels, captions |

---

## Semantic Colors

Semantic colors communicate system states — errors, confirmations, and cautions. They follow the same light/dark pairing logic as the surface palette, keeping them consistent with the overall brand tone.

### Error

Used for destructive actions, validation errors, and failure states.

| Role | Hex |
|---|---|
| Background | `#F5EAEA` |
| Foreground | `#C9A0A0` |

---

### Success

Used for confirmations, completed actions, and positive feedback.

| Role | Hex |
|---|---|
| Background | `#E9F5EA` |
| Foreground | `#9FC6A6` |

---

### Warning

Used for caution states and non-blocking alerts.

| Role | Hex |
|---|---|
| Background | `#F5F0E0` |
| Foreground | `#C9B080` |

---

## Pairing Rules

- Always pair a foreground color with its matching background color. Do not mix foreground colors across hue families (e.g. do not use Rose Foreground on a Sage Background).
- White (`#FFFFFF`) is a neutral base and can be paired with any foreground color.
- Text (`#2E2E2E`) is always used for readable copy — never use a surface color for text.
- Semantic foreground colors may appear as text only in short labels (e.g. status badges) where context makes the meaning clear. Body text always uses `#2E2E2E`.

---

## Accessibility

All text in `#2E2E2E` on any light surface color in this palette meets WCAG AA contrast requirements. The foreground pastel colors are intended for UI elements (borders, icons, decorative marks), not for body text, and do not meet text contrast thresholds on their paired backgrounds.
