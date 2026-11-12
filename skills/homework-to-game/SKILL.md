---
name: homework-to-game
description: Turns a homework sheet, a lesson, a revision list or a textbook chapter into a playable EdVerse learning game. Use when a student, parent or teacher shares an exercise, a photo of a worksheet, a vocabulary list, a chapter or a topic and asks for a game, a way to practise it, or something more fun than the worksheet. Covers reading the material, choosing a mechanic where playing is the practising, building from a template, and getting it ready for the store review.
---

# Homework to game

The idea: the child does the homework by playing. A right answer is a move in the game, never a quiz stuck on top of one.

Needs the EdVerse MCP (free). Read `get_edverse_game_guide` once before building.

## 1. Read the homework

From what the person gave you (text, photo, PDF, a topic), write down:

- **Subject and exact skill.** "Adding fractions with the same denominator", not "fractions".
- **Age.** It decides the age tile (4–6, 7–9, 10–12, 13–15, 16–18), the amount of text and whether instructions must be spoken.
- **The items.** Every question with its correct answer. Solve each one yourself. If the sheet has an answer key, check it; teachers' keys contain mistakes too.
- **Language.** Build in the homework's language. Add a second one only if asked.

If the homework is graded and due, say plainly that the game is for practising, and that handing in a game instead of the sheet is between them and the teacher.

## 2. Choose the mechanic

Pick the action that is the skill. One mechanic, done well.

| The homework asks the child to | A mechanic that is the skill |
|---|---|
| Recall facts fast (tables, capitals, vocabulary) | Race, runner or shooter where the right answer is the target or the gate |
| Compare or order (fractions, dates, sizes) | Sort, stack, balance scales, place on a number line |
| Follow a procedure (long division, conjugation, a method) | Build step by step: a recipe, a machine, a program |
| Read a map, a grid or a diagram | Explore a world and navigate by it |
| Understand a system (water cycle, circuits, a body) | Assemble it or run it and watch what changes |
| Learn words in another language | Listen and act: fetch, serve, point |

Check `search_edverse_store` for the topic and age first. If a good game already exists, say so; the person may only need to play it.

## 3. Build

1. `list_game_templates`, then `create_game` from the closest template (`runner`, `fps-arena`) or `blank`. Give the person the `editorUrl` so they can watch.
2. Put the content in props, never in the code: every question, answer, label and level is a typed prop, every learner-facing text a `LocalizedText` with only the languages the game ships.
3. Build the world with the scene tools and the logic in `src/block.tsx`. Follow the guide's rules exactly; do not edit `src/edverse-scene/*`.
4. Report learning through the tracker: `answerQuestion` for every answer, `complete(score, maxScore)` when a round ends. Without it the game never counts as finished and the parent sees no progress.
5. `get_game_build_status` until it builds, then the visual check.

Design choices that come from the review, so make them now:

- A wrong answer costs a little time and shows the right one. No lives lost for good, no shaming, no countdown pressure for ages 4 to 9.
- Ages 4 to 6: nothing to read. A voice and a pointing hand show each action.
- Works by touch, on a phone held either way, as well as with a keyboard.
- Sound can be muted and stops when the game closes.
- Ten homework questions make one short round. Shuffle the order, and generate fresh numbers when the skill allows it, so a second round is still practice.

## 4. Free assets

Use the template's world, `search_asset_catalogue` and `search_media` before generating anything. For 3D models, voices and subtitles see `free-creative-toolkit`.

## 5. Hand over

Give the person the play link from `get_game_play_link` and say what they must do themselves: play it, and take the game test in the Studio if they want it on the store. Then:

- Just for my child or my class: they can stop here and share the play link.
- On the store: go to `edverse-game-qa`, then `edverse-publish-and-earn`.
