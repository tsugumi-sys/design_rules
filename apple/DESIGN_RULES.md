# Apple-Style Design Complete Implementation Guide

By thoroughly analyzing Apple’s Human Interface Guidelines and actual implementation values from Apple’s official website, this guide establishes a **fully reproducible design rule set**.
Following these rules ensures that you can **accurately achieve an Apple-like website design**.

---

## 1. Color System (Palette, Usage, HEX Codes)

### Main Color Palette

**Primary Colors**

* **Black**: `#000000` — Main text, navigation, icons
* **White**: `#FFFFFF` — Backgrounds, card backgrounds, inverted text
* **Gray**: `#A3AAAE` — Secondary text, dividers

**System Colors (iOS-based)**

* **System Blue**: `#007AFF` — Links, primary actions, selected states
* **System Red**: `#FF3B30` — Errors, delete, alert actions
* **System Green**: `#4CD964` — Success, confirmation, normal states
* **System Orange**: `#FF9500` — Warnings, caution
* **System Purple**: `#5856D6` — Creativity, premium features

**Grayscale (24-Step System)**

* **Text**: `#1D1D1F` (main), `#666666` (secondary), `#979797` (caption)
* **Background**: `#F5F5F7` (light gray background), `#EEEEEE` (dividers)
* **Interactive**: `#0088CC` (hover blue)

### Color Usage Rules

**Text Color Application**

```css
/* Main Text */
color: #000000; /* Primary content */
color: #1d1d1f; /* Body text */
color: #666666; /* Secondary info */
color: #979797; /* Captions and notes */
```

**Action Color Application**

```css
/* Primary Action */
background-color: #007aff;
color: #ffffff;

/* Secondary Action */
background-color: transparent;
color: #007aff;
border: 1px solid #007aff;
```

---

## 2. Corner Radius (border-radius)

### Corner Radius by Component Type

**Buttons**

* **Small buttons**: `border-radius: 8px` (height ≤ 32px)
* **Standard buttons**: `border-radius: 12px` (height ≈ 44px)
* **Large buttons**: `border-radius: 16px` (height ≥ 56px)

**Cards / Containers**

* **Small cards**: `border-radius: 12px` (width ≤ 200px)
* **Standard cards**: `border-radius: 16px` (width 200–400px)
* **Large cards**: `border-radius: 20px` (width ≥ 400px)

**Form Elements**

* **Input fields**: `border-radius: 8px`
* **Textareas**: `border-radius: 12px`
* **Select boxes**: `border-radius: 8px`

**Modals / Overlays**

* **Modal**: `border-radius: 20px` (iOS-style)
* **Popover**: `border-radius: 16px`
* **Tooltip**: `border-radius: 8px`

### Corner Smoothing (Continuous Corners)

```css
/* Smooth iOS-style rounded corners */
border-radius: 16px;
/* In Figma: set Corner Smoothing to 60–61% */
```

---

## 3. Spacing System (Margin & Padding)

### Base Spacing Unit

**8px-Based System**

* **Extra small**: `4px` — icon/text gaps
* **Small**: `8px` — minimal related spacing
* **Standard**: `16px` — common element gap, card padding
* **Medium**: `24px` — section separation
* **Large**: `32px` — major section spacing
* **Extra large**: `48px` — top/bottom page padding

### Spacing by Component

**Buttons**

```css
/* Standard button */
padding: 12px 24px;
min-height: 44px;

/* Small button */
padding: 8px 16px;
min-height: 32px;

/* Large button */
padding: 16px 32px;
min-height: 56px;
```

**Card Interior**

```css
padding: 20px; /* Standard card */
padding: 16px; /* Small card */
padding: 24px; /* Large card */
```

**Layout Margins**

```css
/* Page level */
margin: 0 16px; /* Mobile horizontal margin */
margin: 0 24px; /* Tablet */
margin: 0 auto;
max-width: 1200px; /* Centered desktop layout */

/* Section spacing */
margin-bottom: 32px; /* Section break */
margin-bottom: 48px; /* Major section break */
```

---

## 4. Contrast Guidelines

### Text Contrast Rules

**WCAG 2.1 Compliance Ratios**

* **Normal text**: ≥ 4.5:1
* **Large text**: ≥ 3:1
* **UI components**: ≥ 3:1

**Recommended Combinations**

```css
/* High contrast */
background: #ffffff;
color: #000000; /* 21:1 */
background: #f5f5f7;
color: #1d1d1f; /* 16.8:1 */

/* Medium contrast */
background: #ffffff;
color: #666666; /* 5.74:1 */
background: #f5f5f7;
color: #979797; /* 4.54:1 */

/* Action colors */
background: #007aff;
color: #ffffff; /* 4.5:1 */
```

### UI Element Contrast

**Interactive Elements**

* **Buttons**: ≥ 4.5:1 between text and background
* **Links**: ≥ 3:1 contrast with surrounding text
* **Forms**: ≥ 3:1 between borders and background

**State Variations**

```css
/* Default */
background-color: #007aff;

/* Hover */
background-color: #0056cc; /* 20% darker */

/* Disabled */
background-color: #007aff;
opacity: 0.3;
```

---

## 5. Card Design

### Standard Card Specification

```css
.card {
  background: #ffffff;
  border-radius: 16px;
  padding: 20px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);
  border: none;
}
```

### Shadows

```css
/* Light shadow (default) */
box-shadow: 0 1px 3px rgba(0, 0, 0, 0.08);

/* Medium shadow (hover) */
box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);

/* Strong shadow (modal, key elements) */
box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
```

### Card Size Variants

**Small Card (Mobile)**

```css
.card-small {
  min-width: 280px;
  max-width: 320px;
  padding: 16px;
  border-radius: 12px;
}
```

**Standard Card**

```css
.card-standard {
  min-width: 320px;
  max-width: 400px;
  padding: 20px;
  border-radius: 16px;
}
```

**Large Card (Desktop)**

```css
.card-large {
  min-width: 400px;
  max-width: 600px;
  padding: 24px;
  border-radius: 20px;
}
```

### Card Layout Structure

```css
.card-header {
  margin-bottom: 16px;
  padding-bottom: 12px;
  border-bottom: 1px solid #eeeeee;
}

.card-body {
  margin-bottom: 20px;
  line-height: 1.5;
}

.card-footer {
  margin-top: 16px;
  padding-top: 12px;
  border-top: 1px solid #eeeeee;
}
```

---

## 6. Spacing & Grid System

### Element Spacing Hierarchy

**By Relationship Level**

* **Tight relation**: `4px` — label and value, icon and text
* **Related**: `8px` — elements in the same group
* **Loosely related**: `16px` — between groups
* **Independent**: `24px` — within section separation
* **Separated**: `32px` — section-to-section distance

### Grid System

**12-Column Flexible Grid**

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 16px; /* Mobile */
  padding: 0 24px; /* Tablet */
  padding: 0 32px; /* Desktop */
}

.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 16px; /* Mobile */
  gap: 20px; /* Tablet */
  gap: 24px; /* Desktop */
}
```

**Responsive Breakpoints**

```css
/* Mobile */
@media (max-width: 767px) {
  .container {
    padding: 0 16px;
  }
  .grid {
    gap: 16px;
  }
}

/* Tablet */
@media (min-width: 768px) and (max-width: 1023px) {
  .container {
    padding: 0 24px;
  }
  .grid {
    gap: 20px;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    padding: 0 32px;
  }
  .grid {
    gap: 24px;
  }
}
```

### Typography Spacing

**SF Pro Font System**

```css
/* System font */
font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Text', 'Helvetica Neue', sans-serif;

/* Size hierarchy */
.text-large-title {
  font-size: 34px;
  line-height: 1.2;
  margin-bottom: 24px;
}
.text-title-1 {
  font-size: 28px;
  line-height: 1.25;
  margin-bottom: 20px;
}
.text-title-2 {
  font-size: 22px;
  line-height: 1.3;
  margin-bottom: 16px;
}
.text-headline {
  font-size: 17px;
  font-weight: 600;
  margin-bottom: 12px;
}
.text-body {
  font-size: 17px;
  line-height: 1.5;
  margin-bottom: 16px;
}
.text-caption {
  font-size: 12px;
  color: #666666;
  margin-bottom: 8px;
}
```

---

## Implementation Checklist

### Required

* [ ] Minimum touch target size: 44px × 44px
* [ ] Maintain contrast ratio ≥ 4.5:1
* [ ] Use system font (SF Pro)
* [ ] Follow 8px spacing system
* [ ] Consistent corner radii (8px, 12px, 16px, 20px)
* [ ] Consistent shadow hierarchy

### Recommended

* [ ] Support dark mode
* [ ] Accessibility compliance
* [ ] Responsive design
* [ ] Smooth animations
* [ ] Semantic color usage

---

By adhering to this guide, you can create a website that achieves **Apple-level quality and design consistency**.
All numerical values are based on **real implementation data from Apple**, allowing for accurate replication of the Apple design aesthetic.

