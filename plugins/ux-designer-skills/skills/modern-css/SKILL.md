---
name: modern-css
description: Modern CSS capabilities designers should know — container queries, :has(), view transitions, scroll-driven animations, subgrid, fluid typography. Use when designing responsive layouts, specifying component behavior, or bridging design-to-development communication.
---

# Modern CSS for Designers

## When to Use This Skill

**Use when you need:**
- Responsive design that goes beyond media queries
- Component-level responsiveness (container queries)
- Typography that scales fluidly
- Animation specification that maps to CSS
- Understanding what's possible natively (no JavaScript needed)

---

## Container Queries

Components adapt based on their container's size, not the viewport.

```css
.card-container { container-type: inline-size; }

@container (min-width: 400px) {
  .card { flex-direction: row; }
}
```

**Why designers care:** A card component in a sidebar behaves differently than the same card in main content — automatically. True component reusability.

---

## :has() Selector (Parent Selector)

Style a parent based on what it contains.

```css
.form-group:has(input:invalid) { border-color: red; }
.card:has(img) { grid-template-rows: auto 1fr; }
```

**Why designers care:** Conditional styling without JavaScript. Components self-adapt based on content.

---

## Fluid Typography

Smooth font scaling between min and max sizes:

```css
h1 { font-size: clamp(2rem, 5vw + 1rem, 4rem); }
```

**Rules:**
- Always combine vw with rem (pure vw doesn't respond to browser zoom — accessibility issue)
- Use consistent viewport calculations across elements for synchronized scaling
- Tools: [fluidtypography.com](https://fluidtypography.com), [clampgenerator.com](https://clampgenerator.com)

---

## CSS Grid Patterns

### Auto-responsive grid (no media queries):
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
```

### Subgrid
Child grids inherit parent grid tracks. Cards in a grid maintain aligned headers, content, and footers even when content lengths vary.

### Grid vs. Flexbox
- **Grid** = 2D layout (rows + columns). Use for page layout.
- **Flexbox** = 1D layout (row OR column). Use for component layout.

---

## View Transitions API

Native browser transitions between states or pages. Smooth page transitions, shared element transitions (thumbnail → full image), state changes — all handled natively.

---

## Scroll-Driven Animations

Animate based on scroll position rather than time.

**Use cases:** Reading progress bars, parallax, reveal-on-scroll, header transformations.

**Performance:** Tokopedia replaced JS scroll handlers with CSS: 80% less code, CPU dropped from 50% to 2% while scrolling.

---

## What Designers Should Specify

When handing off responsive behavior, specify:
1. **Container breakpoints** (not just viewport breakpoints)
2. **Fluid ranges** (min/max sizes for typography and spacing)
3. **Layout shifts** (what changes at each breakpoint — grid columns, stack direction)
4. **Animation triggers** (on scroll, on hover, on state change)
5. **Easing and duration** (map to the motion design token system)

---

## Related Skills
- `design-systems` — Token architecture that maps to CSS custom properties
- `motion-design` — Animation principles and easing curves
- `figma-at-scale` — Figma variables that map to CSS tokens
