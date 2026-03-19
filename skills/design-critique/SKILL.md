---
name: design-critique
description: Opinionated design critique framework grounded in business outcomes, named principles, and specific actionable feedback. Use when reviewing designs, running critique sessions, or giving feedback that actually improves the work.
user-invocable: true
argument-hint: "[screenshot or description of design to critique]"
allowed-tools: Read, Glob, Grep, Write
---

# Design Critique

## The Point of Critique

Critique exists to produce better work. Not to check boxes. Not to make everyone feel heard. Not to generate a Notion page of "feedback themes." Better work. That's it.

Good critique is specific, grounded in principles, and framed in business impact. "The button could be better" is worthless. "The touch target is 36px, which is below the 44px minimum for comfortable mobile interaction per Fitts's Law, and on this screen it's the primary conversion action, so undersizing it directly costs you taps and revenue" is a critique.

---

## Step 1: Understand the Business Context

Before you look at a single pixel, answer these questions. If the designer can't answer them, that's the first and most important piece of feedback.

- **Who is this for?** Not "our users." A specific person with a specific job to be done. "A woman in her 30s who needs a wedding guest outfit by Saturday and doesn't want to spend two hours scrolling" is a user. "Shoppers" is not.
- **What's the job to be done?** Functional, emotional, and social. What are they hiring this screen to do?
- **What does success look like?** A number. Conversion rate, activation rate, retention at day 7, support ticket reduction. If the designer says "a better experience," push back. Better for whom, measured how?
- **What are the constraints?** Technical limitations, timeline, brand guidelines, platform conventions. Constraints aren't excuses. They're the box you're designing inside, and knowing them prevents useless feedback.

If you skip this step, everything that follows is noise. You'll be critiquing aesthetics instead of effectiveness.

---

## Step 2: Evaluate Against Business Outcomes

Don't evaluate against abstract dimensions like "Clarity" or "Efficiency" in a vacuum. Evaluate against whether the design achieves its stated business outcome.

### Primary Questions

| Question | What You're Really Asking |
|----------|--------------------------|
| **Does the user know what to do?** | Is the primary action obvious? Information hierarchy should make the job-to-be-done path the path of least resistance. (Jakob's Law, Hick's Law) |
| **Can they complete the job quickly?** | Every unnecessary step is a drop-off point. Count the taps/clicks from intent to completion. Each one costs you conversion. |
| **What happens when things go wrong?** | Error states, empty states, edge cases. These aren't polish items. They're the moments that determine whether a user comes back or churns. |
| **Does it work for everyone?** | Accessibility isn't a nice-to-have. 4.5:1 contrast ratio minimum. 44px touch targets on mobile. Screen reader support. These are table stakes, not stretch goals. |
| **Does it feel like the brand?** | The emotional response matters. A luxury fashion product that looks like a SaaS dashboard is failing even if it's "usable." Reference editorial traditions: does this feel like NET-A-PORTER or like a Bootstrap template? |
| **What about the edges?** | Empty states, first-time use, long text, error states, power user paths, slow connections. The edges are where trust is built or destroyed. |

### Named Principles to Ground Your Feedback

Always cite the principle. It turns opinion into argument.

- **Fitts's Law** - The time to reach a target is a function of distance and size. Small, far-away buttons cost you taps. Primary actions should be large and within thumb reach on mobile.
- **Hick's Law** - Decision time increases with the number of choices. "Here are 47 options" is a design failure. Curate. Five good options beat fifty mediocre ones.
- **Jakob's Law** - Users spend most of their time on other sites and expect yours to work the same way. Don't reinvent navigation patterns for the sake of being different.
- **Miller's Law** - People can hold about 7 items in working memory. If your screen asks users to track more than that, you've lost them.
- **Von Restorff Effect** - Distinctive items are more likely to be remembered. Your primary CTA should be visually distinct from everything else on the screen. If everything is bold, nothing is.
- **Aesthetic-Usability Effect** - Users perceive aesthetically pleasing designs as more usable. This isn't vanity. It's measurable. Beautiful products get more patience from users, which directly affects retention.
- **Serial Position Effect** - People remember the first and last items best. Put the most important content at the top and bottom. The middle is where attention goes to die.
- **Doherty Threshold** - System response time should be under 400ms to keep users engaged. If your design depends on fast loading but the page takes 3 seconds, the design is wrong regardless of how good it looks.
- **Gestalt Principles** - Proximity, similarity, closure, continuity. These aren't abstract theories. They're how the human brain groups information. If related items aren't visually grouped, users won't connect them.

---

## Step 3: Structure Your Feedback

For each issue, be specific. Vague feedback is worse than no feedback because it creates churn without direction.

1. **What you see** - Describe it neutrally and specifically. "The add-to-cart button is 36x32px on the mobile product detail page."
2. **What principle it violates** - "Fitts's Law recommends minimum 44x44px touch targets for primary actions."
3. **What it costs the business** - "This is the conversion action on our highest-traffic page. Undersized touch targets increase mis-taps and abandonment, directly reducing mobile conversion rate."
4. **What to do about it** - "Increase the touch target to minimum 48x48px. Consider making it full-width on mobile to eliminate targeting friction entirely."
5. **How urgent it is** - See priority framework below.

---

## Step 4: Prioritize by Business Impact

Forget "Critical / High / Medium / Low" severity scales disconnected from outcomes. Prioritize based on one question: does this block a business outcome?

### Priority Framework

- **Fix now** - Blocks a primary business outcome. Users can't complete the core job. Accessibility violations that exclude users. Errors that cause data loss. These ship before anything else.
- **Fix before launch** - Creates meaningful friction on a key path. Users can complete the job but it's harder than it should be. Measurable drop-off likely. "If we ship with this, we're leaving conversion on the table."
- **Fix soon** - Consistency issues, minor friction, polish gaps. The product works but doesn't feel as good as it should. This is the MVQP bar: would an early user form a negative permanent impression?
- **Track and revisit** - Genuine edge cases, power user optimizations, nice-to-haves. Log them. Don't let them block shipping. But don't pretend they don't exist either.

---

## Critique Etiquette

These aren't suggestions. These are rules.

### Critique the decision, not the pixels.
"Why did you choose a modal here instead of an inline expansion?" is good feedback. "I don't like modals" is a preference. Preferences are not critique. If you can't articulate the principle being violated, keep it to yourself until you can.

### Start with what's working, and say why.
Not to be polite. Because understanding what's working prevents you from accidentally wrecking it. "The information hierarchy on this page is strong. The primary action is immediately clear, and the supporting content doesn't compete with it" tells the designer what to protect.

### Frame the cost of inaction.
"If we don't fix this" is the most powerful phrase in critique. "If we don't fix this touch target, we're undersizing the primary conversion action on our highest-traffic mobile page" motivates action in a way "the button should be bigger" never will.

### Be specific enough to act on.
"The spacing feels off" is not feedback. "The 8px gap between the label and input field is tighter than the 12px gap between form groups, which breaks the visual hierarchy and makes the form feel cramped" is feedback.

### Silent critique first. Always.
If you're running a group session, everyone writes their feedback before anyone speaks. Written feedback surfaces honest signal. Verbal feedback surfaces whoever is most confident or most senior. Silent critique is the single best thing you can do for the quality of your team's feedback culture.

### Separate "what" from "how."
Your job in critique is to identify the problem and explain why it matters. The designer's job is to figure out the solution. "The navigation is buried" is a valid observation. "Move the nav to the top" is overstepping unless you're the design director and it's a strategic call.

### One more thing: no "I like" or "I don't like."
Critique is not about you. It's about the user, the business outcome, and the principles. "I like the color" contributes nothing. "The primary CTA uses the brand's action color at sufficient contrast (5.2:1), which creates clear visual hierarchy and meets WCAG AA" contributes everything.

---

## Related Skills
- `design-process` - Frameworks for structuring design work and when each one matters
- `design-heuristics` - Nielsen's 10 Heuristics for evaluation
- `laws-of-ux` - Named principles for grounding feedback in research
