---
name: free-creative-toolkit
description: Chooses the free or open-source way to make the media a course or a learning game needs before any paid generation. Use when a game or course needs 3D models, images, icons, voices, music, sound effects, subtitles, transcription or a promo or explainer video, when the person asks how to do it for free or without spending MEXTY credits, or before calling any MEXTY generation tool. Covers headless Blender, Whisper, the Opuscar film styles, stock media and the asset catalogue.
---

# Free creative toolkit

The MEXTY, EdVerse and Mextribe MCP tools are free to call, except media generation, which spends the person's MEXTY credits. Almost everything a game or course needs can be made without it.

Go down each ladder and stop at the first step that works.

| Need | 1. Reuse (free) | 2. Make on your machine (free) | 3. Generate (credits) |
|---|---|---|---|
| 3D models | `search_asset_catalogue`, the template's world | Blender headless, exported as `.glb` | `generate_3d_model_from_prompt`, `generate_3d_model_from_image` |
| Images, icons, video clips | `search_media` (stock photos, clips, icons) | Draw as SVG or render from the game | `generate_image` |
| Subtitles, transcription | An existing transcript | Whisper | `audio_to_srt`, `video_to_srt` |
| Voices | A recording by the author | An open-source text-to-speech model installed locally | `generate_audio` |
| Explainer or promo video | The game's own gameplay capture | An Opuscar film style, rendered locally | none needed |

Before step 3, say what it costs and why steps 1 and 2 were not enough.

## 3D with headless Blender

Needs Blender installed (`blender --version`) and a shell.

1. Write one Python script that builds every model with `bpy`: low-poly, in metres, origin at the base, one material per colour.
2. Run it with no window: `blender --background --factory-startup --python make_models.py`.
3. Export one `.glb` per model (`export_scene.gltf`, `export_format='GLB'`). Keep each under about 20k triangles and 5 MB.
4. Upload: `create_media_upload`, run the returned command, `complete_media_upload`.
5. Pass each URL as its own prop and load it at run time. Never bundle a `.glb` into the game's code.

`get_edverse_game_guide` has a working script under `models3d`. A script is exact and repeatable: change a number, run again, get the whole set in the same style. Models you made can be given to everyone with `contribute_asset_to_catalogue`.

No Blender, or an organic shape a script cannot reach: that is when generation is worth the credits.

## Transcription and subtitles with Whisper

Whisper is an open-source speech-to-text model that runs on the person's computer.

1. Extract the audio if the source is a video (ffmpeg).
2. Run Whisper and ask for SRT output. A small model is enough for clear speech; use a larger one for noise, accents or mixed languages.
3. Read the result. Correct names and subject terms: a wrong word in a lesson's subtitles is a content error.
4. Upload the `.srt` next to its video.

It also turns a recorded lesson into text you can build a course or a game's questions from.

## Video with the Opuscar film styles

MEXTY offers the film styles of the open-source Lemo-Opuscar library (chalkboard, watercolour, pixel RPG, data storytelling and more). Each is a film made entirely in code and rendered on the person's machine.

1. `propose_video_styles({ topic })` shows a few. Stop and let the person pick; do not choose for them.
2. `get_video_style({ slug })` returns the style's guide and the production steps. Follow them.
3. Render, then put the MP4 and its SRT in the person's library.
4. Credit the style wherever the film is described or posted: `Style: <Style name> from Lemo-Opuscar by Lemomo (github.com/lemomo-ai/lemo-opuscar), CC BY 4.0.` Do not burn a watermark into the film.

## Stock media and the catalogue

- `search_media` returns real hosted URLs. Call it once with every term you need. Never invent a media URL.
- `search_asset_catalogue` finds 3D assets other creators shared.
- Write down where each asset came from. The store review asks whether the author has the right to use everything in the game.

## Rights

Free to download is not the same as free to reuse. Use assets that are made by the author, licensed to them, or under a licence that allows reuse in a published, possibly paid, game, and keep the attribution the licence asks for.
