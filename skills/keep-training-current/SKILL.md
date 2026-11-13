---
name: keep-training-current
description: Keeps an organisation's training true and up to date with little manual work, and turns finished training into something that can be sold. Use for compliance training (data protection, security, health and safety, code of conduct, AI literacy), when a policy, law, product or price changed and courses must follow, when someone wants courses checked or refreshed on a schedule, wants an agent that updates training by itself, wants to know who must retrain or re-certify, or wants a landing page and a sales offer made from a course or activity.
---

# Keep training current

Training goes stale the day a policy changes. This skill treats a course as something with a source, a version and an owner, so that a change in the source becomes a reviewed update, not a rewrite.

Needs the MEXTY MCP (Authoring, Authoring + LMS or Enterprise). Assigning, tracking and certificates need the LMS.

## The principle

Nothing reaches learners without a person's yes. An agent may notice, draft and propose. Publishing, certifying and selling are decisions.

## 1. Tie each course to its source

For compliance training the source is the organisation's own document: the policy, the procedure, the regulation text they follow. General knowledge is not a source.

- Put the documents in a knowledge base (`list_knowledge_bases`) so agents and authors read the same text.
- In each course's description, record the source, its version or date, and who owns the course.
- Quote the source for anything a learner will be held to. If the source is silent, say so; do not fill the gap.

## 2. When the source changes

1. Read the new version against the old. List what changed in plain words: added, removed, tightened, renamed.
2. Find what it touches: `list_my_courses`, `list_my_evaluations`, `list_my_programs`, then read the ones that cite it.
3. Open a draft of each (`create_content_draft`). Change only what the source changed: the slide, the question, the pass mark.
4. `get_content_draft_diff` and `get_draft_impact`: what changed, and who is enrolled or already certified.
5. Ask for a review (`request_content_review`) from the course owner or the compliance lead.
6. After approval: `publish_content_draft`, or `schedule_content_draft` for the date the policy takes effect.

The old version stays in the history (`list_content_versions`), which is the record of what people were trained on and when.

## 3. Who must retrain

A certificate belongs to a version of a course. After a material change:

- `list_certificates` shows who holds one and for which version.
- Decide with the owner whether the change requires retraining. A corrected typo does not; a new obligation does.
- Reassign the course to the people concerned, and tell them what changed in one paragraph. People retrain faster when they only have to learn the difference.
- Certificates are issued by the course's rules, or by hand with `issue_certificate`; replacing or revoking one is the owner's decision.

Do not state that training makes an organisation compliant. It records that people were trained on a named version on a date.

## 4. Let an agent watch

A custom agent with the knowledge base and the MEXTY tools can do steps 1 to 4 on a schedule.

1. `create_agent`: instructions that name the sources, the courses they govern, and the rule "work in drafts, never publish, always request a review".
2. `create_scheduled_task`: how often, and what to report. Weekly is enough for most policies.
3. Each run ends with a short report: what changed, which drafts are waiting, for whom.
4. `list_scheduled_tasks` and `run_scheduled_task_now` to check it works before trusting it.

Good jobs for a scheduled agent:

| Job | What it produces |
|---|---|
| Policy watch | Drafts of the affected courses when a source document changes |
| Staleness check | A list of courses not reviewed for a year, with their owners |
| Expiry watch | Who holds a certificate that lapses in the next 30 days |
| New starter path | A draft onboarding path for a new role, from the existing courses |
| Product update | Drafts of sales and support training when a product sheet changes |

## 5. Turn training into a product

A finished activity or course can be offered outside the organisation.

- **A landing page and an offer**: `create_ad_campaign` makes the campaign and its page for a block; `write_ad_campaign_landing_page` holds the page you write. Say what the learner will be able to do, who it is for, how long it takes, and show the real thing.
- **A public audience**: post it on Mextribe, free or for members (`mextribe-community`).
- **A game**: an activity that works as a game can be listed on EdVerse (`edverse-publish-and-earn`).

An agent may draft the page when a new course is published. Prices and going live need the owner's yes, each time.

## Existing material

Bring it in before rewriting it: `import_storyline_block` takes an Articulate Storyline project or package as one activity, free and without AI. Then tie it to its source like the rest.

## Rules

- Learners' names, results and certificates stay in the workspace.
- Analytics and pass marks record training. They are not, alone, grounds for a decision about a person.
- An agent that cannot reach its source reports that and changes nothing.
