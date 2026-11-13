---
name: analytics-dashboards
description: Builds a custom analytics dashboard in the MEXTY workspace that answers one question about learning with live data. Use when someone wants a dashboard, a chart, a report page or a KPI view of their training or their games, such as completions per week, who is behind, which questions learners get wrong, time spent per course, onboarding progress per team, or wants to see or share learning data in a way the standard Analytics page does not show.
---

# Custom analytics dashboards

A dashboard is a page in **Analytics → Dashboards** that reads learning events live. It is built like an interactive activity, in code, and it stays up to date by itself.

Needs the MEXTY MCP (Authoring, Authoring + LMS or Enterprise).

## What decides what a dashboard shows

The person who opens it, never the code:

- A member with the analytics permission sees their organisation's learners, with names.
- Anyone else (a creator, a game author) sees the events on the content they own, with learners as pseudonyms. Those learners may be children.
- A per-learner breakdown follows the organisation's ranking setting. If it is off, do not rebuild a ranking from raw events.

So never hard-code a learner, an organisation or someone else's content id.

## 1. Start from the question

One dashboard, one question. Ask for it in the person's words, then pin down:

- **The measure**: completions, learners, average score, time spent, events.
- **The split**: by day, week or month; by course, path, evaluation or activity; by learner.
- **The filter**: a period, one path or course, one kind of event.
- **Who will read it**, and what they will do when the number is bad.

"Onboarding completions per week, by team, last 90 days, for the HR lead" is ready to build. "A dashboard about training" is not.

Check `list_analytics_dashboards` first. One may already answer it.

## 2. Create it

`create_analytics_dashboard({ title, description })` returns the `blockId` and `reads`: the filters, groupings, event kinds and fields a dashboard can use. Use that list; do not guess field names.

## 3. Build the page

It is a block, so the block rules apply:

1. `list_block_files`, then `read_block_files` on `AI.md`, `src/block.tsx` and `package.json`. The scaffold shows how the page asks `mexty.analytics` for data.
2. Write the page with `write_block_files` or `edit_block_files`. Keep the federation files as they are.
3. `get_block_build_status` until it builds.
4. `save_block_props` so it opens with its settings. Put the period, the chosen path and the labels in props, so the owner can change them without code.

Reads available: a session (who is looking and what they may see), events, a summary grouped by one of the splits, and the content list for pickers.

## 4. Make it readable

- The number that answers the question goes at the top, large, with its period.
- One chart per idea. A line for a trend over time, bars for comparing courses or teams, a table when people need to look someone up.
- Say what the reader is looking at: a title that states the measure, labelled axes, units.
- Show the empty state: "No completions in this period" is information.
- Works on a phone: stacked, no sideways scrolling.
- Colour is not the only signal: add a label or an icon to "behind" and "on track".

## 5. Share it

The owner shares the dashboard with roles, members or groups from the Analytics page. You cannot share it for them. Tell them who will see names and who will not.

## Rules

- Analytics support follow-up and learner support. Do not present a dashboard as the sole basis for a decision about a person: employment, promotion, grades, certification.
- No dashboard that singles out one named learner for anyone but the people allowed to see that learner.
- Do not export or copy learners' names or answers out of the workspace.

## Ideas that work

| Reader | Dashboard |
|---|---|
| HR or L&D | Onboarding completions per week; who has not started after 7 days |
| Compliance | Share of staff with a current certificate, per policy and per team; certificates expiring |
| A teacher | Skills answered wrong most often this week, per class |
| A course author | Where learners stop in a course, slide by slide |
| A game creator | Plays, finishes and the questions where players get stuck, per level |
