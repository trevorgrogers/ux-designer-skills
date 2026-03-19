---
name: information-architecture
description: Information architecture that actually works. Navigation, taxonomy, hierarchy, search, and labeling, framed around the principle that if users can't find it, it doesn't exist.
---

# Information Architecture

## When to Use This Skill

**Auto-loaded by agents:**
- information-architect - For all IA work

**Use when you need:**
- Navigation structure design
- Content taxonomy and classification
- Site map or content hierarchy
- Search and filtering design
- Labeling and nomenclature decisions

---

## Why IA Matters

IA is the invisible work that determines whether your product feels intuitive or confusing. You'll never hear a user say "the information architecture is great." But you'll absolutely hear "I can't find anything on this site." That's an IA problem. And "I can't find it" is a conversion problem.

Bad IA is the root cause of more product failures than bad visual design. You can have the most beautiful interface in the world, but if users can't find what they're looking for, none of it matters.

---

## Core IA Concepts

### The Three Circles of IA
1. **Users** - Mental models, information-seeking behavior, vocabulary
2. **Content** - Volume, structure, existing organization, metadata
3. **Context** - Business goals, constraints, technology, culture

All three have to align. Most IA failures happen because the team designs for content and context but ignores users. They organize things in a way that makes sense to the business, not to the person trying to use the product.

### Organization Schemes
- **Exact**: Alphabetical, chronological, geographical. Objective and unambiguous. Good for reference content.
- **Ambiguous**: By topic, task, audience, metaphor. Subjective. Requires research to get right.
- **Hybrid**: Most real-world IAs combine multiple schemes. That's fine as long as each scheme is internally consistent.

### Navigation Systems
- **Global**: Persistent, site-wide (top nav, side nav)
- **Local**: Section-specific (sub-navigation, sidebar)
- **Contextual**: In-content links, related items, "see also"
- **Supplemental**: Sitemaps, indexes, guides, breadcrumbs

The best navigation is invisible. Users shouldn't be thinking about navigation at all. They should be thinking about their task, their content, their goal. If they're thinking about how to navigate, you've already failed.

### Labeling Principles

If your navigation uses words your team invented instead of words your users use, you're designing for yourselves. Card sort it. It takes 2 hours and saves 6 months of confusion.

- Use user language, not internal jargon. Always.
- Be specific. "Account Settings" not "Settings." "Order History" not "History."
- Be consistent. Don't use "help," "support," and "FAQ" interchangeably. Pick one.
- Test labels with card sorting and tree testing. This is cheap research with massive payoff.

---

## Flat vs. Deep

Flat is almost always better. Every click you add to find something is a user you lose. Research consistently shows that users prefer broader, shallower menus over narrow, deep ones.

But there's a breaking point. If you have 200+ items in a flat list, you don't need deeper hierarchy. You need faceted filtering. Let users narrow down by multiple dimensions simultaneously instead of making them drill through categories.

The exception: truly hierarchical content where the relationships between levels carry meaning (like a file system or org chart). But for most products, especially e-commerce and content sites, flat with good filtering wins.

---

## Search as Navigation

For any product with more than about 50 items of content, search isn't a nice-to-have. It's primary navigation for most users.

This is the thing teams consistently underinvest in. They spend months on navigation menus that 40% of users will ignore in favor of the search bar. Then they ship a search that returns garbage results and wonder why engagement is low.

If your search is broken, your IA is broken. Period.

**What good search looks like:**
- Tolerates typos and synonyms
- Returns results that match user intent, not just keywords
- Surfaces the most relevant results first (this is where editorial curation matters)
- Provides useful filtering and sorting on results
- Shows helpful empty states when there are no results, not just "no results found"

**Search is also a goldmine for IA research.** Your search logs tell you exactly what users are looking for and what words they use. If you're not reviewing search logs quarterly, you're ignoring your best source of IA insight.

---

## Research Methods for IA

| Method | What It Reveals | When to Use |
|--------|----------------|-------------|
| **Card sorting (open)** | How users naturally group content | Early, when discovering user mental models |
| **Card sorting (closed)** | Whether your categories make sense to users | After defining categories |
| **Tree testing** | Whether users can find content in your hierarchy | After defining structure, before building nav |
| **First-click testing** | Where users expect to find things | Evaluating nav labels and placement |

Most teams skip IA research because it feels slow. Then they spend 6 months building navigation that doesn't work and redesigning it. The research is faster.

An open card sort takes half a day to set up, a few days to collect responses, and an hour to analyze. A tree test is even faster. Compare that to the cost of rebuilding your navigation after launch because users can't find anything.

**A practical approach:**
1. Open card sort with 15-20 users to discover mental models
2. Build your proposed structure
3. Tree test with another 15-20 users to validate
4. Fix what doesn't work
5. Ship it

Total time: about 2 weeks. Total cost of skipping it: months of iteration post-launch and lost conversions in the meantime.

---

## Related Skills
- `laws-of-ux` - Cognitive principles (Chunking, Miller's Law, Mental Model)
- `interaction-patterns` - Navigation pattern selection
