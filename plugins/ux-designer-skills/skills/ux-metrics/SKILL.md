---
name: ux-metrics
description: UX measurement frameworks — Google HEART, PULSE, SUS scoring, task success benchmarks, NPS/CSAT for design. Use when defining success metrics, measuring design quality, setting UX KPIs, or reporting design impact to stakeholders.
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

## HEART Framework (Google)

Created by Kerry Rodden, Hilary Hutchinson, and Xin Fu at Google. Measures UX quality at scale.

| Dimension | What It Measures | Example Metrics |
|-----------|-----------------|----------------|
| **Happiness** | User satisfaction, perceived ease | In-app satisfaction surveys, post-task ratings, NPS |
| **Engagement** | Depth and frequency of interaction | Visits/week, actions/session, shares/user, time in feature |
| **Adoption** | New users or new feature uptake | New accounts, app downloads, feature adoption within 7 days |
| **Retention** | Existing users who return | D7/D30 retention, churn rate, subscription renewal |
| **Task Success** | Efficiency and effectiveness | Task completion rate, time on task, error rate |

Not all dimensions are relevant to every project. Choose based on product goals.

### Goals-Signals-Metrics (GSM) Process

For each HEART dimension you choose:

1. **Goal** — What are you trying to achieve? ("Users find relevant content quickly")
2. **Signal** — What user behavior indicates progress? ("Users click first search result")
3. **Metric** — How do you quantify the signal? ("% of searches where user clicks result #1 within 10 seconds")

---

## PULSE Metrics

**P**age views, **U**ptime, **L**atency, **S**even-day active users, **E**arnings.

Low-level, indirect metrics of UX. They tell you *what* is happening but not *why*. Use PULSE for system health; use HEART for UX quality.

---

## System Usability Scale (SUS)

10-item questionnaire, 5-point Likert scales. Created by John Brooke, 1986.

### Scoring Benchmarks

| Score | Grade | Percentile | Interpretation |
|-------|-------|-----------|----------------|
| 90-100 | A+ | Top 5% | Exceptional |
| 80-89 | A | Top 10% | Excellent — users likely to recommend |
| 70-79 | B | Above avg | Good |
| **68** | **C** | **Average** | **Benchmark from 500+ studies** |
| 51-67 | D | Below avg | Needs improvement |
| <51 | F | Bottom 15% | Poor — significant usability issues |

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
| **Design actionability** | High — identifies exact friction | Low — too broad for design changes |

**Use both:** CSAT at touchpoint level for design iteration; NPS for overall experience tracking.

---

## Related Skills
- `usability-testing` — Study design and analysis methods
- `design-heuristics` — Expert evaluation (complements quantitative metrics)
