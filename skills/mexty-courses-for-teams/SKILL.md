---
name: mexty-courses-for-teams
description: Builds and distributes learning for an organisation with the MEXTY MCP. Use when a school, university, training provider or company wants courses, interactive activities, evaluations, learning paths or certificates, wants to turn documents or slides into training, onboard staff, train customers or partners, invite learners and manage seats, or see who completed what. Also explains which MEXTY plan the MCP and the LMS need.
---

# Courses and learning paths for organisations

MEXTY has two halves that are bought separately or together:

- **Authoring**: creators build courses, interactive blocks, evaluations and learning paths, and export to HTML and SCORM.
- **LMS**: learners are invited, assigned content and tracked.

## Plans

The MEXTY MCP server is available on **Authoring**, **Authoring + LMS** and **Enterprise**. It is not part of Free or LMS alone. Assigning content to learners and seeing their progress needs a plan with the LMS. Current prices are at https://mexty.ai/pricing; do not quote prices from memory.

If the person only wants to make games or run a creator community, EdVerse and Mextribe are free: see `mexty-start`.

The MCP's writes spend no MEXTY credits. Only media generation does.

## Before writing

Ask what the organisation needs to be true afterwards: who can do what, by when. Then:

1. `list_my_courses`, `list_my_blocks`, `list_my_programs`, `list_my_evaluations`: build on what exists.
2. `list_course_template_series` and `list_store_blocks`: a template series gives a whole course one visual language. Call `check_bulk_block_ownership` before using a store block.
3. Ground every fact in the source the organisation gave you. Compliance and safety training must match their policy, not general knowledge.

## What to build

| Need | Build |
|---|---|
| One topic, 10 to 60 minutes | A course of slides with interactive blocks |
| A skill to practise | An interactive block where the learner does the thing (drag, order, simulate), not only answers about it |
| Proof of competence | An evaluation, with a certificate on the course |
| A curriculum, an onboarding, a qualification | A learning path (program) of courses and evaluations in order |

Follow the server's own instructions for each type; they are strict for good reasons. Two rules matter most:

- A block is not finished until its props are saved. Code alone renders an empty state.
- Never invent ids or media URLs. List, read, then write; use `search_media` for media.

## Review before learners see it

Work in a draft (`create_content_draft`), ask for a review (`request_content_review`), and publish or schedule it once approved. Check `get_my_access` before editing something that is not yours. Co-authors, reviewers, comments and version history are covered in `build-together`.

## Distribute

- Invite people with `add_or_invite_organization_member`; roles decide what they can do.
- Seats are capped. On a seats-full or plan-required refusal, stop and tell the person what to change in "Manage plan and seats". Do not retry or work around it.
- Delivering in another LMS: export to SCORM or HTML from MEXTY.

## Follow up

`get_analytics_overview` and `get_learner_analytics` show completion and where learners struggle. Report what the numbers say and propose one change, such as splitting the module most people abandon.

## Sharing beyond the organisation

A course or path can also be posted on Mextribe for a public audience (`mextribe-community`), and a block that works as a game can be listed on EdVerse (`edverse-publish-and-earn`).
