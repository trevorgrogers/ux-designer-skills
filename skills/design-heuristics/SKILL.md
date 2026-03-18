---
name: design-heuristics
description: Nielsen's 10 Usability Heuristics and Shneiderman's 8 Golden Rules for interface design evaluation. Use when conducting heuristic evaluations, reviewing designs, or establishing design quality standards.
---

# Usability Heuristics

## When to Use This Skill

**Auto-loaded by agents:**
- design-critic — For structured design evaluations
- design-lead — For quality assessment

**Use when you need:**
- A structured framework to evaluate an existing design
- Checklist for design review before handoff
- Training or onboarding designers on evaluation criteria

---

## Nielsen's 10 Usability Heuristics

### 1. Visibility of System Status
The design should always keep users informed about what is going on, through appropriate feedback within a reasonable amount of time.

**Check for:** Loading indicators, progress bars, confirmation messages, state changes, active/selected states, sync status, save indicators.

### 2. Match Between System and the Real World
The design should speak the users' language. Use words, phrases, and concepts familiar to the user, rather than internal jargon.

**Check for:** User-facing labels, error messages, navigation labels, onboarding copy, help text. Do they use the user's vocabulary?

### 3. User Control and Freedom
Users often perform actions by mistake. They need a clearly marked "emergency exit" to leave the unwanted action without having to go through an extended process.

**Check for:** Undo/redo, cancel buttons, back navigation, close/dismiss, exit flows, draft saving, "are you sure?" for destructive actions (but not for everything).

### 4. Consistency and Standards
Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform and industry conventions.

**Check for:** Consistent terminology, consistent interaction patterns, consistent visual treatment, platform conventions (iOS vs. Android vs. web).

### 5. Error Prevention
Good error messages are important, but the best designs prevent problems from occurring in the first place.

**Check for:** Constraints (disabled buttons for invalid states), confirmations for destructive actions, smart defaults, input formatting, inline validation.

### 6. Recognition Rather Than Recall
Minimize the user's memory load by making elements, actions, and options visible. The user should not have to remember information from one screen to another.

**Check for:** Visible options vs. hidden menus, breadcrumbs, recently used items, search history, contextual help, visible labels (not just icons).

### 7. Flexibility and Efficiency of Use
Shortcuts — hidden from novice users — can speed up the interaction for the expert user. Allow users to tailor frequent actions.

**Check for:** Keyboard shortcuts, customization, saved preferences, recently used, favorites, bulk actions, power user features.

### 8. Aesthetic and Minimalist Design
Interfaces should not contain information that is irrelevant or rarely needed. Every extra unit of information competes with relevant information and diminishes their relative visibility.

**Check for:** Visual noise, decorative elements that compete with content, information density, whitespace usage, progressive disclosure.

### 9. Help Users Recognize, Diagnose, and Recover from Errors
Error messages should be expressed in plain language (not error codes), precisely indicate the problem, and constructively suggest a solution.

**Check for:** Error message clarity, actionable recovery paths, specific vs. generic errors, error placement (inline vs. toast vs. modal).

### 10. Help and Documentation
It's best if the system doesn't need additional explanation. But it may be necessary to provide documentation to help users understand how to complete their tasks.

**Check for:** Contextual help, tooltips, onboarding flows, documentation accessibility, searchable help, empty state guidance.

---

## Heuristic Evaluation Scoring

| Severity | Description | Priority |
|----------|-------------|----------|
| 0 | Not a usability problem at all | — |
| 1 | Cosmetic problem — fix if time permits | Low |
| 2 | Minor usability problem — fix is low priority | Medium |
| 3 | Major usability problem — important to fix, high priority | High |
| 4 | Usability catastrophe — must fix before release | Critical |

---

## Shneiderman's 8 Golden Rules

1. **Strive for consistency** — Consistent sequences of actions, terminology, prompts, layouts
2. **Seek universal usability** — Cater to novice and expert users, diverse abilities
3. **Offer informative feedback** — Every action should have system feedback
4. **Design dialogs to yield closure** — Sequences should have beginning, middle, end
5. **Prevent errors** — Design to make errors impossible; offer simple recovery
6. **Permit easy reversal of actions** — Reduce anxiety by allowing undo
7. **Keep users in control** — Users should feel they control the system, not vice versa
8. **Reduce short-term memory load** — Keep displays simple, reduce multi-page frequency

---

## Related Skills
- `laws-of-ux` — Psychological principles underlying these heuristics
- `accessibility-wcag` — WCAG guidelines (overlaps with heuristic #2, #6, #9)
