---
name: design-systems
description: Design systems architecture — tokens, components, documentation, governance. Use when building or scaling a design system, defining component APIs, establishing token architecture, or creating contribution guidelines.
---

# Design Systems

## When to Use This Skill

**Auto-loaded by agents:**
- design-systems-lead — For all design system work

**Use when you need:**
- Token architecture (color, typography, spacing, elevation)
- Component specification and API design
- Documentation standards
- Design system governance and contribution models

---

## Token Architecture

### Token Layers
1. **Global tokens** — Raw values (`blue-500: #3B82F6`)
2. **Semantic tokens** — Intent-based aliases (`color-primary: blue-500`)
3. **Component tokens** — Scoped to components (`button-bg: color-primary`)

### Core Token Categories
- **Color**: Brand, semantic (success/warning/error/info), neutral, surface, text
- **Typography**: Font family, size scale, weight, line height, letter spacing
- **Spacing**: Base unit (typically 4px or 8px), scale (0, 1, 2, 3, 4, 6, 8, 12, 16...)
- **Elevation**: Shadow levels (0-5), z-index scale
- **Border**: Radius scale, width, style
- **Motion**: Duration (fast/normal/slow), easing curves
- **Breakpoints**: Viewport widths for responsive design

## Component Specification Template

For every component, document:
1. **Purpose** — What problem does this solve?
2. **Anatomy** — Named parts and their relationships
3. **Variants** — Types/styles (primary, secondary, ghost, destructive)
4. **Sizes** — Scale options (sm, md, lg)
5. **States** — Default, hover, active, focus, disabled, loading, error
6. **Props/API** — Configurable properties with types and defaults
7. **Accessibility** — ARIA roles, keyboard behavior, screen reader announcements
8. **Usage guidelines** — When to use, when NOT to use, do/don't examples
9. **Content guidelines** — Label length, tone, capitalization

## Governance

### Contribution Model
- **Centralized**: Core team owns all components. Consistent but slow.
- **Federated**: Product teams contribute, core team reviews. Scalable but needs governance.
- **Hybrid**: Core team owns primitives and patterns, product teams extend.

### Component Lifecycle
1. **Proposal** — Problem statement, use cases, existing alternatives
2. **Design** — Spec, variants, states, accessibility
3. **Build** — Implementation with tests
4. **Document** — Usage guidelines, examples, API reference
5. **Release** — Versioned, changelog, migration guide
6. **Maintain** — Bug fixes, enhancements, deprecation

---

## Related Skills
- `accessibility-wcag` — Accessibility requirements per component
- `interaction-patterns` — Pattern selection for component behavior
