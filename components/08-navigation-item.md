# Navigation Item

The navigation item is the individual link or button within any navigational structure. Four variants exist depending on context: **Primary** (top-level nav links), **Tab** (page-level switching), **Breadcrumb** (path indication), and **Sidebar** (vertical account or dashboard navigation). The Navigation Bar organism is built from Primary navigation items; this document covers the item itself.

---

## Primary Navigation Item

Used in the top navigation bar. Text is uppercase with a hover underline that animates in from the left.

### Anatomy & Spec

| Part | Spec |
|---|---|
| Font | Mulish, 14px, 400, uppercase, 0.04em letter-spacing |
| Padding | `5px 10px` |
| Color (on dark nav) | `#FFFFFF` |
| Color (on light nav) | `#2E2E2E` |
| Underline | `2px`, `border-radius: 10px`, animates from 0% to 80% width on hover |
| Underline color (on dark nav) | `#FFFFFF` |
| Underline color (on light nav) | `#2E2E2E` |
| Active underline | Persistent, same as hover |
| Transition | `all 0.5s` |

### States

| State | Underline width | Notes |
|---|---|---|
| Default | `0%` | No underline visible |
| Hover | `80%` | Underline animates in |
| Active (current page) | `80%` | Underline always visible |

### HTML Structure

```html
<a href="/fabrics" class="fb-nav-item fb-nav-item--active">Fabric</a>
<a href="/accessories" class="fb-nav-item">Accessories</a>
<a href="/homeware" class="fb-nav-item">Homeware</a>
```

### CSS

```css
.fb-nav-item {
  position: relative;
  display: inline-block;
  padding: 5px 10px;
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #FFFFFF;
  text-decoration: none;
  cursor: pointer;
  background: transparent;
  border: none;
  transition: all 0.5s;
}

/* Underline */
.fb-nav-item::before {
  content: '';
  position: absolute;
  bottom: 5px;
  left: 10%;
  width: 0%;
  height: 2px;
  border-radius: 10px;
  background-color: currentColor;
  transition: width 0.5s;
}

.fb-nav-item:hover::before,
.fb-nav-item--active::before {
  width: 80%;
}

/* On a light navigation background */
.fb-nav-item--dark {
  color: #2E2E2E;
}
```

---

## Tab Item

Used for switching between sections within a page — product detail tabs (Description, Specifications, Reviews), account sections (Orders, Profile, Addresses).

### Anatomy & Spec

| Part | Spec |
|---|---|
| Font | Mulish, 14px, 500, uppercase, 0.04em letter-spacing |
| Padding | `12px 16px` |
| Color (default) | `#BCBFD2` |
| Color (active) | `#2E2E2E` |
| Active indicator | `2px solid #AAC9BA`, bottom border |
| Hover color | `#2E2E2E` |
| Transition | `all 0.2s ease-in-out` |

### States

| State | Text color | Bottom border |
|---|---|---|
| Default | `#BCBFD2` | None |
| Hover | `#2E2E2E` | None |
| Active | `#2E2E2E` | `2px solid #AAC9BA` |
| Disabled | `#BCBFD2`, opacity 0.4 | None |

### HTML Structure

```html
<div class="fb-tabs" role="tablist">
  <button class="fb-tab" role="tab" aria-selected="false">Description</button>
  <button class="fb-tab fb-tab--active" role="tab" aria-selected="true">Specifications</button>
  <button class="fb-tab" role="tab" aria-selected="false">Reviews</button>
</div>
```

### CSS

```css
.fb-tabs {
  display: flex;
  border-bottom: 1px solid #EAEBF1;
  gap: 0;
}

.fb-tab {
  padding: 12px 16px;
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  color: #BCBFD2;
  background: none;
  border: none;
  border-bottom: 2px solid transparent;
  margin-bottom: -1px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  white-space: nowrap;
}

.fb-tab:hover {
  color: #2E2E2E;
}

.fb-tab--active {
  color: #2E2E2E;
  border-bottom-color: #AAC9BA;
}

.fb-tab:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}
```

---

## Breadcrumb Item

Used to show the user's location within the site hierarchy. The last item (current page) is non-linked and dark; all preceding items are muted links.

### Anatomy & Spec

| Part | Spec |
|---|---|
| Font | Mulish, 12px, 400 |
| Link color | `#BCBFD2` |
| Link hover color | `#2E2E2E` |
| Current page color | `#2E2E2E` |
| Separator | `›` character, `#BCBFD2` |
| Gap between items | `8px` |

### HTML Structure

```html
<nav class="fb-breadcrumb" aria-label="Breadcrumb">
  <ol class="fb-breadcrumb__list">
    <li class="fb-breadcrumb__item">
      <a href="/" class="fb-breadcrumb__link">Home</a>
    </li>
    <li class="fb-breadcrumb__item">
      <a href="/fabric" class="fb-breadcrumb__link">Fabric</a>
    </li>
    <li class="fb-breadcrumb__item fb-breadcrumb__item--current" aria-current="page">
      Handwoven Cotton
    </li>
  </ol>
</nav>
```

### CSS

```css
.fb-breadcrumb__list {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 8px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.fb-breadcrumb__item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-family: "Mulish", sans-serif;
  font-size: 12px;
  font-weight: 400;
  color: #2E2E2E;
}

.fb-breadcrumb__item:not(:last-child)::after {
  content: '›';
  color: #BCBFD2;
}

.fb-breadcrumb__link {
  color: #BCBFD2;
  text-decoration: none;
  transition: color 0.2s ease-in-out;
}

.fb-breadcrumb__link:hover {
  color: #2E2E2E;
}

.fb-breadcrumb__item--current {
  color: #2E2E2E;
}
```

---

## Sidebar Item

Used in vertical navigation — account pages, dashboards, settings panels. Supports an optional leading icon and an active state with a Sage surface background.

### Anatomy & Spec

| Part | Spec |
|---|---|
| Font | Mulish, 14px, 400 |
| Height | `44px` |
| Padding | `0 16px` |
| Border radius | `3px` |
| Icon size | `20px`, Material Symbol |
| Gap between icon and label | `12px` |
| Default color | `#2E2E2E` |
| Active background | `#E9F1ED` |
| Active text/icon color | `#AAC9BA` |
| Hover background | `#F9F4F5` |

### States

| State | Background | Text & icon color |
|---|---|---|
| Default | `transparent` | `#2E2E2E` |
| Hover | `#F9F4F5` | `#2E2E2E` |
| Active | `#E9F1ED` | `#AAC9BA` |
| Disabled | `transparent` | `#BCBFD2`, opacity 0.4 |

### HTML Structure

```html
<nav class="fb-sidebar">
  <a href="/account/orders" class="fb-sidebar-item fb-sidebar-item--active">
    <span class="material-symbols-outlined">package_2</span>
    Orders
  </a>
  <a href="/account/profile" class="fb-sidebar-item">
    <span class="material-symbols-outlined">person</span>
    Profile
  </a>
  <a href="/account/addresses" class="fb-sidebar-item">
    <span class="material-symbols-outlined">location_on</span>
    Addresses
  </a>
</nav>
```

### CSS

```css
.fb-sidebar {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.fb-sidebar-item {
  display: flex;
  align-items: center;
  gap: 12px;
  height: 44px;
  padding: 0 16px;
  border-radius: 3px;
  font-family: "Mulish", sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: #2E2E2E;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

.fb-sidebar-item .material-symbols-outlined {
  font-size: 20px;
  color: inherit;
}

.fb-sidebar-item:hover {
  background-color: #F9F4F5;
}

.fb-sidebar-item--active {
  background-color: #E9F1ED;
  color: #AAC9BA;
  font-weight: 500;
}

.fb-sidebar-item--disabled {
  color: #BCBFD2;
  opacity: 0.4;
  cursor: not-allowed;
  pointer-events: none;
}
```

---

## Usage Rules

- Primary nav items are always uppercase. Do not use sentence case in top-level navigation.
- Tab items are always uppercase. Do not use them for external links — tabs switch content within the same page.
- Breadcrumbs must reflect the actual URL hierarchy. Do not fabricate intermediate levels.
- Breadcrumbs are hidden on mobile when the path depth is 2 or fewer — they add noise without value at that depth.
- Sidebar items are only used in vertical navigation contexts (account, dashboard, settings). Do not adapt them for horizontal use.
- Never show more than one active state per navigation variant on the same page (one active primary nav item, one active tab, one active sidebar item).
