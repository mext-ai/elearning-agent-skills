---
name: edverse-publish-and-earn
description: Lists an EdVerse game on the store, sets its price, and runs it after launch with the Suggestion box and the stats. Use when someone wants to publish, sell or monetise a learning game, asks how creators get paid, wants to earn from their AI subscription by making games, asks about free, fixed price, pay what you want or Included pricing, or wants to read, answer or act on players' suggestions for a game.
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

## More content without a new game

`save_game_props` saves another variant of the same game (another grade, another language, another topic). `propose_game_variant` sends it to review with its own title and listing. One good mechanic can carry many homework sets.
