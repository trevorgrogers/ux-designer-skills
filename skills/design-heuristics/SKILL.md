---
name: design-heuristics
description: Usability heuristics for catching real problems in interfaces, not generating busywork. Nielsen's 10 and Shneiderman's Golden Rules, reframed around business outcomes with practical severity scoring.
---

# Usability Heuristics

## When to Use This Skill

**Auto-loaded by agents:**
- design-critic - For structured design evaluations
- design-lead - For quality assessment

**Use when you need:**
- To find real usability problems in an existing design
- A mental checklist for reviewing critical flows before ship
- To prioritize what to fix when everything feels broken

---

## The Problem with Heuristic Evaluations

Nielsen's heuristics are from 1994. They still hold up. But the way most teams use them is broken.

The standard playbook says: get 5 evaluators, have each walk through independently, compile findings into a spreadsheet, then prioritize. What actually happens: you produce a 200-row spreadsheet that nobody reads, nothing gets fixed, and the team resents the process.

Here's what works instead: one experienced designer walks through the critical flows with these heuristics as a mental checklist. Write down the top 5 problems. Fix those. That's it. You'll catch 80% of the real issues in a fraction of the time.

Save the formal 5-evaluator method for when you're at serious scale and the stakes justify it.

---

## Nielsen's 10 Usability Heuristics

### 1. Visibility of System Status
The design keeps users informed about what's happening, with appropriate feedback within a reasonable time.

**Why it matters:** This isn't about loading spinners. It's about trust. Users who don't know what's happening leave. That's a conversion problem.

**Check for:** Loading indicators, progress bars, confirmation messages, state changes, active/selected states, sync status, save indicators.

### 2. Match Between System and the Real World
The design speaks the users' language, not your team's internal jargon.

**Why it matters:** Every label that confuses a user is a support ticket, a bounce, or a lost sale. If your checkout says "Fulfill Order" instead of "Place Order," you're losing revenue to vocabulary.

**Check for:** User-facing labels, error messages, navigation labels, onboarding copy, help text. Do they use the user's vocabulary?

### 3. User Control and Freedom
Users make mistakes. They need a clear way out without going through an extended process.

**Why it matters:** Users who feel trapped don't come back. Undo and easy exits reduce anxiety, which increases willingness to explore, which increases engagement and feature adoption.

**Check for:** Undo/redo, cancel buttons, back navigation, close/dismiss, exit flows, draft saving, "are you sure?" for destructive actions (but not for everything).

### 4. Consistency and Standards
Users shouldn't have to wonder whether different words, situations, or actions mean the same thing.

**Why it matters:** Inconsistency creates cognitive load. Cognitive load slows users down. Slower users convert less. Every inconsistency is a tiny tax on every interaction.

**Check for:** Consistent terminology, consistent interaction patterns, consistent visual treatment, platform conventions (iOS vs. Android vs. web).

### 5. Error Prevention
The best error message is the one that never shows up.

**Why it matters:** Every error is a moment where a user might quit. Preventing errors keeps users in flow, and users in flow complete tasks. Completed tasks are conversions.

**Check for:** Constraints (disabled buttons for invalid states), confirmations for destructive actions, smart defaults, input formatting, inline validation.

### 6. Recognition Rather Than Recall
Make elements, actions, and options visible. Don't make users memorize things across screens.

**Why it matters:** If users have to remember something from three screens ago, some percentage of them won't. They'll abandon. This is especially brutal in mobile where context switching is constant.

**Check for:** Visible options vs. hidden menus, breadcrumbs, recently used items, search history, contextual help, visible labels (not just icons).

### 7. Flexibility and Efficiency of Use
Let experienced users move fast. Shortcuts and customization for power users, simple defaults for everyone else.

**Why it matters:** Your power users are your highest-LTV users. If you slow them down to simplify for beginners, you'll lose the people who matter most to retention. Serve both.

**Check for:** Keyboard shortcuts, customization, saved preferences, recently used, favorites, bulk actions, power user features.

### 8. Aesthetic and Minimalist Design
Every extra element on the screen competes with the things that actually matter.

**Why it matters:** Visual noise kills clarity. Clarity drives action. If your conversion page has 15 competing elements, users don't know where to look, and they leave. This is where editorial thinking matters. Curate, don't accumulate.

**Check for:** Visual noise, decorative elements competing with content, information density, whitespace usage, progressive disclosure.

### 9. Help Users Recognize, Diagnose, and Recover from Errors
Error messages in plain language. Specific problem. Clear solution.

**Why it matters:** A user who hits an error and can recover stays. A user who hits "Error 403" leaves and doesn't come back. Good error recovery is a retention mechanism.

**Check for:** Error message clarity, actionable recovery paths, specific vs. generic errors, error placement (inline vs. toast vs. modal).

### 10. Help and Documentation
The system ideally doesn't need explanation. But when it does, help should be easy to find and focused on the user's task.

**Why it matters:** Users who can't figure out your product don't file complaints. They just leave. Good contextual help is an activation tool, especially for complex products.

**Check for:** Contextual help, tooltips, onboarding flows, documentation accessibility, searchable help, empty state guidance.

---

## Severity Scoring

| Severity | Description | Priority |
|----------|-------------|----------|
| 0 | Not a usability problem at all | - |
| 1 | Cosmetic problem, fix if time permits | Low |
| 2 | Minor usability problem, fix is low priority | Medium |
| 3 | Major usability problem, important to fix, high priority | High |
| 4 | Usability catastrophe, must fix before release | Critical |

**If you have more than 3 severity-4 issues, stop building new features and fix what's broken.** Shipping new features on top of a broken foundation just means more users hit more problems. You're scaling damage.

---

## Shneiderman's 8 Golden Rules

These overlap heavily with Nielsen's heuristics. Here's where they actually add something different:

1. **Strive for consistency** - Same as Nielsen #4. Nothing new here.
2. **Seek universal usability** - Nielsen doesn't emphasize this enough. Design for novice AND expert. Design for diverse abilities. This is where accessibility lives.
3. **Offer informative feedback** - Same as Nielsen #1. Every action should get a response.
4. **Design dialogs to yield closure** - This is the one Nielsen misses. Flows should have a clear beginning, middle, and end. Users need to feel "done." Without closure, users wonder if they actually completed the task. That uncertainty kills confidence.
5. **Prevent errors** - Same as Nielsen #5.
6. **Permit easy reversal of actions** - Same as Nielsen #3.
7. **Keep users in control** - Same as Nielsen #3 and #7 combined.
8. **Reduce short-term memory load** - Same as Nielsen #6.

The real additions from Shneiderman: universal usability (#2) and dialog closure (#4). Everything else you're already covering with Nielsen's list.

---

## How to Actually Use These

**For most teams (under 50 people, shipping fast):**
1. Pick your 3 most critical user flows (signup, core action, checkout/conversion)
2. One experienced designer walks through each flow with these heuristics as a mental checklist
3. Write down every issue you find with a severity score
4. Sort by severity, then fix the top 5
5. Repeat quarterly or after any major redesign

**For teams at scale (dedicated UX research function):**
1. 3-5 evaluators walk through independently
2. Compile and de-duplicate findings
3. Have the team vote on severity to calibrate
4. Feed severity 3-4 issues directly into the sprint backlog
5. Track fix rates over time

The goal is to find and fix problems, not to produce a deliverable. If your heuristic evaluation produces a beautiful spreadsheet that nobody acts on, you wasted everyone's time.

---

## Related Skills
- `laws-of-ux` - Psychological principles underlying these heuristics
- `accessibility-wcag` - WCAG guidelines (overlaps with heuristic #2, #6, #9)
