---
name: motion-design
description: UI animation principles — Disney's 12 principles applied to interfaces, Material Design motion system, easing curves, duration guidelines, and accessibility (prefers-reduced-motion). Use when specifying animations, transitions, or micro-interactions.
---

# Motion Design for UI

## When to Use This Skill

**Use when you need:**
- Animation specification for a component or flow
- Easing curve and duration decisions
- Transition design between states or pages
- Accessible motion implementation
- Micro-interaction design

---

## Disney's 12 Principles Applied to UI

| Principle | UI Application | Example |
|-----------|---------------|---------|
| **Squash & Stretch** | Buttons compress on press, modals stretch on appear | Button press feedback |
| **Anticipation** | Hover states preview what happens next | Pull-to-refresh indicator building |
| **Staging** | Direct attention with motion | Dim background behind modal |
| **Straight Ahead vs. Pose to Pose** | Define keyframes, let system interpolate | CSS transition keyframes |
| **Follow Through & Overlapping** | Content arrives slightly after container | Staggered list animations |
| **Slow In & Slow Out** | Never use linear motion. Objects ease naturally. | Every CSS transition |
| **Arcs** | Elements move along curves, not straight lines | Floating action button expansion |
| **Secondary Action** | Button ripple (primary) + icon shift (secondary) | Material ripple effect |
| **Timing** | Milliseconds define personality: fast=snappy, slow=elegant | Duration system |
| **Exaggeration** | Subtle overscale on success | Bounce on notification badge |
| **Solid Drawing** | Consistent 3D perspective in shadows, tilts | Card hover elevation |
| **Appeal** | Motion should feel satisfying and appropriate | Delightful micro-interactions |

---

## Duration Guidelines

| Change Type | Duration | Use For |
|-------------|----------|---------|
| Micro-interaction | 100-200ms | Button press, toggle, checkbox |
| Small transition | 200-300ms | Fade in, color change, tooltip |
| Medium transition | 300-500ms | Panel slide, modal open, card expand |
| Large transition | 500-700ms | Page transition, complex layout change |
| Stagger delay | 30-50ms per item | List item entrance |

**Rule of thumb:** Most UI animations should be 200-500ms. Under 100ms feels instant (not perceived as motion). Over 700ms feels sluggish.

---

## Easing Curves (Material Design 3)

| Curve | CSS | Use For |
|-------|-----|---------|
| **Standard (ease-in-out)** | `cubic-bezier(0.2, 0, 0, 1)` | Elements moving between on-screen positions |
| **Deceleration (ease-out)** | `cubic-bezier(0, 0, 0, 1)` | Elements entering the screen |
| **Acceleration (ease-in)** | `cubic-bezier(0.3, 0, 1, 1)` | Elements leaving the screen |
| **Sharp** | `cubic-bezier(0.4, 0, 0.2, 1)` | Elements that may return (temporary exits) |

**Never use `linear`** for UI motion. Real objects don't move at constant velocity.

---

## Accessible Motion

### prefers-reduced-motion

Users with vestibular disorders experience dizziness, nausea, and headaches from motion. Respect their preference:

```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Vestibular Triggers to Avoid
- Large-scale zooming or spinning
- Parallax scrolling
- Auto-playing animations without pause controls
- Rapid flashing (WCAG 2.3.1: no more than 3 flashes/second)

### Safe Alternatives for Reduced Motion
- Fade-in / opacity changes
- Color transitions
- Small scale changes (1.0 → 1.05, not 0 → 1)
- Instant state changes (no transition)

---

## When NOT to Animate

- User has `prefers-reduced-motion` enabled
- Animation adds no functional value (purely decorative)
- It slows down task completion
- It distracts from primary content
- The element appears frequently (repetitive animation is annoying)

---

## Related Skills
- `interaction-patterns` — State transitions that motion supports
- `accessibility-wcag` — WCAG motion requirements (2.2.2, 2.3.1, 2.3.3)
- `design-systems` — Motion tokens as part of the token system
