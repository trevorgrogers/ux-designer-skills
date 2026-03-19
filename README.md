# UX Designer Skills for Claude Code

Design leadership in your terminal. Not a checklist of best practices. A set of opinionated design agents and skills built by a design leader who actually does this work, grounded in cognitive psychology, real research, and the belief that every design decision should map to a business outcome.

This is how I think about design. Now Claude thinks about it the same way.

## Philosophy

**Artifacts over opinions.** Make the thing that ends the debate.

**Speak business, not design.** "This change keeps users past day 7" changes a roadmap. "Delightful UX" changes nothing.

**MVQP over MVP.** Ship fast, but hold a hard quality bar on anything customer-facing.

**Editorial over algorithmic.** Five curated options beats forty-seven search results.

**Validate before building.** Who is this for, what problem does it solve, what does success look like?

Read the full [design philosophy](PHILOSOPHY.md).

## Install

```
/plugin marketplace add https://github.com/trevorgrogers/ux-designer-skills
/plugin install ux-designer-skills
```

## What's Included

### 7 Specialist Agents

| Agent | What It Does |
|-------|-------------|
| **design-lead** | Routes to the right specialist. Pushes back when the problem isn't defined. |
| **design-critic** | Structured critiques grounded in named principles and business outcomes |
| **interaction-designer** | Pattern selection, flows, states, and the boring-but-correct choice |
| **accessibility-auditor** | WCAG 2.1/2.2 audits with specific, implementable fixes |
| **information-architect** | Navigation, taxonomy, content hierarchy, search as navigation |
| **design-systems-lead** | Tokens, components, governance. Adoption is the only metric. |
| **usability-researcher** | Study design, protocols, analysis. Research without action is tourism. |

### 16 Skills

#### Foundations
| Skill | What You Get |
|-------|-----------|
| **laws-of-ux** | All 30 Laws of UX. The named principles behind why things feel right or wrong. |
| **design-heuristics** | Nielsen's 10 + Shneiderman's 8. How to actually use them, not just list them. |
| **design-process** | JTBD, Design Sprint, Double Diamond. When each matters and when it's overhead. |
| **design-ethics** | Deceptive patterns, GDPR consent UX, the ethical litmus test |

#### Craft
| Skill | What You Get |
|-------|-----------|
| **design-critique** | How to give feedback that produces better work, not hurt feelings |
| **interaction-patterns** | Modals vs. drawers vs. inline. The right pattern for the context. |
| **design-systems** | Token architecture, component specs, governance. Don't build this before PMF. |
| **motion-design** | Disney's 12 principles for UI. When to animate and when to stop. |
| **mobile-design** | iOS HIG, Material Design 3, gestures, haptics. Mobile first, always. |
| **modern-css** | Container queries, :has(), fluid typography. What designers need to know. |

#### Figma
| Skill | What You Get |
|-------|-----------|
| **figma-best-practices** | File organization at scale, component architecture, tokens, dev handoff |
| **figma-ai-coding** | Figma MCP + Claude Code workflow, Code Connect, vibe coding done right |

#### Research & Measurement
| Skill | What You Get |
|-------|-----------|
| **accessibility-wcag** | WCAG 2.1/2.2 quick reference, ARIA patterns, the one test you should always run |
| **information-architecture** | Navigation design, taxonomy, labeling. Search is navigation. |
| **usability-testing** | 5 users, one afternoon, problems found. That's the whole method. |
| **ux-metrics** | HEART framework, SUS scoring, and the metrics that actually drive design decisions |

## Usage

Ask design questions naturally:

```
"Critique this checkout flow"
"Should I use a modal or a drawer for this?"
"Is this color contrast accessible?"
"How should I structure the navigation for this app?"
"Write a usability test plan for onboarding"
"How should I set up Figma for vibe coding with Claude Code?"
```

## Built On

- [Laws of UX](https://lawsofux.com/) by Jon Yablonski
- [Nielsen Norman Group](https://www.nngroup.com/) heuristics and research
- [WCAG 2.1/2.2](https://www.w3.org/WAI/standards-guidelines/wcag/) W3C accessibility guidelines
- [Atomic Design](https://atomicdesign.bradfrost.com/) by Brad Frost
- [Figma Best Practices](https://www.figma.com/best-practices/) official documentation
- [Material Design 3](https://m3.material.io/) by Google
- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
- [Google HEART Framework](https://research.google/pubs/measuring-the-user-experience-on-a-large-scale-user-centered-metrics-for-web-applications/)

## Author

Built by [Trevor Rogers](https://github.com/trevorgrogers). Design leader, currently at Daydream. Previously Meta, Shopify. I build things, lead teams, and believe craft is the edge.

## Contributing

PRs welcome. Add new skills, expand existing ones, or add templates to the assets folders.

## License

MIT
