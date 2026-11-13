---
name: assessment-design
description: Designs a fair, valid evaluation in MEXTY - a quiz, a unit test, a final exam, a certification check or a placement test - with questions, points and a pass mark. Use when someone asks for an assessment, test, exam, quiz or graded evaluation, wants questions written for a course or learning outcome, asks how to set a pass mark or weight questions, or wants to know whether an existing test measures what it should.
---

# Designing an evaluation

Needs the MEXTY MCP. An evaluation is an ordered list of steps; each step runs one interactive activity with its questions and is worth points.

## 1. What it certifies

Write one sentence: "A person who passes can ...". That is the evaluation's objective. If you cannot write it, the course is not ready to be assessed.

Decide the kind:

| Kind | Purpose | Consequence |
|---|---|---|
| Practice check | The learner sees what they know | None; unlimited tries |
| Unit test | The teacher sees who needs help | Low; feedback matters more than the mark |
| Final or certifying | A decision rests on it | High; needs review by a person who knows the subject |

## 2. Blueprint before questions

List the outcomes and give each a share of the points in proportion to its importance and teaching time. Then the level each is tested at:

- **Recall**: name, define, recognise.
- **Apply**: use it in a new, concrete case.
- **Analyse or judge**: compare, find the error, choose and justify.

Most of the points should sit on applying and judging. A test of recall certifies memory.

## 3. Write the steps

- 3 to 10 steps for a classic assessment, recall first, application and analysis last.
- Choose the activity by what is tested: ordering for a procedure, matching for relations, a calculation with a typed answer, a scenario with choices, an open question for reasoning.
- Every step needs the learner's input.
- Points per step add up to the total (20 by default). Check with `get_evaluation`; it warns when they do not.

Question rules:

- One idea per question, in plain words, with no negatives to trip on.
- Wrong options are the mistakes real learners make.
- No "all of the above", no trick wording, no clue in the length of the right answer.
- The question can be answered from what was taught.
- Solve every question yourself, and write the feedback for each wrong answer.

## 4. Pass mark

Set it from what "able to do" means, not from habit. Ask the subject owner: which questions must a competent person get right? For safety or compliance, some steps may need to be right regardless of the total; say so to the owner, since the total alone will not enforce it.

## 5. Fairness

- Language at the learners' level; the test measures the subject, not reading.
- Works by keyboard and on a phone; no colour-only information.
- Time limits only where speed is part of the skill.
- Names and contexts in scenarios are varied and neutral.

## 6. Build and release

`create_evaluation`, get your own copy of each activity (`check_bulk_block_ownership`), save each step's questions (`save_block_props`), then `add_evaluation_steps_bulk`. In a learning path, the final evaluation is the single exam at the end.

A person validates and publishes an evaluation in the app before learners can sit it. You cannot release it, and for a certifying test you should not want to.

## After the first sitting

Look at the results per question. One that nearly everyone fails is either badly taught or badly written; one that everyone passes may be testing nothing. Propose the fix as a draft.
