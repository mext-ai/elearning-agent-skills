---
name: learning-game-design
description: Designs a learning game so that the play is the practice, before any code is written. Use when someone has an idea for an educational game, asks how to make a subject fun, wants a game design document or a core loop for a learning game, is unsure which genre or mechanic fits a skill, or has a game that is fun but teaches little, or teaches but is dull.
---

# Designing a learning game

Do this before building. A weak design cannot be fixed with polish.

## 1. The skill, exactly

One sentence: "The player practises ___ by ___." If the second blank is "answering questions", keep working.

Then the age tile (4–6, 7–9, 10–12, 13–15, 16–18), because it decides reading load, session length and how failure is handled.

## 2. The verb test

Write the verbs of the skill and the verbs of the game. They should be the same verbs.

| Skill | Verbs of the skill | A game with the same verbs |
|---|---|---|
| Fractions | compare, split, combine | Cut and pour ingredients to fill an order |
| Refraction | aim, predict the bend | Fire a beam through water to hit a target |
| Coordinates | locate, name a position | Find ships on a grid by calling squares |
| Telling time | read, set a clock | Turn the hands to the time someone asks for |
| Loops in code | repeat, shorten | Guide a robot with fewer blocks |

If the game's verbs are "run, jump, shoot" and the skill's are "compare, split", the learning is bolted on. Players will learn to run, jump and shoot.

## 3. The loop

Each loop of a few seconds to a minute: see a situation, decide using the skill, act, see what happened, try again. Check:

- **The decision needs the skill.** Guessing should lose to thinking.
- **The world answers.** A wrong beam shows where the light went. That is better feedback than "Wrong!".
- **A miss costs little.** Time, not lives, and never shame.
- **It grows.** New cases, not just faster ones.

## 4. Difficulty

Teach, then test, then combine. One new idea at a time, first in a safe case. Keep the player succeeding most of the time. If the skill has levels in school (halves before thirds), follow them.

Generated content must stay correct and answerable for every seed.

## 5. Reward

Reward understanding: shorter solutions, a mastered skill, a new place to explore. Avoid streak pressure, countdown anxiety for young children, and anything that nudges a child to keep playing or to pay.

## 6. A one-page design

```
Title · ages · subject · languages
The skill: the player practises ___ by ___
The loop: see / decide / act / result
Levels: what each adds
Wrong answer: what happens
Session: length, where it ends
Content: what is in props (questions, levels, words)
Art and sound: three reference words
Not in version 1: ...
```

Cut until version 1 is one loop done well. Check the store for the idea first (`search_edverse_store`).

## Go deeper

Genre playbooks and craft skills are in `third-party/gamedev/` (`puzzle`, `platformer`, `card-game`, `rpg`, `fps-shooter`, `game-feel`, `level-design`, `prototype-fast`). They are written for games in general: where they suggest lives, timers or losing, the rules above for children come first.

Then build with `homework-to-game`, and check with `edverse-game-qa`.
