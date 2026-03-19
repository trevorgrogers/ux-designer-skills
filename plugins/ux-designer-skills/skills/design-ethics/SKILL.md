---
name: design-ethics
description: Deceptive patterns (dark patterns), ethical design frameworks, persuasive vs. manipulative design, GDPR/consent UX. Use when reviewing designs for manipulation, designing consent flows, or evaluating ethical implications of design decisions.
---

# Design Ethics & Deceptive Patterns

Every deceptive pattern is a short-term revenue play that destroys long-term trust. If you have to trick someone into staying, your product isn't good enough. This isn't a moral argument (though it is). It's a business argument. Deceptive patterns tank retention, inflate support costs, and get you sued.

## When to Use This Skill

**Use when you need:**
- Audit a design for deceptive patterns
- Design a consent or privacy flow (GDPR/CCPA)
- Evaluate whether a design is persuasive vs. manipulative
- Ethical review of engagement mechanics

---

## Deceptive Patterns (Harry Brignull's 12 Types)

| Pattern | What It Does | Example |
|---------|-------------|---------|
| **Trick Questions** | Confusing wording leads to unintended actions | Double negatives in checkboxes |
| **Sneak into Basket** | Items added to cart without consent | Pre-selected add-ons at checkout |
| **Roach Motel** | Easy to enter, hard to leave | Amazon Prime's multi-page cancellation |
| **Privacy Zuckering** | Tricks users into sharing more data | Confusing privacy settings |
| **Price Comparison Prevention** | Hard to compare with competitors | Non-standard unit pricing |
| **Misdirection** | Draws attention away from important info | Prominent "Accept" with hidden "Decline" |
| **Hidden Costs** | Fees revealed only at final step | Shipping costs at checkout |
| **Bait and Switch** | Advertise one thing, deliver another | Free trial → auto-charge |
| **Confirmshaming** | Shame language on opt-out | "No, I don't want to save money" |
| **Disguised Ads** | Ads styled as content or navigation | Download buttons that are ads |
| **Forced Continuity** | Free trial silently becomes paid | No cancellation reminder |
| **Friend Spam** | Requests contacts under false pretenses | "Find friends" that spams contacts |

---

## The Ethical Design Litmus Test

For any design decision, ask:

1. **Is the user fully informed?** - Do they understand what will happen?
2. **Does the user retain genuine choice?** - Can they easily say no?
3. **Would they feel betrayed?** - If they understood the mechanism, would they feel tricked?
4. **Who benefits?** - Does this serve the user, the business, or only the business?

**Persuasive** (ethical): Transparent, user retains autonomy, benefits the user. (Duolingo streaks motivate learning.)

**Manipulative** (unethical): Hidden intent, exploits biases, benefits company at user's expense. (Hidden cancellation flows.)

---

## GDPR/CCPA Consent UX

### Legal Requirements
- Explicit opt-in consent for non-essential cookies
- Fines: up to 20M EUR or 4% of global turnover (GDPR)

### Design Rules

| Rule | Why |
|------|-----|
| **Button parity** | Accept and Reject must have equal visual prominence (size, font, color) |
| **Click parity** | Opting out must require same number of clicks as opting in |
| **No pre-ticked boxes** | All consent must be affirmative |
| **Easy withdrawal** | Revoking consent must be as easy as giving it |
| **Plain language** | Replace legal jargon with clear explanations |
| **Accessible** | 4.5:1 contrast, keyboard navigable, screen reader compatible |

---

## Related Skills
- `accessibility-wcag` - Overlaps on inclusive, non-discriminatory design
- `laws-of-ux` - Cognitive biases that deceptive patterns exploit
