---
name: edverse-game-qa
description: Gets an EdVerse game ready to pass the store review and deals with a review that came back. Use before submitting a game, when the person asks whether a game is ready, good enough or valid, when a build misbehaves on a phone, when the Studio game test fails on a step, or when a reviewer sent a game back or rejected it. Checks the game against the 11 EdVerse Game Requirements, fixes what an AI can fix, and tells the person exactly what only they can test.
---

# EdVerse game QA

Every game is tested twice against the same 11 requirements: once by its author in the Studio game test, once by a MEXTY reviewer. Your job is to make both pass the first time.

You cannot take the game test. It is answered by the author while playing. Never say you tested the game: say what you checked in the code and what the person has to play.

## Read the state first

- `get_edverse_game_guide`: the current requirements (`requirements.items`). Use this list, not your memory of it.
- `get_game`: build, listing, media, `gameTest` progress, `visualCheck`.
- `get_game_review`: the reviewer's reasons, if it was sent back.
- `read_logs` and `get_game_build_status`: build and runtime errors.

## The 11 requirements, and what to check for each

| Key | Requirement | What you can check | What the author must play |
|---|---|---|---|
| EV-LOAD | Loads properly | Build is green, no console error, every asset URL resolves, `mexty.ready()` is called once the first screen shows | Open it: no blank screen |
| EV-DEVICES | Responsive on every device | Layout uses relative sizes and safe areas, touch controls exist, `orientation` is set if it only works one way | Desktop, tablet, phone, phone sideways |
| EV-COMPLETE | Playable to the end | A round ends and calls `complete`, replay works, saved progress loads, no placeholder text | A full round, twice |
| EV-CLEAR | Easy to understand | First screen says what to do in words right for the age; ages 4–6 need voice, not text | Would a child that age know what to do? |
| EV-LEARNING | Real learning | The skill is the main action, and it matches the listed subject | Is the learning in the play itself? |
| EV-ACCURATE | Correct content | Solve every question in the props yourself; check generated content stays answerable for every seed | Spot-check answers and feedback |
| EV-SAFE | Right for the ages | Nothing violent, scary or mocking; failing is met kindly; nothing pressures the child to keep playing or pay | Play to lose on purpose |
| EV-CONTAINED | Stays inside the game | No links out, ads, chat, sign-up, payment screen or tracker; never asks for a name, email, photo or location | Tap everything |
| EV-SOUND | Sound under control (if it has sound) | A mute control, respects `mexty.muted`, audio stops on close and on pause | Mute, then close |
| EV-LISTING | Honest listing | Title, description, thumbnails, subjects, ages and languages describe this game; every claim is true | Read the listing next to the game |
| EV-RIGHTS | Rights to everything | Every image, sound, model and text is made by the author, licensed, or free to reuse; note the source of each | Confirm it |

## Order of work

1. Fix what breaks loading or completion first. Nothing else matters until a round can be played to the end.
2. Check content accuracy by solving it, question by question, in every declared language.
3. Check the listing media are complete (`listingMedia.missing`): square 800×800, landscape 1280×720, a gameplay video, 1 to 8 screenshots.
4. Run the visual check and record it.
5. Write the person a short test plan: the steps only they can do, in the order the Studio asks them.

## When a review comes back

1. Quote the reviewer's reasons from `get_game_review` as they are written.
2. Fix each one, and look for the same fault elsewhere in the game.
3. The author re-takes the game test on the new build.
4. Resubmit with `submit_game_for_review`. For a game already live, `changes` must say what changed since the version the store plays.

## Common reasons a game is sent back

- A subject listed that the game does not really teach.
- Languages declared but props not filled in all of them.
- A phone in landscape cuts off the buttons.
- The round never calls `complete`, so plays never count as finished.
- A timer or a "you lose" screen that is too harsh for the youngest listed age.
- A model or a track whose licence nobody can name.
