# UI/UX Design Specification

## Minimalist Full-Stack Developer Portfolio

This document outlines the visual system, UI philosophy, layout structure, typography definitions, color tokens, and motion guidelines for the minimalist portfolio web application.

---

## 1. Visual Vibe & Design Philosophy

The aesthetic design targets a **high-end, editorial, ultra-minimalist developer portfolio**. It relies on intentional negative space, bold layout structures, refined typography hierarchy, and smooth micro-interactions to create a premium user experience.

### Key Tenets
1. **Monochromatic Baseline with Muted Accents**: Leverage deep grays and pristine whites rather than high-contrast defaults. Use subtle accent overlays only to highlight high-value actions.
2. **Glassmorphism & Faint Grids**: Incorporate thin borders, high-blur backdrops, and responsive grid layouts instead of heavy solid backgrounds.
3. **Motion is Information**: Animations must be elegant, micro-level gestures (e.g., hover expansions, gentle fade-ins) rather than overwhelming, complex structures.
4. **Perfect Theme Transition**: Transition between light and dark modes with a CSS variable-based transition duration, leaving no un-styled state (FOUC).

---

## 2. Color System & Design Tokens

Theme colors are managed completely via CSS Variables mapped directly inside a Tailwind CSS configuration.

### A. Dark Mode Tokens (Default)
* **Background Primary**: `#09090b` (Zinc-950) — A deep, rich charcoal black.
* **Background Secondary**: `#18181b` (Zinc-900) — Elevated surface for cards/panels.
* **Border Color**: `rgba(255, 255, 255, 0.08)` — Faint, clean divider lines.
* **Text High-Contrast**: `#f4f4f5` (Zinc-100) — Maximum legibility for headings.
* **Text Muted**: `#a1a1aa` (Zinc-400) — Soft gray for body copy, dates, and labels.
* **Accent Active**: `#d4d4d8` (Zinc-300) / Custom muted primary like Indigo or Amber (`#6366f1` / `#f59e0b`) in micro doses.

### B. Light Mode Tokens
* **Background Primary**: `#fafafa` (Zinc-50) — Pristine paper white.
* **Background Secondary**: `#f4f4f5` (Zinc-100) — Soft contrast panels.
* **Border Color**: `rgba(0, 0, 0, 0.06)` — Subtle gray dividers.
* **Text High-Contrast**: `#09090b` (Zinc-950) — Editorial-style text color.
* **Text Muted**: `#52525b` (Zinc-600) — Highly legible body text.
* **Accent Active**: `#27272a` (Zinc-800) — Polished dark accents.

### C. Core CSS Variable Schema (`index.css`)
```css
@theme {
  --color-background-primary: var(--bg-primary);
  --color-background-secondary: var(--bg-secondary);
  --color-border-primary: var(--border-primary);
  --color-text-high: var(--text-high);
  --color-text-muted: var(--text-muted);
}

:root {
  --bg-primary: #fafafa;
  --bg-secondary: #f4f4f5;
  --border-primary: rgba(0, 0, 0, 0.06);
  --text-high: #09090b;
  --text-muted: #52525b;
}

[data-theme='dark'] {
  --bg-primary: #09090b;
  --bg-secondary: #18181b;
  --border-primary: rgba(255, 255, 255, 0.08);
  --text-high: #f4f4f5;
  --text-muted: #a1a1aa;
}

body {
  background-color: var(--color-background-primary);
  color: var(--color-text-high);
  transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease;
}
```

---

## 3. Typography Hierarchy

Typography is the absolute core of a minimalist design. Default web fonts are bypassed in favor of premium, clean, high-performance web typefaces:

| Element | Font Family | Weight | Case | Style / Purpose |
| :--- | :--- | :---: | :---: | :--- |
| **Hero / Main Headings** | Playfair Display / Outfit | Bold (700) | Sentence | Large, editorial, premium feel. |
| **Subheadings (H2, H3)** | Inter / System-Sans | Semi-Bold (600) | Sentence | Strict technical hierarchy. |
| **Body & Paragraphs** | Inter | Regular (400) | Sentence | High legibility, comfortable reading, wide line-height (`leading-relaxed`). |
| **Code & Technical Specs**| JetBrains Mono / Source Code | Regular / Medium | Monospace | Markdown code blocks, command lines, stack tags. |

---

## 4. UI Components Layout Specs

### A. Navigation & Header
* **Layout**: Fixed or floating thin-border bar (`backdrop-blur-md`) at the top of the viewport.
* **Interactive Elements**: Logo mark (minimal text or monogram), nav-links, and the dynamic theme toggle.
* **Hover State**: Navigation links display a subtle line sliding underneath or simple fading from text-muted to text-high.

### B. Project Cards
* **Visual Structure**: 
  - Monochromatic layout with a faint structural border.
  - Display project title, core stack (represented in pill badges), and primary description.
  - Dynamic scale-up (`scale-[1.01]`) or glowing border on mouse hover.
* **Hover Interaction Mockup**:
```
+------------------------------------------+
|  PROJECT TITLE                           |
|  --------------------------------------- |
|  Brief descriptive sentence highlighting  |
|  engineering impact and success.         |
|                                          |
|  [Next.js] [Supabase] [Tailwind CSS]     |
|                                          |
|  -> View Repository      -> Live App     |
+------------------------------------------+
```

### C. Technical Blog Post Index
* **Layout**: Chronological vertical list. Clean rows showing `Date`, `Title`, and `Reading Time` aligned inline with wide spacing.
* **Focus**: Remove card formats in the blog list to maintain a high-end editorial feel (similar to a premium newspaper or medium layout).

---

## 5. Micro-Animations & Transitions

We use **Framer Motion** for React transitions, ensuring animations remain lightweight and performant.

### Page Transitions
* Simple, fluid fade-and-slide up transitions when changing routes:
```typescript
export const pageTransitionVariants = {
  initial: { opacity: 0, y: 10 },
  animate: { opacity: 1, y: 0, transition: { duration: 0.4, ease: 'easeOut' } },
  exit: { opacity: 0, y: -10, transition: { duration: 0.3 } }
}
```

### Theme Toggler Animation
* Transitioning the theme switcher between `Sun` and `Moon` SVGs:
  - Rotates `180deg` on hover.
  - Scales down on click (`scale-90`) and expands smoothly on release (`scale-100`).

### Hover Magnet Effect
* Call-to-action buttons use a magnetic pull interaction: when the cursor is in close proximity to a primary CTA, the button shifts slightly towards the cursor using standard mouse-move tracking.
