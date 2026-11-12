---
name: edverse-game-performance
description: Makes a 3D browser learning game run smoothly on a school tablet or a mid-range phone, with three.js on WebGL or WebGPU. Use when an EdVerse or web game stutters, loads slowly, heats the device, crashes on mobile, or when planning a 3D game and deciding polygon, texture and draw-call budgets, or whether to use WebGPU and TSL.
---

# Game performance for the browser

The children who play EdVerse games are often on a shared tablet or an older phone. A game that only runs well on the developer's laptop fails the "responsive on every device" requirement.

## Measure before changing anything

1. Reproduce on the weakest device the listing claims: a phone, in landscape and portrait.
2. Read `renderer.info` (draw calls, triangles, textures, geometries) and frame time. In an EdVerse scene game also read `read_logs`.
3. Decide where the time goes: CPU (many draw calls, game logic, physics, garbage collection) or GPU (pixels, overdraw, heavy shaders, shadows). Lower the resolution: if the frame rate jumps, it is the GPU.
4. Change one thing, measure again.

## Budgets to start from

| Thing | Budget for a phone |
|---|---|
| One model | Under about 20k triangles and 5 MB (the EdVerse guide's limit) |
| Draw calls on screen | Low hundreds |
| Pixel ratio | Cap it: `Math.min(devicePixelRatio, 2)`, lower on weak devices |
| Shadows | One shadow-casting light, a small map, or baked |
| Textures | Power-of-two, 1024 or less for props, compressed (KTX2) when the loader supports it |
| First load | Playable in a few seconds on mobile data; load the rest while playing |

## What usually fixes it

- **Too many draw calls**: instance repeated objects (`InstancedMesh`), merge static geometry, share materials. In a scene game, use the editor's components and duplicates for repetition.
- **Too many pixels**: cap the pixel ratio, drop full-screen post-processing on phones, avoid large transparent layers.
- **Heavy models**: decimate in Blender, remove hidden faces, compress with Draco or Meshopt, load models from URLs in props and never bundle a `.glb` in the code.
- **Stutter every few seconds**: allocations in the frame loop. Reuse vectors and arrays, pool bullets and particles.
- **Memory growing until a crash**: dispose geometries, materials and textures when a level unloads.
- **Slow start**: show the first screen, call `mexty.ready()`, then load the rest.
- **Physics**: fixed time step, simple colliders, sleep what does not move.

## WebGPU

- Not every device a child uses has WebGPU. Ship a path that works without it. three.js `WebGPURenderer` (imported from `three/webgpu`) falls back to WebGL 2 by itself; test both paths, since the fallback is where the weak devices are.
- Initialise asynchronously before the first frame, and handle the device being lost.
- Materials and effects for it are written in TSL (node materials), not raw GLSL strings. Old `ShaderMaterial` code has to be ported.
- Use it when it buys something: many instances, compute-driven particles, heavier scenes on desktop. For a small game, WebGL is enough.
- For the renderer, TSL node materials, compute shaders, post-processing and device loss in detail, read `third-party/webgpu-threejs-tsl/SKILL.md` in this repository.
- The API moves quickly. Read the current three.js documentation for the version in `package.json` before writing renderer code, and do not trust remembered signatures.

## In an EdVerse scene game

The world is drawn by `<SceneCanvas>`. Do not replace its renderer or edit `src/edverse-scene/*`. Read `get_3d_guide` (topic `scene-games`) for what the scene supports, keep the world in the scene, and spend your optimisation effort on asset weight, instance counts and the logic in `src/block.tsx`.

## Going deeper

`third-party/gamedev/` holds engine-neutral skills that pair with this one: `performance-optimization`, `threejs-scene-setup`, `threejs-gltf-loading`, `threejs-materials-lighting`, `camera-systems`, `input-systems`, `save-systems`. Read the one that matches the problem. In an EdVerse scene game the EdVerse guide wins wherever the two disagree.

## Done means

The game holds a steady frame rate through a full round on a phone, in both orientations, and the second round is as smooth as the first.
