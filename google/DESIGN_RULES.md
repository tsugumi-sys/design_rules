# Google-Style Design Complete Implementation Guide

By analyzing Google's **Material Design 3 (Material You)** guidelines and implementation patterns, this document defines a **fully reproducible Google-style design rule set** for web.  
Following these standards ensures your design matches **Google’s official UI aesthetics and structure**.

---

## 1. Color System (Palette, Usage, HEX Codes)

### Main Color Palette

Material Design emphasizes *dynamic color palettes* derived from a primary key color.

**Core Roles**

- **Primary** — brand accent, key interactive color  
- **Secondary** — supportive accent  
- **Tertiary** — complementary accent  
- **Neutral (Surface)** — backgrounds, cards  
- **Error** — alerts, validation errors  
- **"On" Colors** — text/icons placed on colored surfaces

**Example (Material 3 Default)**

```css
/* Primary */
--md-color-primary: #6200EE;
--md-color-on-primary: #FFFFFF;

/* Secondary */
--md-color-secondary: #03DAC6;
--md-color-on-secondary: #000000;

/* Background / Surface */
--md-color-background: #FFFFFF;
--md-color-surface: #FFFFFF;
--md-color-on-surface: #000000;
--md-color-on-background: #000000;

/* Error */
--md-color-error: #B00020;
--md-color-on-error: #FFFFFF;
````

**Tonal Palette Structure**

Each key color generates a *tonal palette* (usually 13 tones):
`0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 95, 99, 100`
Used for dark/light modes and elevation layers.

**Color Usage Rules**

* **Primary**: buttons, active elements, navigation highlights
* **Secondary**: floating buttons, selections
* **Surface**: cards, sheets, modals
* **Error**: destructive actions, alerts
* **On Colors**: ensure legibility and 4.5:1 contrast ratio minimum

---

## 2. Corner Radius (border-radius)

Material uses a **shape scale** to unify rounded corners.

| Component Type            | Border Radius |
| ------------------------- | ------------- |
| Small (chips, icons)      | 4px           |
| Medium (buttons, fields)  | 8px           |
| Large (cards, containers) | 12px          |
| XL (dialogs, modals)      | 16px          |
| Full (FAB, pill)          | 24px+         |

**Examples**

```css
button {
  border-radius: 8px;
}

.card {
  border-radius: 12px;
}

.dialog {
  border-radius: 16px;
}
```

---

## 3. Spacing System (Margin & Padding)

Material uses an **8px grid system** for spacing and layout rhythm.

**Base Units**

| Scale       | Value | Usage            |
| ----------- | ----- | ---------------- |
| Extra Small | 4px   | icon/text gap    |
| Small       | 8px   | compact elements |
| Medium      | 16px  | standard padding |
| Large       | 24px  | section spacing  |
| XL          | 32px  | layout margins   |
| XXL         | 48px  | page padding     |

**Component Spacing**

```css
/* Buttons */
button.small { padding: 8px 16px; min-height: 36px; }
button.medium { padding: 12px 20px; min-height: 40px; }
button.large { padding: 16px 24px; min-height: 48px; }

/* Cards */
.card { padding: 16px; }
.card-large { padding: 24px; }

/* Page Layout */
.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 16px; /* mobile */
}
@media (min-width: 768px) {
  .container { padding: 0 24px; }
}
@media (min-width: 1024px) {
  .container { padding: 0 32px; }
}
```

---

## 4. Contrast & Accessibility

**Contrast Ratios (WCAG 2.1)**

* Normal text: ≥ 4.5 : 1
* Large text (≥ 18 pt / 14 pt bold): ≥ 3 : 1
* UI components: ≥ 3 : 1

**Interactive State Guidelines**

```css
/* Default */
background-color: var(--md-color-primary);

/* Hover */
background-color: color-mix(in srgb, var(--md-color-primary) 85%, black);

/* Disabled */
opacity: 0.38;
pointer-events: none;
```

**State Elevations**

| State   | Elevation | Shadow Example                |
| ------- | --------- | ----------------------------- |
| Default | 1         | `0 1px 3px rgba(0,0,0,0.12)`  |
| Hover   | 2         | `0 4px 6px rgba(0,0,0,0.16)`  |
| Active  | 3         | `0 6px 12px rgba(0,0,0,0.24)` |

---

## 5. Card Design

**Base Card**

```css
.card {
  background: var(--md-color-surface);
  border-radius: 12px;
  box-shadow:
    0 1px 3px rgba(0,0,0,0.12),
    0 1px 2px rgba(0,0,0,0.24);
  padding: 16px;
}
```

**Card Variants**

```css
.card-outlined {
  border: 1px solid rgba(0,0,0,0.12);
  box-shadow: none;
}

.card-elevated {
  box-shadow:
    0 4px 8px rgba(0,0,0,0.16),
    0 2px 4px rgba(0,0,0,0.12);
}
```

**Structure**

```css
.card-header {
  margin-bottom: 12px;
  font-weight: 600;
}

.card-body {
  line-height: 1.5;
  color: var(--md-color-on-surface);
}

.card-footer {
  margin-top: 16px;
  border-top: 1px solid rgba(0,0,0,0.12);
  padding-top: 12px;
}
```

---

## 6. Typography System

Google’s typography uses the **Roboto** and **Noto** font families.

```css
body {
  font-family: 'Roboto', 'Noto Sans', sans-serif;
  color: var(--md-color-on-surface);
}

/* Type Scale */
.h1 { font-size: 96px; line-height: 112px; margin-bottom: 32px; }
.h2 { font-size: 60px; line-height: 72px; margin-bottom: 24px; }
.h3 { font-size: 48px; line-height: 56px; margin-bottom: 20px; }
.h4 { font-size: 34px; line-height: 40px; margin-bottom: 16px; }
.h5 { font-size: 24px; line-height: 32px; margin-bottom: 16px; }
.h6 { font-size: 20px; line-height: 28px; margin-bottom: 12px; }
.body1 { font-size: 16px; line-height: 24px; margin-bottom: 16px; }
.body2 { font-size: 14px; line-height: 20px; margin-bottom: 12px; }
.caption { font-size: 12px; line-height: 16px; margin-bottom: 8px; color: #666; }
```

**Spacing Between Text Elements**

* Tight relation: 4 px
* Related: 8 px
* Loosely related: 16 px
* Section separation: 24 px
* Independent: 32 px

---

## 7. Layout Grid System

Material uses a **12-column responsive grid**.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 16px;
}

@media (min-width: 768px) {
  .grid { gap: 20px; }
}

@media (min-width: 1024px) {
  .grid { gap: 24px; }
}
```

**Breakpoints**

| Device  | Width      | Container Padding |
| ------- | ---------- | ----------------- |
| Mobile  | ≤ 767px    | 16px              |
| Tablet  | 768–1023px | 24px              |
| Desktop | ≥ 1024px   | 32px              |

---

## 8. Implementation Checklist

### Required

* [ ] Use dynamic color palette (Material Color System)
* [ ] Maintain ≥ 4.5 : 1 contrast ratio
* [ ] Apply shape scale for rounded corners
* [ ] Follow 8px-based spacing grid
* [ ] Use elevation tokens for shadows
* [ ] Use Roboto/Noto system fonts

### Recommended

* [ ] Dark mode support
* [ ] Accessibility compliance
* [ ] Responsive grid system
* [ ] Motion and transitions (easing, duration)
* [ ] Color roles consistent with theme tokens

---

By following this guide, you can reproduce **Google Material Design** precision and achieve a **modern, accessible, and adaptive interface** consistent with Google’s products.
