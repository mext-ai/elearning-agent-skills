---
name: multiplayer-and-saves
description: Adds saved progress, leaderboards, achievements and real-time multiplayer to an EdVerse game or a MEXTY activity. Use when a game should remember a player's progress, when someone asks for a leaderboard, badges or achievements, a co-op or versus mode, family or class play, a live race, a shared board or whiteboard, or when saves are lost, scores do not appear, or a multiplayer game does not connect.
---

# Saves, leaderboards and multiplayer

Read the current rules from the tools before writing code: `get_edverse_game_guide` (its `sdk` section) for games, and the MEXTY server's block instructions for multiplayer. Packages and versions change; use what they say, not what you remember.

## Which one

| The player should | Use | Lives |
|---|---|---|
| Come back and find their progress | Cloud save | Per child, private, across devices |
| Compare scores with family, class or everyone | Leaderboard | Per game board |
| Earn a badge | Achievement | Declared per game |
| Play with others right now | Multiplayer shared state | Only while someone is in the room |

They combine: a co-op round is multiplayer; the stars it earns are a save.

## Saves, leaderboards, achievements: `@mexty/sdk`

Add the package to the game's `package.json` at the version the guide gives, keeping every existing dependency, and include `package.json` in the write.

- Call `mexty.ready()` once the first screen is drawn.
- **Guests play normally.** Their saves stay on the device; scores and achievements do nothing. Never block play or build a sign-in screen.
- Save small, meaningful state: level, stars, settings. Not the whole world. There are limits per save and per player; the guide lists them.
- Declare achievement ids and shared collections yourself with `update_game_data_settings` before using them. Until then, unlocks do nothing.
- Leaderboards: submit at the end of a round, and choose the scope (family, class, everyone) to suit the age. For young children, family and class are kinder than everyone.
- Pause when `mexty.paused` is true, and respect `mexty.muted`.
- Report learning progress through one channel, the SDK or the tracker, not both for the same answer.

Test: play as a guest, play signed in, leave and come back, and play on a second device.

## Multiplayer: shared state

Real-time play uses a shared state that every participant reads and writes; the platform provides the connection, sign-in and room. Follow the server's current instructions for the package and version.

- The state is plain JSON: objects, arrays, numbers, strings. No dates, maps or class instances.
- Give it an initial state; it only fills keys the room does not have yet.
- Each player has an id; keep per-player data under it so players do not overwrite each other.
- Show a simple waiting state until connected, and handle reconnecting.
- **It is not saved.** When the room empties, the state is gone. Anything that must last goes to a cloud save or a database.
- Do not configure rooms or connections yourself.

Design for children:

- No free-text chat, no names beyond the nickname the platform shows.
- Preset reactions (emotes, icons) in place of messages.
- A Report button on other players, using the game's report message, and hide the reported player at once in that child's view.
- A player who leaves must not break the round for the others. Offer a bot or let the round continue.
- Co-op is easier to keep kind than versus. If there is a winner, celebrate the round, not the ranking.

## When it does not work

| Symptom | Look at |
|---|---|
| Saves vanish | Playing as a guest; the save key changed; saved before `ready()` |
| Score not on the board | Guest; board name differs between submit and read; daily submit limit |
| Achievement never unlocks | Id not declared in the game's data settings |
| Players do not see each other | Old multiplayer package version; state not plain JSON; not waiting for the connection |
| State resets | Everyone left the room; that is how it works |

`read_logs` shows the game's errors. Then check the result on a phone (`edverse-game-qa`).
