---
name: mextribe-community
description: Runs a creator's learning community on Mextribe end to end, alone. Use when someone wants to post a course, activity, video or EdVerse game to followers, set up or price paid membership plans, answer or moderate comments, send an update or a poll, read follower, member and earnings insights, plan what to post next, or build an audience for their educational content.
---

# Run your learning community on Mextribe

Mextribe is MEXTY's social network for learning. Learners follow a creator for free and subscribe to the creator's paid plans for the rest. Using it and its MCP is free.

Read `get_mextribe_guide` once per session, then `get_tribe_profile`. If there is no profile, the person creates it once in the Mextribe app (it asks their date of birth and who their content is for). Give them the link the tool returns. Never guess a handle.

## Post

1. `list_postable_content`: their courses, learning paths, activities and EdVerse games. Never invent an id. For a video or image, upload it first.
2. `list_plans` and `list_series` to see the access options.
3. `create_post`. It is always a draft. Fill the caption, topics (`list_topics`), audience and access.
4. Show what will go live: title, audience, who can see it, price. Ask.
5. After an explicit yes: `publish_post` or `schedule_post`. A first post aimed at under-18s goes to MEXTY's review first; say so.
6. `get_share_kit`: link, QR code, Story card and ready captions. Offer it (see `instagram-showcase`).

## Plans and money

`create_plan`, `update_plan` and `archive_plan` need the person's explicit yes in the conversation, with the price shown. A price change applies to new members only. Read the share the creator keeps and the payout schedule from the guide and `get_payout_status`; do not quote them from memory.

A simple structure that works for one person:

| Tier | What members get |
|---|---|
| Free (followers) | One full piece a week, previews of the rest |
| One paid plan | Everything, plus a series that builds week after week |
| A second plan, later | Only when there is something distinct to put in it |

## Community

- `list_comments({ filter: "unanswered" })`, then `questions`, then `held`.
- Reply kindly and briefly, in the creator's voice. Never promise grades, refunds or personal contact.
- A held comment that asks to talk elsewhere or for personal details: do not reply. Hide it and tell the creator it should be reported.
- `send_tribe_update` sends a message or a poll to members or followers. It is one-way: Mextribe has no private messages. Ask before sending.

## Insights

- `get_insights`: followers, members, earnings, top posts, where members came from.
- `get_post_insights`: the funnel and where learners drop off in a lesson.
- `list_members`: learners under 18 show as a first name and an initial. Never try to identify them.

Use the drop-off point to decide what to fix or make next. A lesson most people leave at minute three needs a shorter opening, not a sequel.

## A weekly rhythm for one person

| When | Do |
|---|---|
| Start of week | Read insights; pick one thing to make from what worked |
| Midweek | Publish one free piece and one for members |
| Twice a week | Clear unanswered comments and questions |
| End of week | One update or poll to members; schedule next week's posts |

## Safety

Content must fit its declared age range. Never post or reply anything inappropriate for the audience, and never collect personal data about learners.
