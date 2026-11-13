---
name: onboarding-path
description: Builds an onboarding learning path for a role in a company, from the documents the company already has. Use when someone needs to onboard new hires, a new team, contractors, seasonal staff or a newly promoted manager, asks for a first-week or first-90-days plan, an induction, a starter kit for a role, or wants onboarding that is the same quality for everyone and shows who is on track.
---

# An onboarding path for a role

Needs the MEXTY MCP (Authoring + LMS to assign and track).

## 1. What must be true, and by when

Ask for the role and three dates: what the person must be able to do on day 1, by the end of week 1, and by day 30 or 90. Onboarding fails when it lists what to read instead of what to be able to do.

Collect what exists: the handbook, the security and conduct policies, the product sheet, the tools list, the org chart. Reuse existing courses (`list_my_courses`); most roles share the first half.

## 2. Shape of the path

| Stage | Holds | Typical length |
|---|---|---|
| Before day 1 | Welcome, who is who, how the first day goes | 10 min |
| Day 1 | Must-know rules: security, safety, conduct. Each with a short check | 30 to 45 min |
| Week 1 | The tools and the job's core task, practised in an activity | 2 to 3 short courses |
| Day 30 | The role's own knowledge: product, process, customers | Branches by team |
| End | One final evaluation, and a certificate if the company issues one | 15 to 20 min |

Build it as a learning path: `create_program`, then the nodes and links in bulk. Rules that matter:

- Common courses first, then parallel branches per team, joined by one lock before one final evaluation. Never one exam per branch.
- Locks gate access. Deadlines only show on the learner's calendar; use relative ones ("7 days after the previous step") so the path works for anyone's start date.
- Each course is short and ends on something the learner does. A new hire should practise the returns process, not read about it.

## 3. Write from the company's text

Quote the handbook and policies for rules. Where the documents are silent or contradict each other, list the gaps for the owner; do not invent a rule. Use the company's own words for tools, teams and products.

## 4. Review, assign, follow

- Work in a draft and ask the HR or team lead to review (`build-together`).
- Assign to the new starters' role or group; seats are capped, so stop on a seats-full refusal.
- After two weeks, look at where people stop (`get_analytics_overview`), or build an "onboarding completions per week" dashboard (`analytics-dashboards`).
- When a policy changes, the path follows (`keep-training-current`).
