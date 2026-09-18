---
name: agentic-product-design
description: Designing AI agent experiences - proactive vs. reactive agent design, material and metaphor language for AI presence, omnipresent agent navigation, and platform-convention tension. Use when designing a conversational agent, an "AI assistant" surface, or any product where AI needs a visual and behavioral identity.
---

# Agentic Product Design

An AI agent is not a feature you bolt onto a product. It's a relationship you're asking the user to enter into. Most teams design the chat window and stop there. The actual design problem is bigger: what does the agent look like when it's thinking, where does it live when you're not talking to it, and does it earn the right to interrupt you. Get those wrong and you've built a search bar with extra steps.

## When to Use This Skill

**Use when you need:**
- A visual/material language for "the AI is doing something" (thinking states, loading, generation)
- To decide where a persistent agent lives across a multi-surface product
- To evaluate whether a feature should be reactive (user asks) or proactive (agent surfaces)
- To audit whether "AI" signaling has become noise instead of signal

---

## Proactive vs. Reactive Is the Real Product Decision

A purely reactive agent only captures users who already have high, specific intent — and that's a small, expensive slice of the market. If someone already knows exactly what they want, they have no reason to route through your agent instead of going straight to the source. A reactive-only AI product is competing for leftover demand.

The agent has to be proactive to matter: surfacing things before being asked, noticing context, initiating. That's not a chatbot behavior, it's a stylist/concierge behavior — the value isn't answering questions, it's the same thing a good advisor does in real life: *"I found this, I think you'd like it,"* not *"waiting for you to ask."*

**Design implication:** if every agent-touched surface in your product only responds to explicit user input, you've built a search feature, not an agent. Budget real design time for the proactive surfaces — nudges, notices, "I noticed X" moments — not just the conversation UI.

| Reactive design | Proactive design |
|---|---|
| Chat box waiting for input | Agent surfaces something unprompted, with a clear reason why |
| Wins only high-intent users who already know what they want | Wins the much larger population still forming intent |
| Feels like search | Feels like a relationship |
| Success = fast, correct answers | Success = timing, relevance, restraint (don't become spam) |

---

## Material and Metaphor: Give the Agent One Consistent Language

"The AI is thinking" needs a visual language, and that language needs to come from your brand, not from copying whatever the platform vendor (Apple, Google) shipped last cycle. Chasing a platform's current AI-glow aesthetic guarantees you look dated the moment the platform redesigns it — and it teaches users your product *is* the platform's feature, not yours.

**Pick a brand-native metaphor and commit to it everywhere the agent shows up:**
- Ground it in something that's already true about your brand (a product literally named for a feeling, a category, an origin story) rather than a generic "AI sparkle."
- One material property, applied consistently: how soft, how saturated, how much movement. A metaphor you can describe in a sentence ("soft, translucent, low-opacity gradients, nothing saturated") is one your team can actually apply consistently across ten different screens without a spec doc.
- Resist full saturation. An agent recommending across a wide, opinionated catalog (fashion, home, anything with its own color story) shouldn't compete with the content it's recommending. That's the same reason NET-A-PORTER, Vogue, and most serious editorial retail brands stay black-and-white in their UI chrome even though their imagery is full of color — the chrome has to stay neutral enough to represent anything.
- A light, consistent tint (5–10% opacity) is usually enough to signal "something is happening here" without turning every screen with AI into a rave.

---

## Don't Over-Badge AI. Earn the Signal.

If every headline has a sparkle icon, every card has a gradient border, and every button says "AI-powered," none of it means anything anymore. Users stop reading the signal within a session. Worse: if literally everything in the product is framed as "the AI part," you've implicitly told the user everything *else* is just regular shopping/browsing/whatever your product is — which raises the obvious question of why they need you at all versus any other version of that regular experience.

**The fix isn't more restraint on individual elements, it's a decision about scope:** should the entire product feel like a relationship with the agent (every interaction — favoriting, browsing, viewing a detail page — is data the agent is learning from), or is AI a bolt-on feature in an otherwise conventional product? Pick one. A product that's AI everywhere and calls out AI nowhere reads as more sophisticated than one that's AI in three places and screams about it in all three.

---

## Where the Agent Lives: Omnipresent Without Being Intrusive

The hardest unsolved problem in agent UX right now is where the entry point lives when the user isn't actively in a conversation.

**Anti-patterns, from real failures:**
- A chat interface that changes shape/position on every screen (nav bar here, a different-looking bubble there, a third treatment on a product detail page). Take a screenshot of the "same" agent surface on two different screens — if they read as two different products, you have a consistency problem, not a nuance.
- An "omnipresent chat sheet" that tries to be a persistent, always-expandable surface. This sounds right on paper and is genuinely difficult to execute on mobile — it tends to either take up too much screen real estate to feel like a background presence, or get so minimized it's undiscoverable.
- Full-screen or 30%-of-screen agent takeovers that interrupt browsing. If you're building a browse/discovery experience, people need to actually be able to browse — the agent should feel present, not load-bearing.

**What's working:** small, fixed-footprint, always-in-the-same-place entry points that don't compete with the primary content — closer to a persistent icon than a persistent panel. The agentic-browser pattern (a small, consistent tap target that's always available regardless of what's on screen, expanding into a full surface only on demand) is the best current reference: it accepts that most of the time the user just wants to browse, and stays out of the way until invited in.

---

## Platform Convention vs. Brand Identity

You will feel pressure to either (a) fully match the platform's current visual system (Apple's current AI treatment, Material's current AI treatment) so the experience feels "native," or (b) build something fully custom so the brand feels distinct. Both extremes have real costs.

**The resolution that actually works:** snap to platform conventions for structure and interaction (touch targets, gesture handling, how a sheet vs. a modal behaves, safe areas) so the user never has to think about whether they're using "your app" or "the phone" — then carry your brand identity through material, color, and metaphor, not through fighting the platform's interaction model. If you commit to platform-native structure, commit to it on every surface that shares this pattern (web, desktop, other platforms) rather than maintaining two incompatible systems that require constant translation between them.

The tell that you've gotten this wrong: your team is maintaining two separate visual languages for the same feature because one platform "needed" something custom. That's not a brand decision, that's technical debt with a design justification bolted on afterward.

---

## Related Skills
- `mobile-design` - Platform HIG specifics this skill assumes as a baseline
- `interaction-patterns` - Modal vs. drawer vs. inline, which applies to agent surfaces too
- `motion-design` - The actual animation principles behind a "thinking state"
- `design-systems` - How a brand-native AI metaphor gets tokenized so it stays consistent
