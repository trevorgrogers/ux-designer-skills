---
name: design-process
description: Design process philosophy and frameworks. When to use JTBD, Design Sprints, Double Diamond, IDEO. How to run outcome-driven design, effective critique, and recognize when process is theater. Use when planning design work, structuring discovery, or choosing the right level of rigor for the problem.
---

# Design Process

## The Only Thing That Matters

Design process exists for one reason: to produce artifacts that change conversations. Not to follow steps. Not to fill Confluence pages. Not to make stakeholders feel like "the process was followed."

The artifact ends the debate. A prototype beats a slide deck. A research doc with a recommendation beats a readout with no opinion. A brief that frames three jobs to be done beats a kickoff meeting where everyone nods along and leaves confused.

If your process isn't producing things that move decisions forward, it's not a process. It's a performance.

---

## Jobs-to-Be-Done (JTBD)

This comes first because it's the foundation. Every other framework is downstream of understanding what job the user is hiring your product to do.

People don't buy products. They hire them. And every job has three dimensions:

- **Functional** - The practical task ("I need to find a dress for a wedding this weekend")
- **Emotional** - How they want to feel ("I want to feel like I nailed it without trying too hard")
- **Social** - How they want to be perceived ("I want compliments, not questions about where I found it")

**Job statement format:**
> "When [situation], I want to [motivation], so I can [expected outcome]."

**When it matters:** Always. JTBD should be in every brief, every PRD, every design review. If you can't articulate the job, you're not ready to design. When I wrote the Collections Redesign brief, the entire thing organized around three jobs to be done. That's how you keep a team aligned on what matters and prevent scope creep disguised as "good ideas."

**When it's overhead:** Never. If someone tells you JTBD is too heavy for the project, the project probably isn't worth doing.

Strategyn reports teams using JTBD achieve an 86% innovation success rate. That's not because the framework is magic. It's because it forces you to validate the problem before falling in love with a solution.

---

## Outcome-Driven Design

**Impact > Outcome > Output**

- **Impact**: The business result (reduce churn by 15%)
- **Outcome**: The behavior change (users find relevant products in their first session)
- **Output**: The feature (curated collections with editorial recommendations)

This hierarchy matters because most teams skip straight to output. "We need a new search page." Why? "Because the old one is bad." That's not a reason. That's a feeling.

Every design surface maps to a business outcome. If it doesn't, question whether it should exist. Every review should start with: "What outcome are we driving?" not "What are we building?"

An output is what you ship. An outcome is the behavior you change. An impact is the number that moves. Design for the impact. Measure the outcome. Ship the output.

---

## Google Design Sprint (Jake Knapp)

The best framework for when you need to answer a big question fast and you don't have months to figure it out.

| Day | Focus | Key Activity |
|-----|-------|-------------|
| **Monday** | Understand | Set long-term goal, map the challenge, pick a target |
| **Tuesday** | Diverge | Individual sketching. No group brainstorming. |
| **Wednesday** | Decide | Silent critique, dot voting, storyboard the winner |
| **Thursday** | Prototype | Build a realistic facade in one day |
| **Friday** | Validate | Interview 5 customers using the prototype |

**When it matters:** High-stakes decisions with real ambiguity. New product directions. Major redesigns. Moments where the team is going in circles and needs a forcing function. The no-group-brainstorming rule is the best part. Individual sketching kills groupthink. Silent critique (Wednesday) is how you get honest signal instead of whoever-talks-loudest-wins.

**When it's overhead:** Small iterations on existing features. Bug fixes. Anything where the problem is already well-defined and you just need to execute. Running a 5-day sprint to redesign a settings page is cosplaying as a startup.

---

## Double Diamond (British Design Council)

Two phases: figure out the right problem, then figure out the right solution.

**Diamond 1, Problem Space:**
- **Discover** (Diverge): Research broadly. Talk to users. Look at data. Don't jump to solutions.
- **Define** (Converge): Synthesize into a clear problem statement. One sentence. If it takes a paragraph, you haven't converged.

**Diamond 2, Solution Space:**
- **Develop** (Diverge): Generate multiple approaches. Sketch. Prototype. Explore.
- **Deliver** (Converge): Test, refine, ship.

**When it matters:** Projects where you genuinely don't know what the problem is yet. Discovery work. New market entry. When leadership says "our users are unhappy" but can't tell you why.

**When it's overhead:** When the problem is already validated. If you have data showing organic users convert at 4% and paid users at 1.7%, you don't need to "discover" the problem. You need to fix the onboarding for paid users. Skipping straight to Diamond 2 is fine. The framework is a tool, not a religion.

---

## IDEO's Design Thinking (5 Phases)

1. **Empathize** - Understand users through observation, interviews, immersion
2. **Define** - Synthesize into a clear problem statement
3. **Ideate** - Generate a wide range of solutions
4. **Prototype** - Build to learn, not to ship
5. **Test** - Put it in front of real users and iterate

**When it matters:** Teaching junior designers how to think. Workshops with non-design stakeholders who need a shared vocabulary. It's a good mental model for someone who's never done design work before.

**When it's overhead:** For experienced teams, this is training wheels. You don't need to label each phase. You already do this intuitively. If your team is spending time arguing about whether they're in "Ideate" or "Prototype," you've confused the map for the territory. Just make things and test them.

---

## Design Critique Culture

Critique is not a meeting format. It's a culture of producing better work through structured, honest feedback. The goal of critique is artifacts, not discussion. If a critique session ends with "great discussion" and no clear next steps, it failed.

### How to Run Critique

- **Size**: 5-6 people. More than that and you get a presentation, not a critique.
- **Structure**: Designer presents context first. The job to be done, the business outcome, the constraints. No one looks at the design until they understand the problem.
- **Silent critique is king.** Everyone writes feedback independently before anyone speaks. This is non-negotiable. The moment you open it up to live discussion first, you get anchoring bias and whoever speaks first sets the frame. Written feedback surfaces real signal.
- **Timeboxing**: 30 minutes max per design. Constraint creates focus.
- **Output**: Every critique ends with a written list of decisions made and open questions. If it's not written down, it didn't happen.

### Formats

- **Silent critique** (default): Written feedback, then discussion. Always start here.
- **Gallery walk**: Designs posted on walls or in a shared space. Participants annotate with sticky notes before any conversation. Good for reviewing multiple directions.
- **Round-robin**: Each participant takes turns giving feedback. Use sparingly, only when you need to hear from everyone equally (like cross-functional reviews where engineering needs airtime).

### Critique Etiquette

- Critique the decision, not the pixels. "Why did you choose a carousel here?" not "I don't like carousels."
- If you can't articulate the principle being violated, it's a preference, not feedback. "This feels off" is not useful. "The touch target is 36px, which is below the 44px minimum for comfortable mobile interaction (Fitts's Law)" is useful.
- Start with what's working and why. Not to be nice. Because understanding what's working prevents you from accidentally breaking it.
- Frame cost. "If we don't fix this, here's what it costs in drop-off, support tickets, conversion."

---

## When Process Becomes Theater

Here's the thing nobody wants to say: most design process is theater. It's performative rigor that substitutes for actually making things.

Signs your process has become theater:

- **You're documenting more than you're designing.** If your design system documentation is more polished than your actual product, your priorities are inverted.
- **You're running workshops to avoid decisions.** Workshops are great for generating options. They're terrible for making choices. If you leave a workshop without a decision, you ran a group therapy session.
- **Your critique sessions produce more critique sessions.** Feedback loops are healthy. Infinite loops are dysfunction. At some point, someone needs to make a call and ship.
- **You're following the process because it's the process.** "We always do user interviews first." Do you? Or do you already know the answer and you're using research as a security blanket? Research without action is tourism.
- **The fidelity of your process artifacts exceeds the fidelity of your product.** Beautiful journey maps, polished personas, gorgeous Miro boards. And a product that hasn't shipped in 6 months.

The fix is simple: ask "what decision does this activity produce?" If you can't answer that, skip it. Make the thing. Test the thing. Ship the thing.

Process serves the work. The moment it's the other way around, you've lost the plot.

---

## Related Skills
- `design-critique` - Structured critique framework for reviewing specific designs
- `usability-testing` - Testing methodology
- `ux-metrics` - Measuring outcomes
