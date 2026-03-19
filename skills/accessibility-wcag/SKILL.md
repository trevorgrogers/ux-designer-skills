---
name: accessibility-wcag
description: WCAG 2.1/2.2 guidelines, ARIA patterns, and inclusive design principles. Use when auditing accessibility, implementing ARIA, reviewing color contrast, or designing for screen readers, keyboard users, and cognitive accessibility.
---

# Accessibility & WCAG

Accessibility is not a compliance checkbox you handle at the end. It's a design quality bar. If your product isn't accessible, it's not finished. Full stop. Every accessibility failure is a user you're turning away. That's not just an ethical problem. It's a revenue problem. And it's a legal one too.

## When to Use This Skill

**Auto-loaded by agents:**
- accessibility-auditor - For full audits
- design-critic - For accessibility dimension in critiques

**Use when you need:**
- Accessibility audit of a design or implementation
- ARIA pattern for an interactive component
- Color contrast check
- Keyboard navigation design
- Inclusive design guidance

---

## WCAG 2.1 Quick Reference

### Level A (Minimum)
- All non-text content has text alternatives
- Captions for pre-recorded audio
- Content is meaningful without color alone
- Keyboard accessible (no keyboard traps)
- No content that flashes more than 3 times per second
- Pages have descriptive titles
- Focus order is logical
- Link purpose is clear from text

### Level AA (Target - Industry Standard)
- **Contrast**: 4.5:1 for normal text, 3:1 for large text (18px+ or 14px+ bold)
- **Resize**: Text scales to 200% without loss of content
- **Images of text**: Use real text, not images of text
- **Focus visible**: Keyboard focus indicator is visible
- **Consistent navigation**: Same components appear in same order
- **Error identification**: Errors are identified and described in text
- **Labels**: Form inputs have associated labels

### Level AAA (Aspirational)
- **Contrast**: 7:1 for normal text, 4.5:1 for large text
- **No timing**: No time limits on user actions
- **No interruptions**: User can postpone or suppress interruptions
- **Re-authentication**: No data loss on session timeout

---

## Common ARIA Patterns

| Component | Key ARIA | Keyboard |
|-----------|----------|----------|
| Modal/Dialog | `role="dialog"`, `aria-modal="true"`, `aria-labelledby` | Escape to close, trap focus |
| Tabs | `role="tablist/tab/tabpanel"`, `aria-selected` | Arrow keys between tabs |
| Menu | `role="menu/menuitem"`, `aria-expanded` | Arrow keys, Enter to select, Escape to close |
| Accordion | `aria-expanded`, `aria-controls` | Enter/Space to toggle |
| Toast/Alert | `role="alert"` or `role="status"` | Auto-announced by screen readers |
| Toggle | `role="switch"`, `aria-checked` | Space to toggle |

---

## Quick Checks

- [ ] Color contrast meets 4.5:1 (AA) for body text
- [ ] All images have alt text (or `alt=""` for decorative)
- [ ] All form inputs have visible labels
- [ ] Focus order follows visual order
- [ ] Interactive elements have visible focus styles
- [ ] Touch targets are at least 44x44px
- [ ] Content is readable at 200% zoom
- [ ] No information conveyed by color alone
- [ ] Error messages are specific and actionable
- [ ] Skip navigation link exists

### The One Thing

If you're only going to do one thing: test with a keyboard. Tab through your entire flow. If you can't complete the core task with only a keyboard, you've failed the most basic accessibility test. Fix that before you touch anything else.

---

## Related Skills
- `design-heuristics` - Overlaps with Nielsen #2, #6, #9
- `laws-of-ux` - Cognitive accessibility (Cognitive Load, Chunking, Working Memory)
