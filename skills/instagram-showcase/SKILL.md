---
name: instagram-showcase
description: Turns a finished learning game, course or Mextribe post into Instagram and TikTok content. Use when someone wants to promote, announce, share or show off what they made, asks for a Reel, a Story, a carousel, a caption or hashtags for an educational game or course, or wants a posting plan to grow an audience for their learning content.
---

# Show it on Instagram

What sells a learning game is ten seconds of someone playing it and getting it. Show the play, then say what it teaches.

## Gather what exists

- A game: `get_game` returns its listing media (square, landscape, gameplay video, screenshots). Use these; they already passed or will pass review.
- A Mextribe post: `get_share_kit` returns the link, a QR code, a Story card (1080×1920) and ready captions for Instagram and TikTok.
- Only use media the person owns. Another creator's game needs their agreement.

## Formats

| Format | Size | Make it from |
|---|---|---|
| Reel | 1080×1920, 15 to 30 s | The gameplay video, cropped or reframed to vertical |
| Story | 1080×1920 | The share kit's Story card, with the link sticker |
| Carousel | 1080×1350, 5 to 7 slides | Screenshots, one idea per slide |
| Feed post | 1080×1350 or square | The square thumbnail |

## Reel structure

1. **0 to 2 s: the hook.** The most surprising moment of play, with one line of text: the homework it replaces. "Fractions homework, but it's a roller coaster."
2. **2 to 15 s: the play.** One right answer and what it does in the game. One wrong answer and how kindly the game handles it.
3. **Last 3 s: what and where.** The skill, the ages, "free on EdVerse" if it is, and where the link is.

Add captions on screen; most people watch without sound. Cut and reframe with ffmpeg. For an animated explainer or promo, use an Opuscar film style (`free-creative-toolkit`).

## Three story angles

- **Play to learn**: a child plays, a skill is practised. For parents and teachers.
- **Build to learn**: a student turned their own homework into this game. For students.
- **Make and earn**: one person, one AI subscription, a game on the store and a community. For creators.

Pick one angle per post.

## Companion skills

For a motion graphics opener or promo, the bang-motion skill; for carousel slides and posters, canvas-design. Both are listed with their sources in `THIRD_PARTY.md` and are installed separately.

## Captions

- First line carries the whole point; the rest is cut off in the feed.
- Say the subject, the age range and the price honestly, as the listing does.
- One call to action: play it, follow, or make your own.
- A few specific hashtags (the subject, the grade, the kind of game) beat many general ones.
- Say that it was built with AI when it was.
- A film made in an Opuscar style carries its credit line in the caption (`free-creative-toolkit`).

## Rules

- No faces, names or voices of children without their parent's consent. Film hands and the screen.
- No promises about grades or income.
- Posting to Instagram is done by the person. Prepare the files and the text, and give them to the person to post.

## A two-week launch plan

| Day | Post |
|---|---|
| 1 | Reel: the hook and the play |
| 3 | Carousel: what it teaches, level by level |
| 5 | Story: how it was made, with the editor on screen |
| 8 | Reel: a suggestion from the Suggestion box, now in the game |
| 11 | Carousel: three other games worth playing on the same topic |
| 14 | Story: the numbers so far, and what comes next |
