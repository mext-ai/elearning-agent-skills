---
name: edverse-publish-and-earn
description: Lists an EdVerse game on the store, sets its price, and runs it after launch with the Suggestion box and the stats; and earns by improving other people's games that are open for collaboration, by hand or on an automatic routine. Use when someone wants to publish, sell or monetise a learning game, asks how creators get paid, wants to earn from their AI subscription by making or improving games, asks about free, fixed price, pay what you want or Included pricing, wants to read, answer or act on players' suggestions, wants to contribute to collaborative games or propose features to someone else's game, or wants an agent routine that does this regularly.
---

# Publish and earn on EdVerse

Making games on EdVerse is free. The MCP tools spend no credits, so the creator's own AI subscription is the only cost of building.

## Before listing

The game passes `edverse-game-qa`. Then set the listing:

- `update_game_listing`: ages (one or more neighbouring tiles), up to 5 subjects it really teaches, languages and default language, orientation, price.
- `set_game_listing_media`: square 800×800, landscape 1280×720, gameplay video, 1 to 8 screenshots. Upload each file to the library first.

## The four price options

Read the bounds from `get_edverse_game_guide` (`listing.storeOptions`, `listing.priceEurCents`).

| Option | Who plays | When to choose it |
|---|---|---|
| Free | Anyone | A first game, a game for your class, building an audience |
| Fixed price | Whoever buys it once | A complete game with hours of content |
| Pay what you want | Whoever pays at least your minimum | You want reach and let fans pay more |
| ★ Included | Families and schools with a learner seat; paid from the learner pool by minutes played | A game children come back to. MEXTY staff approve the request |

★ Included can be added on top of fixed or pay what you want: seat holders play it, everyone else buys it.

On a sale, the creator keeps 80% of the price after the card fee. The Studio's Sell dialog shows the exact amount for a given price; quote that, not your own arithmetic.

A paid option needs payouts set up in the Studio. `get_seller_status` says what is missing. You cannot set up payouts or tax details: give the person the Studio link.

Never promise an income. Show what the tools return: `get_earnings` for the balance, sales and pool line, `get_game_stats` and `get_studio_overview` for players and finishes.

## Submit

1. The author passes the game test in the Studio.
2. `get_game_review` returns the store licence terms. Show the summary. Call `submit_game_for_review` with `licenceTermsAcceptedByUser: true` only after the person said yes to submitting.
3. If it comes back, go to `edverse-game-qa`.

A live game keeps playing its approved version. New builds, new content and price changes reach the store after their own review.

## Run it: the Suggestion box

Every game has a Suggestion box next to Play. Players propose ideas; the developer answers. It is the game's public roadmap and the cheapest way to know what to build next.

As the developer:

1. `list_game_suggestions({ blockId, status: "submitted" })`: the new ones, oldest first.
2. Decide each with `update_game_suggestion`: approved, declined, building, shipped. Write a short, kind public reply. Children wrote these.
3. Group similar ideas. Build the ones that add practice of the skill, not only decoration.
4. When a build ships an idea, mark it shipped. The player who sent it sees it happened.

As a player or a teacher with an idea for someone else's game: read `get_game_suggestion_box` so you do not repeat one, then `submit_game_suggestion` (a title and a description; a few a day per game).

Suggestions that are unkind or contain personal information are filtered. Decline them without quoting them.

## A weekly loop for one person

| Day | Do |
|---|---|
| Monday | `get_studio_overview`: which game lost players, which one do children not finish |
| Tuesday | Answer the Suggestion box of every live game |
| Midweek | Build one accepted idea, or fix the level where players stop |
| Friday | Submit the update with `changes`, post it on Mextribe, share the kit (`instagram-showcase`) |

## Earn by improving other people's games

A game's owner can open it for collaboration. Any signed-in maker (an adult account, not a child's) can then read the game and propose changes in a draft of their own. Nothing reaches players until the owner merges it.

**How the money works.** A game's ★ Included earnings, paid from the learner pool by the minutes children with a learner seat play it, are split each month between the people who built it, by contribution points: the 3D-world work and the lines of code of theirs still in the game. When the owner merges a draft you proposed, you join the game as a contributor and your merged work counts from then on. The owner sees the split and can adjust it until the month's statement is written. One-off sales stay with the owner, and a game that earns nothing from the pool pays nothing to anyone. Say this plainly; never promise an amount. `get_earnings` shows what has actually been paid.

**Find a game and an idea.**

1. `list_collaborative_games({ query })`: the games open for collaboration, with the owner's note on what help they want.
2. `get_collaborative_game({ game_id })`: its note, its Suggestion box summary and how to propose.
3. Read the Suggestion box (`get_game_suggestion_box`). An approved idea nobody built yet is the best start: players asked for it and the owner agreed. Without one, propose something the game clearly lacks: a level for a skill it skips, an accessibility fix, a bug players hit, a translation.
4. Read the game before changing it (`get_scene`, `read_game_files`, `list_game_scenes`). Keep the owner's style, age range and learning goal.

**Propose it.**

1. `create_draft({ game_id })`. You work only in your own drafts; the main version is read-only for you. A person can have 3 open drafts per game.
2. Build in the draft (the scene and file tools take `draft_id`; your writes go to your draft automatically). Keep one idea per draft so the owner can say yes to it alone.
3. Check it still passes `edverse-game-qa` for what you touched.
4. `get_draft_diff`, then `request_review` with a short note: what it adds, which suggestion it answers, how to try it. The owner gets an email.
5. Follow up with `list_drafts`. Answer change requests in the same draft. If main moved, `update_draft_from_main` first.

Do not create drafts on many games at once to see what sticks. Owners decide what they merge, and spam gets your drafts closed.

**As the owner, opening your game.** Turn on "Open for collaboration" from the game's Share dialog in the Studio and write a one-line note on the help you want. Outsiders can then read your game's scenes, code and assets and propose drafts; they cannot change main, your listing, your price or your people. Review with `get_draft_diff`, merge with `merge_draft`. Manage your team with `list_game_collaborators`, `invite_game_collaborators`, `set_game_collaborator_role` (maintainer or contributor) and `remove_game_collaborator`.

## A routine that runs on its own

If the AI app can run scheduled tasks (Claude routines, ChatGPT tasks, a cron job calling an agent), set one up once and let it work. A weekly routine:

1. `list_collaborative_games`, then `get_collaborative_game` on the few that fit the person's skills and subjects.
2. For each, read the Suggestion box and pick at most one idea: an approved suggestion first, else a clear gap or bug.
3. Skip a game where the person already has a draft waiting for review.
4. Build the idea in a new draft, check it, and `request_review` with a note.
5. Check last week's drafts with `list_drafts`: answer change requests, catch up with main, close drafts the owner declined.
6. For their own games, run the Suggestion box loop above and answer new suggestions.
7. Write a short report: what was proposed, what was merged, and what `get_earnings` shows.

Guardrails for a routine: one idea per draft, one draft per game per week, never `merge_draft` on someone else's game, never reply to children's suggestions without a human reading the reply first, and stop and ask the person when an idea would change a game's price, age range or learning goal.

Mextribe can turn the work into followers: post the games you shipped or improved with `mextribe-community`.

## More content without a new game

`save_game_props` saves another variant of the same game (another grade, another language, another topic). `propose_game_variant` sends it to review with its own title and listing. One good mechanic can carry many homework sets.
