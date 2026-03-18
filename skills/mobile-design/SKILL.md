---
name: mobile-design
description: Mobile-specific design guidelines — iOS Human Interface Guidelines, Material Design 3, gesture navigation, haptic feedback, adaptive layouts, thumb zones. Use when designing mobile apps or evaluating mobile-specific patterns.
---

# Mobile Design

## When to Use This Skill

**Use when you need:**
- iOS or Android platform-specific guidance
- Gesture navigation patterns
- Touch target sizing
- Adaptive layout strategy
- Platform decision (native patterns vs. cross-platform)

---

## iOS Human Interface Guidelines (Key Points)

### Four Core Principles
1. **Clarity** — Clean, uncluttered layouts. Ample white space.
2. **Deference** — Interface guides without competing with content.
3. **Depth** — Layers, shadows, motion create hierarchy.
4. **Consistency** — Uniform design language. Predictable interactions.

### Key Specs
| Element | Spec |
|---------|------|
| Touch targets | Minimum 44x44 points |
| Navigation | Bottom tab bars, labeled back buttons |
| Safe areas | Respect notch, Dynamic Island, home indicator |
| Typography | SF Pro, Dynamic Type support required |
| Tab bar items | 3-5 items maximum |

### iOS 26 (2025): Liquid Glass
Most significant visual redesign since 2013. Translucent, rounded elements with optical glass properties. Elements adapt dynamically to light and content.

---

## Material Design 3 (Key Points)

### Core Systems
- **Color**: 5 key colors → 13-tone palettes. Dynamic Color from wallpaper (Material You).
- **Typography**: Role-based scale (display, headline, title, body, label).
- **Shape**: Component corner rounding system. Different shapes for emphasis levels.

### M3 Expressive (2025)
Backed by 46 research studies, 18,000+ participants. Users preferred Expressive designs AND found them more usable. More emotional range and brand expression.

### Key M3 Components
- Buttons: 4 emphasis levels (filled, tonal, outlined, text)
- Navigation: Bottom nav, nav rail, nav drawer (responsive)
- Cards: Elevated, filled, outlined variants

---

## Gesture Navigation

| Gesture | iOS | Android | Use For |
|---------|-----|---------|---------|
| Swipe from edge | Back navigation | Back navigation | Primary navigation |
| Pull down | Refresh, dismiss | Refresh | Content update |
| Long press | Context menu | Context menu | Secondary actions |
| Pinch | Zoom | Zoom | Media, maps |
| Swipe on item | Quick actions | Quick actions | Delete, archive, etc. |

---

## Haptic Feedback

| Type | When to Use |
|------|------------|
| Light impact | Toggle, selection change |
| Medium impact | Confirming an action |
| Heavy impact | Significant state change |
| Success | Task completion |
| Warning | Approaching limit |
| Error | Failed action |

Every interaction should have intentional, subtle tactile response.

---

## Thumb Zone

The bottom third of the screen is most accessible one-handed. Place primary actions there.

| Zone | Reachability | Place Here |
|------|-------------|------------|
| Bottom center | Easy | Primary CTA, bottom nav, FAB |
| Middle | Comfortable | Content, secondary actions |
| Top corners | Hard | Non-critical info, settings |

---

## Adaptive Layouts

Design for multiple device classes with a single codebase:
- **Phone** (compact): Single column, bottom nav, full-screen modals
- **Tablet** (medium): Two-pane layout, nav rail, inline modals
- **Foldable** (adaptive): Flex mode, table-top mode, split content

---

## Related Skills
- `interaction-patterns` — Navigation and overlay patterns
- `accessibility-wcag` — Touch targets, gestures, screen reader support
- `design-systems` — Responsive token architecture
