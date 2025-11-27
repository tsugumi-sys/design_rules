# Google-Style Design Complete Implementation Guide

By analyzing Google's **Material Design 3 (Material You)** guidelines and implementation patterns from https://m3.material.io/, this document defines a **fully reproducible Google-style design rule set** for web.
Following these standards ensures your design matches **Google's official UI aesthetics and structure**.

---

## 1. Color System (Palette, Usage, HEX Codes)

### Main Color Palette (Google Cloud Console Style)

Material Design 3 emphasizes *dynamic color palettes* derived from a primary key color. This implementation uses Google Cloud Console's blue palette.

**Core Roles**

- **Primary** — brand accent, key interactive color
- **Secondary** — supportive accent
- **Tertiary** — complementary accent
- **Surface** — backgrounds, cards
- **Error** — alerts, validation errors
- **On Colors** — text/icons placed on colored surfaces

**Google Cloud Console Colors**

```css
/* Primary (Google Blue) */
--md-color-primary: #1a73e8;
--md-color-primary-container: #d3e3fd;
--md-color-on-primary: #ffffff;
--md-color-on-primary-container: #001d35;

/* Secondary */
--md-color-secondary: #5f6368;
--md-color-secondary-container: #e8eaed;
--md-color-on-secondary: #ffffff;
--md-color-on-secondary-container: #1a1c1e;

/* Tertiary */
--md-color-tertiary: #34a853;
--md-color-tertiary-container: #c8e6c9;
--md-color-on-tertiary: #ffffff;

/* Surface / Background */
--md-color-background: #ffffff;
--md-color-surface: #ffffff;
--md-color-surface-variant: #f1f3f4;
--md-color-on-surface: #202124;
--md-color-on-surface-variant: #5f6368;

/* Error */
--md-color-error: #d93025;
--md-color-on-error: #ffffff;
--md-color-error-container: #fce8e6;

/* Outline */
--md-color-outline: #dadce0;
--md-color-outline-variant: #e8eaed;
```

**Tonal Palette Structure**

Each key color generates a *tonal palette* with 13 tones:
`0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 95, 99, 100`
Used for dark/light modes and surface elevation layers.

**Color Usage Rules**

* **Primary (#1a73e8)**: primary buttons, active elements, navigation highlights, links
* **Secondary (#5f6368)**: text buttons, secondary actions, supporting UI
* **Tertiary (#34a853)**: success states, confirmations
* **Surface**: cards, sheets, modals, dialogs
* **Error (#d93025)**: destructive actions, alerts, validation errors
* **On Colors**: ensure legibility with ≥4.5:1 contrast ratio

---

## 2. Corner Radius (border-radius)

Material Design 3 uses a **shape scale** to unify rounded corners with updated values.

| Component Type            | Border Radius |
| ------------------------- | ------------- |
| Extra Small (chips)       | 8px           |
| Small (buttons, fields)   | 12px          |
| Medium (cards)            | 16px          |
| Large (dialogs, sheets)   | 28px          |
| Extra Large (modals)      | 28px          |
| Full (FAB, pill buttons)  | 999px         |

**Examples**

```css
/* Buttons */
button {
  border-radius: 12px;
}

/* Cards */
.card {
  border-radius: 16px;
}

/* Dialogs */
.dialog {
  border-radius: 28px;
}

/* FAB (Floating Action Button) */
.fab {
  border-radius: 16px; /* For square FAB */
  border-radius: 999px; /* For circular FAB */
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

/* Hover - 8% overlay */
background-color: #1557b0; /* Darker blue */

/* Pressed - 12% overlay */
background-color: #0d47a1;

/* Disabled */
opacity: 0.38;
pointer-events: none;
cursor: not-allowed;
```

**Material 3 Elevation System**

| Level       | Usage                    | Shadow                                                                  |
| ----------- | ------------------------ | ----------------------------------------------------------------------- |
| Level 0     | No elevation             | none                                                                    |
| Level 1     | Cards, switches          | `0 1px 2px 0 rgba(0,0,0,0.30), 0 1px 3px 1px rgba(0,0,0,0.15)`         |
| Level 2     | Hover states, menus      | `0 1px 2px 0 rgba(0,0,0,0.30), 0 2px 6px 2px rgba(0,0,0,0.15)`         |
| Level 3     | Modals, dialogs          | `0 4px 8px 3px rgba(0,0,0,0.15), 0 1px 3px 0 rgba(0,0,0,0.30)`         |
| Level 4     | Navigation drawers       | `0 6px 10px 4px rgba(0,0,0,0.15), 0 2px 3px 0 rgba(0,0,0,0.30)`        |
| Level 5     | Maximum elevation        | `0 8px 12px 6px rgba(0,0,0,0.15), 0 4px 4px 0 rgba(0,0,0,0.30)`        |

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

Material Design 3 uses **Google Sans** for display/headlines and **Roboto** for body text.

```css
body {
  font-family: 'Roboto', 'Noto Sans', sans-serif;
  color: var(--md-color-on-surface);
}

h1, h2, h3, h4, h5, h6 {
  font-family: 'Google Sans', 'Roboto', sans-serif;
}

/* Material 3 Type Scale */
.display-large { font-size: 57px; line-height: 64px; font-weight: 400; margin-bottom: 32px; }
.display-medium { font-size: 45px; line-height: 52px; font-weight: 400; margin-bottom: 28px; }
.display-small { font-size: 36px; line-height: 44px; font-weight: 400; margin-bottom: 24px; }

.headline-large { font-size: 32px; line-height: 40px; font-weight: 400; margin-bottom: 20px; }
.headline-medium { font-size: 28px; line-height: 36px; font-weight: 400; margin-bottom: 18px; }
.headline-small { font-size: 24px; line-height: 32px; font-weight: 400; margin-bottom: 16px; }

.title-large { font-size: 22px; line-height: 28px; font-weight: 400; margin-bottom: 16px; }
.title-medium { font-size: 16px; line-height: 24px; font-weight: 500; margin-bottom: 12px; }
.title-small { font-size: 14px; line-height: 20px; font-weight: 500; margin-bottom: 12px; }

.body-large { font-size: 16px; line-height: 24px; font-weight: 400; margin-bottom: 16px; }
.body-medium { font-size: 14px; line-height: 20px; font-weight: 400; margin-bottom: 12px; }
.body-small { font-size: 12px; line-height: 16px; font-weight: 400; margin-bottom: 8px; }

.label-large { font-size: 14px; line-height: 20px; font-weight: 500; }
.label-medium { font-size: 12px; line-height: 16px; font-weight: 500; }
.label-small { font-size: 11px; line-height: 16px; font-weight: 500; }
```

**Spacing Between Text Elements**

* Tight relation: 4px
* Related: 8px
* Loosely related: 16px
* Section separation: 24px
* Independent: 32px

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
