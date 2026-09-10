# Astra: Ruined Star

## Release Candidate 1

Character selection now includes Astra (balanced sword), Seir (fast sword/bolt caster)
and Var (slow heavy sword guardian). Choice persists locally and changes the gameplay
rig, starting weapons and stats. Their portraits are existing concept art; gameplay
uses the sprite/3D rig representations. A first-run sanctuary tutorial covers reaching
a marker, defeating a harmless target, collecting experience and choosing a blessing.
It can be replayed or skipped, grants no permanent currency, and resets the expedition
before normal play. The title menu also contains three story chapters and expanded
credits.

Desktop browser build for keyboard and mouse. The title screen, sanctuary upgrades,
settings, pause menu and expedition results now share a consistent visual design.
Sword attacks follow the cursor automatically. WASD or arrows move the character;
Escape pauses, and 1/2/3 selects a level-up blessing. Settings include audio volume,
mute, reduced effects and fullscreen. Progress is stored locally in this browser,
not in a cloud account. Narrow-screen layouts are supported, but touch movement is
not implemented.

RC1 fixes corrupted save loading, repeated start/reward handling, queued level-ups,
maxed-build choices and final-boss victory detection. It adds a boss health meter,
kill count, best survival record, retry and retreat flows, faster opening encounters,
and bounded enemy/effect counts. Generated art and procedural rigs remain prototype
assets; this is a playable release candidate, not a claim of commercial-release QA.

Run `node work/release-check.cjs` for lifecycle and combat checks.

A browser action-survival game with an isometric view, automatic combat, level-up choices and persistent upgrades.

## Play

The repository root `index.html` is the deployable game bundle. Import this repository into Vercel with the Other framework preset; `vercel.json` serves the root directory without a build step. An internet connection is needed to load the pinned Three.js module.

For editable source, extract `astra-upload.zip` and open `outputs/astra-ruined-star/index.html` in a desktop browser. The archive includes source files, images and checks. The root bundle embeds local scripts and runtime images for portable hosting.

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
