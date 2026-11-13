---
name: mexty-start
description: Entry point for anything e-learning with MEXTY, EdVerse or Mextribe. Use when someone wants to make a learning game, turn homework or a lesson into something playable, build a course or training program, earn money from educational content, or run a learning community, and it is not yet clear which product, plan or skill fits. Works out who the person is, picks the free route first, and hands over to the right skill.
---

# Start here

MEXTY is three products that share one account:

| Product | What it is | MCP server | Cost to use the MCP |
|---|---|---|---|
| **EdVerse** | A store of learning games for ages 4 to 18, with a Studio and a 3D editor to make them | `https://mcp.mexty.ai/mcp/edverse` | Free |
| **Mextribe** | A social network for learning: creators post courses, activities, videos and games; learners follow for free or subscribe to paid plans | `https://mcp.mexty.ai/mcp/mextribe` | Free |
| **MEXTY** | AI authoring (courses, interactive blocks, evaluations, learning paths) and an LMS for organisations | `https://mcp.mexty.ai/mcp/mexty` | Authoring, Authoring + LMS or Enterprise plan |

Install links for every AI app are at https://mexty.ai/connect. The sign-in happens inside the AI app.

The MCP tools themselves spend no MEXTY credits: your own AI subscription supplies the intelligence. The only tools that spend credits are the media generators (images, audio, 3D models, transcription). See `free-creative-toolkit` for the free way to do each of those.

## Step 1: find out who you are talking to

Ask at most two questions, and only what the request has not already answered: what do you want to end up with, and who is it for?

| The person is | They usually want | Go to |
|---|---|---|
| A student | To turn homework or revision into a game | `homework-to-game` |
| A parent | A game that helps their child with one topic | `homework-to-game` |
| A parent or guardian | To know what their child learned and what to practise | `track-kid-progress` |
| A teacher | A game or activity for a class, sometimes sold to other teachers | `homework-to-game`, then `edverse-publish-and-earn` |
| A game creator | To build, polish and sell learning games | `edverse-game-performance`, `edverse-game-qa`, `edverse-publish-and-earn` |
| Someone with an AI subscription who wants income | Games on the store, a paid community, or both | `edverse-publish-and-earn`, `mextribe-community` |
| A creator with an audience | Posts, paid plans, comments, insights | `mextribe-community` |
| A school, university or company | Courses, programs, evaluations, learners and seats | `mexty-courses-for-teams` |
| A compliance, HR or product lead | Training that follows a policy or a product, kept current, with proof of who was trained | `keep-training-current` |
| Anyone with learners or players | A dashboard that answers one question about their learning | `analytics-dashboards` |
| A company onboarding people | A path for a role, from day 1 to day 90 | `onboarding-path` |
| A company with a policy to train on | One compliance course and its check | `compliance-course` |
| A company or a school teaching AI literacy | Staff by role, or pupils by age | `ai-literacy-at-work`, `ai-literacy-curriculum` |
| A sales, support or partner lead | Product knowledge, pitch and objection practice | `sales-enablement` |
| A teacher or lecturer with a syllabus | A learning path with a course per outcome | `curriculum-to-learning-path` |
| Anyone writing a test or an exam | Questions, points and a pass mark | `assessment-design` |
| A parent choosing games | Games by age, subject and language; screen-time settings | `pick-games-for-my-kid` |
| A game maker with an idea | The design before the code | `learning-game-design` |
| A game maker adding saves, leaderboards or co-op | The SDK and shared state, safely for children | `multiplayer-and-saves` |
| Two or more people, a class, a team | To build the same course or game together, review each other, merge | `build-together` |
| Anyone with something finished | To show it on Instagram or TikTok | `instagram-showcase` |

A person can be several of these. A teacher who builds a game for their class, lists it on EdVerse, posts it on Mextribe and shares the Story card is using four skills in a row: say which step you are on.

A parent who wants to follow their child, not build anything: go to `track-kid-progress`. It reads the EdVerse Learners dashboard with them and writes the report.

## Step 2: check what is connected

Look at the tools you actually have. If the server a route needs is missing, say which one and give https://mexty.ai/connect. Never pretend a tool ran.

- EdVerse tools present: `get_edverse_game_guide` is the first call of any game session.
- Mextribe tools present: `get_mextribe_guide`, then `get_tribe_profile`.
- MEXTY tools present: list before you write (`list_my_courses`, `list_my_blocks`, `list_my_programs`).
- A MEXTY tool refuses with a plan error: the person is on Free or LMS only. Say what the plan includes and offer the EdVerse or Mextribe route if it fits what they want.

## Step 3: free first

Before any tool that spends credits, look for the free way:

1. Reuse: a store template (`list_game_templates`, `list_store_game_templates`), the asset catalogue (`search_asset_catalogue`), stock media (`search_media`).
2. Make it on the person's machine: Blender headless for 3D, Whisper for transcription, the Opuscar film styles for video.
3. Generate with credits only when 1 and 2 cannot give what is needed, and say what it will cost first.

## Rules that hold everywhere

- Games on EdVerse are for children. Nothing scary, no links out, no chat, no request for personal information.
- You cannot take the Studio game test, accept licence terms, or set up payouts. The person does those.
- Anything that sets a price, publishes, or sends a message to followers needs the person's explicit yes, with the details shown.
- Never invent an id, a URL or a number. Read it from a tool.
