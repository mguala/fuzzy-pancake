# Design System: D&D Player Character Companion

## 1. Overview
The **D&D Player Character Companion Design System** provides a consistent, immersive, and high-performance visual framework tailored for tabletop role-playing game (TTRPG) enthusiasts. It bridges functional web components with an evocative fantasy aesthetic.

---

## 2. Core Principles
* **Immersive Fantasy Atmosphere**: Rich dark surfaces, gold/amber accents, and crisp parchment-inspired contrast.
* **TTRPG Utility First**: Rapid stat readability, clear dice roll indicators, and low cognitive load during live gameplay.
* **Responsive & Mobile-Ready**: Seamless adaptation from desktop monitors to mobile phones at the gaming table.
* **Component Modularity**: Reusable UI elements built on CSS custom properties and semantic structure.

---

## 3. Design Tokens

### Color Palette
```css
:root {
  /* Brand & Surfaces */
  --bg-primary: #121418;
  --bg-surface: #1e222a;
  --bg-surface-elevated: #282d37;

  /* Primary Accent: Dragon Gold */
  --color-primary: #d4af37;
  --color-primary-hover: #f1c40f;
  --color-primary-muted: rgba(212, 175, 55, 0.15);

  /* Secondary Accent: Arcane Crimson */
  --color-secondary: #9b2c2c;
  --color-secondary-hover: #c53030;

  /* Typography Colors */
  --text-primary: #f0f4f8;
  --text-secondary: #a0aec0;
  --text-muted: #718096;

  /* Utility & State */
  --color-success: #38a169;
  --color-warning: #dd6b20;
  --color-danger: #e53e3e;
  --border-color: #363c4a;
  --border-accent: #d4af37;
}
```

### Typography
* **Primary Font**: `Cinzel`, `Georgia`, serif (Headings & Character Titles)
* **Body Font**: `Inter`, `system-ui`, sans-serif (Interface text, inputs, stats)
* **Monospace Font**: `Fira Code`, `monospace` (Dice roll results, math logs)

| Scale | Size | Line Height | Usage |
| :--- | :--- | :--- | :--- |
| `display-1` | 2.5rem (40px) | 1.2 | Hero Headers |
| `heading-1` | 2.0rem (32px) | 1.25 | Page Titles |
| `heading-2` | 1.5rem (24px) | 1.3 | Section Headers |
| `heading-3` | 1.25rem (20px) | 1.4 | Card Titles |
| `body-base` | 1.0rem (16px) | 1.5 | Standard Body / Form Labels |
| `stat-number` | 1.75rem (28px) | 1.0 | Modifier Badges & Stat Scores |

### Spacing & Grid System
Based on an 8px spatial grid:
* `space-xs`: 4px
* `space-sm`: 8px
* `space-md`: 16px
* `space-lg`: 24px
* `space-xl`: 32px
* `space-2xl`: 48px

---

## 4. Components Layout & Specs

### Stat Block Card
Displays character attributes (STR, DEX, CON, INT, WIS, CHA) with clear numerical hierarchy:
* Container: Surface background, 1px solid border (`--border-color`), 8px rounded corners.
* Title Label: Small caps, muted text (`--text-secondary`).
* Attribute Value: Bold prominent text (`--text-primary`).
* Modifier Badge: Circle container with primary accent gold border (`--border-accent`), displaying calculated modifier (e.g., `+3`).

### Action Buttons
* **Primary Button**: Background `--color-primary`, text `#121418`, bold, subtle glow shadow on hover.
* **Secondary Button**: Transparent background, border 1px solid `--color-primary`, text `--color-primary`.
* **Danger/Delete Button**: Background `--color-secondary`, text white.

### Form Inputs
* Background `--bg-surface-elevated`, text `--text-primary`, border `--border-color`.
* Focus State: Border color `--color-primary`, subtle gold box shadow.

---

## 5. Accessibility Guidelines
* Minimum contrast ratio of 4.5:1 for body text against dark backgrounds.
* Explicit focus states for all interactive controls (keyboard navigation).
* Semantic HTML5 elements (`<main>`, `<nav>`, `<section>`, `<article>`).
