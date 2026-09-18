---
name: mobile-design
description: Mobile-specific design guidelines - iOS Human Interface Guidelines, Material Design 3, gesture navigation, haptic feedback, adaptive layouts, thumb zones. Use when designing mobile apps or evaluating mobile-specific patterns.
---

# Mobile Design

Every design decision is a mobile decision first. More than half your users are on phones. If you design for desktop and then "adapt" for mobile, you're designing for the minority and degrading the experience for the majority. Start with the phone. The desktop version is the adaptation.

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
1. **Clarity** - Clean, uncluttered layouts. Ample white space.
2. **Deference** - Interface guides without competing with content.
3. **Depth** - Layers, shadows, motion create hierarchy.
4. **Consistency** - Uniform design language. Predictable interactions.

### Key Specs
| Element | Spec |
|---------|------|
| Touch targets | Minimum 44x44 points |
| Navigation | Bottom tab bars, labeled back buttons |
| Safe areas | Respect notch, Dynamic Island, home indicator |
| Typography | SF Pro, Dynamic Type support required |
| Tab bar items | 3-5 items maximum |

### iOS 26 (2025) → iOS 27 (2026): Liquid Glass, Matured
iOS 26 introduced the most significant visual redesign since 2013: translucent, rounded elements with optical glass properties. iOS 27 pulled back the saturated AI-glow treatment that shipped alongside it — the direction moved toward less color, more fluid/liquid motion. If your AI surfaces are still matching iOS 26's original glow aesthetic, they already read as a generation behind. Don't chase the platform's current AI visual treatment directly — match its underlying material logic (translucency, adaptivity, restraint on color) and carry your own brand metaphor through it. See `agentic-product-design` for how to build a brand-native material language instead of following the platform's each cycle.

### Native AI Surfaces (Camera, Siri, On-Screen Context)
iOS 27 opened system-level AI context (camera-based recognition, Siri understanding on-screen content) to third-party apps. When your app can plug into a platform AI surface (e.g., a system-level visual search) rather than building a parallel custom one, prefer the platform surface for the parts users expect to feel "built into the phone," and reserve custom UI for the parts that are genuinely yours (recommendations, catalog-specific results). Don't rebuild what the platform already gives you for free just to keep full visual control — that's a maintenance cost with no user-facing upside.

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
- `interaction-patterns` - Navigation and overlay patterns
- `accessibility-wcag` - Touch targets, gestures, screen reader support
- `design-systems` - Responsive token architecture
- `agentic-product-design` - Designing the AI agent layer on top of these platform conventions
