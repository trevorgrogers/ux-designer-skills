---
name: laws-of-ux
description: Master the 30 Laws of UX from lawsofux.com. Apply cognitive psychology, perception, and behavioral science principles to interface design. Use when evaluating designs, making interaction decisions, justifying design choices, or teaching UX fundamentals.
---

# Laws of UX

The Laws of UX are a collection of principles from psychology and cognitive science that designers can use to build more intuitive, human-centered interfaces. Based on Jon Yablonski's [Laws of UX](https://lawsofux.com/).

## When to Use This Skill

**Auto-loaded by agents:**
- design-lead — For general UX principle questions
- design-critic — For grounding critiques in named principles
- interaction-designer — For pattern selection rationale

**Use when you need:**
- Justification for a design decision with a named principle
- Evaluation of a design against cognitive science
- Teaching or explaining UX fundamentals
- Making trade-off decisions between competing patterns

---

## Heuristic & Decision Laws

### Hick's Law
**"The time it takes to make a decision increases with the number and complexity of choices."**

- Minimize choices when response times are critical
- Break complex tasks into smaller steps to reduce cognitive load
- Highlight recommended options to avoid overwhelming users
- Use progressive onboarding to minimize cognitive load for new users
- Don't oversimplify to the point of abstraction
- *Origin: William Edmund Hick & Ray Hyman, 1952*
- *Example: Google's homepage eliminates distractions to focus on a single action*

### Fitts's Law
**"The time to acquire a target is a function of the distance to and size of the target."**

- Touch targets should be large enough to select accurately (minimum 44x44px on mobile)
- Touch targets should have ample spacing between them
- Place important actions in easily reachable areas (thumb zones on mobile)
- Interactive elements should be positioned where they're most accessible
- *Origin: Paul Fitts, 1954*

### Jakob's Law
**"Users spend most of their time on other sites. They prefer your site to work the same way as all the other sites they already know."**

- Leverage existing mental models — users transfer expectations from familiar products
- Use established patterns so users focus on tasks, not learning your interface
- When redesigning, offer transition periods so users can adapt gradually
- Innovation should enhance, not replace, familiar interaction patterns
- *Origin: Jakob Nielsen, Nielsen Norman Group*
- *Example: YouTube's 2017 redesign allowed preview period with ability to revert*

### Miller's Law
**"The average person can keep approximately 7 (plus or minus 2) items in working memory."**

- Don't use this as an excuse to limit UI to 7 items
- Organize content into logical chunks of 5-9 items
- Working memory capacity varies — design for the lower end
- Chunking helps users process and remember information
- *Origin: George A. Miller, 1956*

### Occam's Razor
**"Among competing hypotheses that predict equally well, the one with the fewest assumptions should be selected."**

- Analyze and eliminate unnecessary elements without compromising function
- The simplest solution is usually the best solution
- Avoid adding features "just in case"
- Every element should earn its place in the interface

### Tesler's Law (Law of Conservation of Complexity)
**"For any system there is a certain amount of complexity that cannot be reduced."**

- All processes have a core of complexity that cannot be designed away
- The question is: does the user bear the complexity, or does the system?
- Ensure as much burden is shifted from user to system as possible
- Don't simplify interfaces to the point where users can't accomplish their goals
- *Origin: Larry Tesler, Xerox PARC*

### Pareto Principle
**"Roughly 80% of effects come from 20% of causes."**

- Focus design effort on the 20% of features that deliver 80% of value
- Identify and prioritize the most impactful elements
- Use analytics to find the most common user paths and optimize those first
- Not everything deserves equal design investment

---

## Perception & Attention Laws

### Law of Proximity
**"Objects that are near each other tend to be grouped together."**

- Use spacing to create visual groups — related elements should be close
- Proximity overrides similarity — close items are grouped even if they look different
- Applies to form fields, navigation items, card layouts, action buttons
- *Origin: Gestalt psychology*

### Law of Similarity
**"Elements that share visual characteristics are perceived as more related than those that don't."**

- Make functionally similar elements look similar (same color, shape, size)
- Use visual differentiation to distinguish between element types
- Consistency in visual treatment creates implicit grouping
- *Origin: Gestalt psychology*

### Law of Prägnanz (Law of Good Form)
**"People will perceive and interpret ambiguous or complex images in the simplest form possible."**

- The human eye simplifies complex shapes into recognizable patterns
- Design with simple, clear forms — users will fill in the blanks
- Reduce visual noise so the essential structure is perceived
- *Origin: Gestalt psychology*

### Law of Common Region
**"Elements tend to be perceived into groups if they are sharing an area with a clearly defined boundary."**

- Use borders, backgrounds, or containers to group related content
- Cards, wells, and sections create implicit grouping
- More explicit than proximity — use when proximity alone is ambiguous

### Law of Uniform Connectedness
**"Elements that are visually connected are perceived as more related than elements with no connection."**

- Lines, arrows, and connectors create explicit relationships
- Use connecting elements in flows, timelines, and step indicators
- Visual connections are stronger grouping cues than proximity or similarity

### Selective Attention
**"People filter stimuli to focus on what's relevant to their current goals."**

- Users have tunnel vision when task-focused — they miss things outside their focus
- Don't rely on peripheral elements for critical information
- Use pattern interrupts carefully (color, motion, contrast) for important messages
- Banner blindness is real — users learn to ignore areas they expect ads

### Von Restorff Effect (Isolation Effect)
**"When multiple similar objects are present, the one that differs from the rest is most likely to be remembered."**

- Make the most important element visually distinct (CTA buttons, key metrics)
- Don't make everything stand out — if everything is bold, nothing is
- Use color, size, or position to create visual hierarchy
- Avoid visual competition between multiple "highlighted" elements
- *Origin: Hedwig von Restorff, 1933*

### Serial Position Effect
**"Users tend to best remember the first and last items in a series."**

- Place the most important items at the beginning and end of lists
- Middle items are most likely to be forgotten
- Applies to navigation, onboarding steps, form fields, and content feeds
- The recency effect (last items) is stronger for short-term recall
- The primacy effect (first items) is stronger for long-term recall

---

## Behavioral & Motivation Laws

### Goal-Gradient Effect
**"The tendency to approach a goal increases with proximity to the goal."**

- Show progress indicators — users speed up as they see the finish line
- Use progress bars, step indicators, and completion percentages
- Artificial progress (starting at 20% instead of 0%) increases completion rates
- Break long processes into visible milestones

### Zeigarnik Effect
**"People remember uncompleted or interrupted tasks better than completed tasks."**

- Use this to drive engagement — show users what's incomplete
- Profile completion bars, unfinished onboarding steps, draft indicators
- Don't abuse it — anxiety-inducing incomplete states harm trust
- *Origin: Bluma Zeigarnik, 1927*

### Peak-End Rule
**"People judge an experience largely based on how they felt at its most intense point and at its end, not on the sum of every moment."**

- Invest in the emotional peak moment (delight, accomplishment, surprise)
- End every flow on a positive note — confirmation screens matter
- A great ending can redeem a mediocre middle
- Recovery from errors matters more than preventing all errors
- *Origin: Daniel Kahneman*

### Paradox of the Active User
**"Users never read manuals. They jump in and start using the product immediately."**

- Users want to start doing, not start learning
- Design for immediate action, not instruction-first onboarding
- Inline help and contextual guidance beats documentation
- Progressive disclosure over upfront tutorials

### Parkinson's Law
**"Any task will inflate until all of the available time is spent."**

- Set deadlines and time constraints to drive completion
- Shorter forms get completed faster than longer forms (even with same fields)
- Reduce perceived effort — smaller-looking tasks get started sooner
- Time pressure can improve decision quality (within reason)

### Flow
**"A state of complete immersion in a focused, enjoyable activity."**

- Remove friction that breaks concentration (unnecessary confirmations, interruptions)
- Match challenge to skill level — too easy is boring, too hard is frustrating
- Provide clear goals and immediate feedback
- Minimize distractions and context switches
- *Origin: Mihaly Csikszentmihalyi*

---

## Cognitive Load & Processing

### Cognitive Load
**"The total amount of mental effort being used in working memory."**

- Three types: intrinsic (task complexity), extraneous (poor design), germane (learning)
- Reduce extraneous load through clear design — that's the designer's job
- Don't add decorative elements that compete with functional ones
- Use established patterns to reduce learning cost (intrinsic load)

### Chunking
**"People tend to organize items into groups, or 'chunks,' when presented with complex information."**

- Phone numbers, credit card numbers, dates — chunking makes them manageable
- Apply to navigation (grouped menu items), content (sections), and data (tables)
- Optimal chunk size is 3-5 items per group
- Visual chunking (whitespace, borders) supports cognitive chunking

### Working Memory
**"A limited-capacity cognitive system responsible for temporarily holding and manipulating information."**

- Don't require users to remember information across screens
- Show, don't require recall — display previous selections, current context
- Reduce the need to hold information in mind by making it visible
- Forms should show summaries before final submission

### Mental Model
**"A mental model represents a person's compressed understanding of how something works."**

- Users have pre-existing mental models based on past experience
- Your design either matches or violates their model — mismatches cause confusion
- Research mental models before designing (card sorting, interviews)
- When you must break a mental model, provide explicit guidance for the transition

---

## Tolerance & Error

### Postel's Law (Robustness Principle)
**"Be liberal in what you accept, and conservative in what you send."**

- Accept varied user inputs (date formats, phone formats, with/without spaces)
- Provide clear, consistent outputs regardless of input variation
- Anticipate edge cases and handle them gracefully
- Validate and transform input rather than rejecting it
- *Origin: Jon Postel, TCP/IP specification*

### Aesthetic-Usability Effect
**"Users often perceive aesthetically pleasing design as design that's more usable."**

- Beautiful interfaces get more patience from users
- Visual polish masks minor usability problems — which is both a benefit and a testing risk
- Invest in visual design, but don't let it substitute for usability testing
- First impressions are heavily influenced by aesthetics
- *Origin: Masaaki Kurosu & Kaori Kashimura, Hitachi, 1995*

### Cognitive Bias
**"Systematic patterns of deviation from rationality in judgment."**

- Users are not rational actors — design for actual behavior, not ideal behavior
- Anchoring: first information seen disproportionately influences decisions
- Confirmation bias: users seek information that confirms existing beliefs
- Status quo bias: users prefer the current state over change
- Design with biases, not against them

### Choice Overload
**"When presented with too many options, people experience anxiety and decision paralysis."**

- More options reduces satisfaction with the chosen option
- Provide defaults and recommendations to reduce decision burden
- Use progressive disclosure — show essential options first, advanced later
- Filter and sort capabilities help users manage large option sets
- *Directly related to Hick's Law*

### Doherty Threshold
**"Productivity soars when a computer and its users interact at a pace (<400ms) that ensures neither has to wait on the other."**

- System response time should be under 400ms for the interaction to feel fluid
- Use loading indicators for anything over 1 second
- Skeleton screens and optimistic UI reduce perceived latency
- Animation can mask loading time (progressive image loading, content shimmer)
- *Origin: Walter Doherty & Ahrvind Thadani, IBM, 1982*

---

## Quick Reference: Applying Laws to Common Decisions

| Design Decision | Most Relevant Laws |
|----------------|-------------------|
| How many nav items? | Hick's Law, Miller's Law, Chunking |
| Button size and placement? | Fitts's Law, Von Restorff Effect |
| Should I follow convention or innovate? | Jakob's Law, Mental Model |
| How to show progress? | Goal-Gradient Effect, Zeigarnik Effect |
| How to handle errors? | Postel's Law, Peak-End Rule |
| How to group content? | Proximity, Similarity, Common Region |
| How to reduce cognitive load? | Chunking, Working Memory, Cognitive Load |
| How to drive completion? | Goal-Gradient, Zeigarnik, Parkinson's Law |
| CTA hierarchy? | Von Restorff, Serial Position Effect |
| Form design? | Cognitive Load, Chunking, Postel's Law |

---

## Related Skills
- `design-heuristics` — Nielsen's 10 Usability Heuristics
- `interaction-patterns` — Common interaction patterns and when to use them
- `accessibility-wcag` — WCAG 2.1/2.2 guidelines and testing

## Source
Based on [Laws of UX](https://lawsofux.com/) by Jon Yablonski. Laws are grounded in research from cognitive psychology, behavioral science, and human-computer interaction.
