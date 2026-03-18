---
name: interaction-patterns
description: Common interaction patterns and when to use them — modals, drawers, progressive disclosure, inline editing, navigation patterns, mobile gestures, and form design. Use when choosing between interaction approaches or designing component behavior.
---

# Interaction Patterns

## When to Use This Skill

**Auto-loaded by agents:**
- interaction-designer — For pattern selection
- design-lead — For interaction architecture decisions

**Use when you need:**
- Choosing between competing patterns (modal vs. drawer vs. inline)
- Designing navigation structure
- Form design decisions
- Mobile interaction patterns
- State management (loading, empty, error)

---

## Overlay Patterns

| Pattern | Use When | Avoid When |
|---------|----------|------------|
| **Modal** | Focused task, confirmation, blocking decision | Simple info, frequent action, long content |
| **Drawer/Panel** | Supplementary content, filters, detail views | Primary content, critical actions |
| **Popover** | Contextual info, quick actions, tooltips | Complex forms, lots of content |
| **Toast/Snackbar** | Non-critical feedback, status updates | Errors requiring action, important info |
| **Bottom Sheet (mobile)** | Actions, filters, short forms on mobile | Desktop, very long content |

## Disclosure Patterns

| Pattern | Use When | Avoid When |
|---------|----------|------------|
| **Progressive disclosure** | Complex features, optional settings | Critical info, primary actions |
| **Accordion** | FAQ, settings categories, collapsible sections | Primary content, few items |
| **Tabs** | Parallel content categories, same-level info | Sequential content, too many tabs (>5) |
| **Stepper/Wizard** | Multi-step processes, complex forms | Simple tasks, non-linear processes |

## Input Patterns

| Pattern | Use When | Avoid When |
|---------|----------|------------|
| **Inline editing** | Quick edits, data tables, settings | Complex validation, multi-field changes |
| **Form page** | Multiple related fields, complex validation | Single-field changes |
| **Auto-save** | Content creation, preferences | Financial transactions, irreversible actions |
| **Optimistic UI** | Low-risk actions, social interactions | Payments, data deletion |

## Navigation Patterns

| Pattern | Use When | Avoid When |
|---------|----------|------------|
| **Top nav** | Desktop, <7 items, global navigation | Mobile (use bottom nav), deep hierarchy |
| **Side nav** | Dashboard apps, many sections, deep hierarchy | Simple sites, mobile |
| **Bottom nav (mobile)** | 3-5 primary destinations, mobile apps | Desktop, >5 items |
| **Tab bar** | Content categories at same level | Hierarchical navigation |
| **Breadcrumbs** | Deep hierarchy, e-commerce, content sites | Flat site structure |
| **Command palette** | Power users, many actions, keyboard-first | Consumer apps, novice users |

## State Design Checklist

Every interactive component should define:
- [ ] **Default** — Initial state
- [ ] **Hover** — Mouse over (desktop)
- [ ] **Active/Pressed** — During interaction
- [ ] **Focus** — Keyboard focus (visible outline)
- [ ] **Disabled** — Cannot interact
- [ ] **Loading** — Awaiting response
- [ ] **Empty** — No content yet
- [ ] **Error** — Something went wrong
- [ ] **Success** — Action completed
- [ ] **Partial** — Partially complete (multi-select, progress)

---

## Related Skills
- `laws-of-ux` — Principles behind pattern choices
- `design-heuristics` — Evaluation framework
- `accessibility-wcag` — Keyboard and screen reader requirements for each pattern
