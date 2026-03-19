---
name: ux-metrics
description: UX measurement that connects design work to business outcomes. HEART, GSM, SUS, task success, and the metrics that actually drive design decisions. Cuts through vanity metrics to focus on what proves impact.
---

# UX Metrics & Measurement

## When to Use This Skill

**Use when you need:**
- Success metrics for a design project
- UX KPIs for a product or feature
- Benchmarks for usability testing
- Stakeholder reporting on design impact
- Defining Goals-Signals-Metrics for a feature

---

## Most Teams Measure the Wrong Things

They track page views and time-on-site and call it "engagement." That's not engagement. That's often users being lost. High time-on-site in a checkout flow isn't a win. It means something is confusing.

The metrics that matter are the ones that connect user behavior to business outcomes. If a metric doesn't help you make a design decision or prove design impact, stop tracking it. It's noise.

---

## HEART Framework (Google)

Created by Kerry Rodden, Hilary Hutchinson, and Xin Fu at Google. This is the best framework for connecting design work to business outcomes.

| Dimension | What It Measures | Example Metrics |
|-----------|-----------------|----------------|
| **Happiness** | User satisfaction, perceived ease | In-app satisfaction surveys, post-task ratings, NPS |
| **Engagement** | Depth and frequency of interaction | Visits/week, actions/session, shares/user, time in feature |
| **Adoption** | New users or new feature uptake | New accounts, app downloads, feature adoption within 7 days |
| **Retention** | Existing users who return | D7/D30 retention, churn rate, subscription renewal |
| **Task Success** | Efficiency and effectiveness | Task completion rate, time on task, error rate |

Not every dimension matters for every project. Pick 2-3. If you're measuring all 5, you're not prioritizing. A new feature launch? Adoption and Task Success. A redesign of an existing flow? Retention and Happiness. Know what question you're trying to answer.

### Goals-Signals-Metrics (GSM) Process

This is the most important part of HEART. The framework is just categories. GSM is where it becomes actionable.

For each HEART dimension you choose:

1. **Goal** - What are you trying to achieve? ("Users find relevant content quickly")
2. **Signal** - What user behavior indicates progress? ("Users click first search result")
3. **Metric** - How do you quantify the signal? ("% of searches where user clicks result #1 within 10 seconds")

If you can't articulate Goal > Signal > Metric for your design work, you can't prove it mattered. This is the single most important exercise a designer can do before starting a project. Write it down. Get agreement from your PM and eng lead. Revisit it when you ship.

---

## PULSE Metrics

**P**age views, **U**ptime, **L**atency, **S**even-day active users, **E**arnings.

These are infrastructure metrics, not UX metrics. They tell you if the system is working, not if the experience is good. A product can have 99.9% uptime, fast page loads, and growing page views while delivering a terrible user experience.

Don't report PULSE metrics in a design review. They're important for the business, but they don't tell you anything about the quality of the design. If someone asks "how do we know the redesign worked?" and you answer with page views, you haven't answered the question.

---

## System Usability Scale (SUS)

10-item questionnaire, 5-point Likert scales. Created by John Brooke, 1986. Still the most widely used standardized usability questionnaire.

### Scoring Benchmarks

| Score | Grade | Percentile | Interpretation |
|-------|-------|-----------|----------------|
| 90-100 | A+ | Top 5% | Exceptional |
| 80-89 | A | Top 10% | Excellent, users likely to recommend |
| 70-79 | B | Above avg | Good |
| **68** | **C** | **Average** | **Benchmark from 500+ studies** |
| 51-67 | D | Below avg | Needs improvement |
| <51 | F | Bottom 15% | Poor, significant usability issues |

SUS is useful for benchmarking over time, not for diagnosing specific problems. If your SUS score dropped, it tells you something got worse. It doesn't tell you what. You still need qualitative research to find the specific issues.

The real value of SUS is the trend line. Run it quarterly. If the number goes up after a redesign, you improved usability. If it goes down, something broke. Then go figure out what.

---

## Task Success Metrics

| Metric | What It Measures | Benchmark |
|--------|-----------------|-----------|
| **Task success rate** | Can users complete the task? | >78% average across studies |
| **Time on task** | How long does it take? | Compare to your baseline or competitors |
| **Error rate** | How many mistakes per task? | <2 per task (varies by complexity) |
| **Learnability** | Improvement across attempts | Time should decrease 20-30% by 3rd attempt |

These map to ISO 9241: **Effectiveness** (success rate), **Efficiency** (time on task), **Satisfaction** (SUS/CSAT).

---

## CSAT vs. NPS for Design

| | CSAT | NPS |
|---|------|-----|
| **Scope** | Specific touchpoint | Overall product/brand |
| **Question** | "How satisfied were you with X?" | "How likely to recommend?" |
| **Scale** | 1-5 or 1-7 | 0-10 |
| **Best for** | Micro-level design feedback | Longitudinal tracking |
| **Design actionability** | High, identifies exact friction | Low, too broad for design changes |

**Use both:** CSAT at touchpoint level for design iteration. NPS for overall experience tracking. But don't pretend NPS tells you anything specific about design quality. It doesn't.

---

## Metrics That Actually Drive Design Decisions

Beyond the frameworks, these are the metrics that change how you design:

### Task Success Rate
The most direct measure of whether your design works. If users can't complete the core task, nothing else matters. Measure it on your critical flows and track it over time.

### Time-to-Value
How fast does a new user get to their first win? This is the activation metric that matters most. If your onboarding takes 10 minutes but a competitor's takes 2, you're losing users before they ever see what makes your product good. Measure time from signup to first meaningful action.

### Retention Curves
Don't just look at D7 and D30 numbers. Look at the shape of the curve. A product that drops 50% in week 1 then flattens is healthy. A product that drops 10% per week forever is dying. The shape tells you whether you have a product-market fit problem or an activation problem.

### Conversion by Acquisition Channel
This one matters more than most designers realize. Organic users and paid users behave differently. At Daydream, organic users converted at 4.0% while paid converted at 1.7%. If you're designing based on aggregate conversion data, you're designing for a user that doesn't exist. Segment by channel. Design for your best users, not your average.

### The Most Important Metric

The most important metric for any design project is the one you defined before you started designing. If you didn't define it, you can't prove impact, and you're just hoping.

Write it down before you open Figma. Get buy-in from your PM. Measure it after you ship. This is how designers build credibility. Not with pretty deliverables, but with measurable outcomes.

---

## Related Skills
- `usability-testing` - Study design and analysis methods
- `design-heuristics` - Expert evaluation (complements quantitative metrics)
