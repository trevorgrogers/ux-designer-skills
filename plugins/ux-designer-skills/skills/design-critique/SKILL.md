---
name: design-critique
description: Structured design critique frameworks for giving and receiving design feedback. Use when reviewing designs, running critique sessions, or establishing feedback culture on design teams.
user-invocable: true
argument-hint: "[screenshot or description of design to critique]"
allowed-tools: Read, Glob, Grep, Write
---

# Design Critique Frameworks

## When to Use This Skill

**Use when you need:**
- A structured critique of a specific design
- Framework for running team critique sessions
- Feedback on a screenshot, mockup, or prototype
- Design review before development handoff

---

## The Critique Framework

### Step 1: Understand Intent
Before critiquing, clarify:
- Who is the user?
- What is their goal?
- What is the business objective?
- What constraints exist? (tech, time, brand)

### Step 2: Evaluate Across Dimensions

| Dimension | Questions |
|-----------|-----------|
| **Clarity** | Can users understand what to do? Is the hierarchy clear? |
| **Efficiency** | Can users accomplish their goal quickly? Are there unnecessary steps? |
| **Consistency** | Does it follow established patterns (system and platform)? |
| **Error handling** | What happens when things go wrong? Are errors preventable? |
| **Accessibility** | Can everyone use it? Color contrast, touch targets, screen reader support? |
| **Emotional response** | How does it feel? Does the aesthetic match the brand and audience? |
| **Edge cases** | Empty states, long text, error states, first-time use, power user paths? |

### Step 3: Structure Feedback
For each observation:
1. **Observation** — What you see (neutral, specific)
2. **Principle** — What UX law or heuristic applies
3. **Impact** — Who is affected and how
4. **Suggestion** — Specific, actionable alternative
5. **Severity** — Critical / High / Medium / Low

### Step 4: Prioritize
- **Must fix** — Blocks user goals, accessibility violations, error-prone flows
- **Should fix** — Friction points, consistency issues, cognitive load
- **Could fix** — Polish, delight, minor optimizations

---

## Critique Etiquette (For Team Sessions)

- Critique the work, not the designer
- Start with what's working
- Ask questions before making statements
- Be specific — "the spacing feels tight between the label and input" not "this looks off"
- Suggest alternatives, don't just identify problems
- Differentiate between personal preference and usability issue

---

## Related Skills
- `design-heuristics` — Nielsen's 10 Heuristics (evaluation framework)
- `laws-of-ux` — Named principles for grounding feedback
