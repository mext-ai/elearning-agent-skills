---
name: track-kid-progress
description: Helps a parent, guardian or teacher see what their child learned on EdVerse over a period they choose, as a short plain-language report with what to do next. Use when a grown-up asks how their kid is doing, what they learned or practised this week or this month, where they are stuck, whether screen time is reasonable, which game to try next, or wants a regular weekly or monthly progress report, or help reading the EdVerse Learners dashboard.
---

# Track what my kid learned

For grown-ups, not for children. The report is about one family's own learners and stays with that family.

The skill is free. The report itself needs a **learner seat** for the child (from €5 a month, less per learner as a school or family adds more; the Learners page shows the exact price).

| On the Learners page, for every kid profile | With a learner seat |
|---|---|
| Play time, games played, days active | Skills mastered |
| When they play (morning, after school, evening) | Needs practice: skills answered right less than 60% of the time |
| Today's minutes against the daily limit | Subjects they play, progress in each game |
| | The report through your AI (`get_learner_report`) |

A learner seat also unlocks every ★ Included game for that child.

## 1. Agree on the question

Ask only what is missing:

- **Which learner**, if there are several.
- **Which period.** EdVerse reports over the last 7 or 30 days. For a longer stretch (a term, a school year), build it from saved monthly reports; see step 5.
- **What they want to know.** "Is the maths getting better?" gives a more useful report than "everything".

## 2. Get the data

Call `get_learner_report` on the EdVerse MCP, signed in as the grown-up:

- `days`: 7 or 30.
- `timeZone`: the family's time zone, so days start and end where they live.
- `profileId`: one learner, or leave it out for all of them.

It returns, for each learner with a seat: minutes played and minutes per day, days active, the games played, skills mastered, skills that need practice with their accuracy, subjects, when they play, and today's minutes against the daily limit.

A learner without a seat comes back with `seat: false` and no play data. Say so plainly, tell the grown-up what they can still see themselves on the Learners page (play time, games played, days active), and give the `seatsUrl` if they want the report. Do not rebuild the report another way, and do not guess at skills from play time.

Never ask for the child's password or sign in as the child, and never ask the child for anything.

## 3. Read it

- **Practice, not minutes.** Thirty minutes spread over five days is worth more than ninety on one. Look at days active first.
- **Mastered** means answered right consistently, in play. It is evidence of practice, not a grade.
- **Needs practice** is the most useful line. Name the skill exactly, and check whether it is one game or several: one game may be a confusing level, several is the skill.
- **A game started and dropped** is often too hard, too easy or too much reading for the age. Say which you think it is and why.
- **Time of day and the daily limit**: note it only if it explains something (late play, limit reached every day).
- Small numbers prove little. With a few plays, say so instead of drawing a trend.

## 4. Write the report

Short enough to read standing up. In the grown-up's language, no jargon.

```
[Name] · [period]

In short: one sentence.

Practised: what, in which games, on how many days.
Getting good at: skills mastered, with one concrete example.
Needs practice: one or two skills, said kindly, with what it looks like in the game.
Try next: one game, and one thing to do together away from the screen.
Screen time: total, and how it sits against the limit you set.
```

Rules for the wording:

- Describe what the child did, never what the child is. "Mixes up thirds and quarters" is useful; "weak at maths" is not.
- No comparison with other children.
- No prediction of school grades.
- For "try next", use `search_edverse_store` with the skill and the age, and check the game is in a language the child plays in.
- If they want a version to read with the child, write three lines: what went well, one thing to try, and a question the child can answer.

## 5. A regular report

- **Weekly or monthly**: if the AI app can schedule a task, offer to set one up that calls `get_learner_report` for the new period and writes the report. Otherwise suggest a day of the week and keep the same template so reports compare.
- **Over a longer period**: keep each report's facts (dates, minutes, days active, mastered, needs practice). A term report is these laid side by side: what moved from "needs practice" to "mastered", what stayed.
- Store reports where the grown-up chooses. Do not post them or send them to anyone, including a teacher, unless the grown-up asks.

## 6. Act on it

- A skill that needs practice: find a game for it, or turn the next homework on that skill into one (`homework-to-game`).
- Too much or too late: the grown-up sets a daily limit or quiet hours in **Settings**. You cannot change these.
- A game that was scary, confusing or broken: the Report button in the game, or a suggestion in its Suggestion box.

## Privacy

A child's name, age and play history are personal data. Use them for this report only. Do not put them in a search, a prompt to another service, a file name that will be shared, or a public post.
