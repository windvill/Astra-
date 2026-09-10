# Astra: Ruined Star

A browser action-survival game with an isometric view, automatic combat, level-up choices and persistent upgrades.

## Play

Open `outputs/astra-ruined-star/index.html` in a desktop browser. An internet connection is needed to load the pinned Three.js module. No build step is required.

- Move: WASD or arrow keys (works with Korean keyboard input).
- Choose an upgrade: 1, 2, 3.
- Pause: Escape.
- Permanent upgrades are stored in the browser's localStorage.

## Current Implementation

- Directional frame-based Astra character with walking and overhead attack poses.
- Articulated 3D monsters, experience pickups and six weapon types.
- Boss encounters at 5, 10 and 15 minutes.
- Generated image assets and runtime chroma-key compositing.

This is a work-in-progress prototype. The player uses 2.5D sprites, not a fully rigged model matching the concept art. Background architecture is decorative and has no collision. Visual polish, balance and full-run testing remain ongoing.

## Development

Game source and assets: `outputs/astra-ruined-star/`.
Checks and the atlas embedding script: `work/`.

With Node.js installed:

```sh
node work/embed-atlas.cjs
node work/movement-check.cjs
node work/rig-check.cjs
node work/monster-check.cjs
node work/motion-check.cjs
```

The checks cover input, projection, action timing, rig poses and sprite frame selection using test doubles. They do not replace browser rendering tests.

Art was generated using OpenAI image generation. Asset notes are kept alongside the images. No third-party game artwork is bundled. Three.js is loaded from jsDelivr at version 0.180.0.
