# GRANNY'S HOUSE

A complete single-file Three.js first-person horror game inspired by *Granny*. Everything — engine setup, procedural textures, enemy AI, WebAudio sound design, UI — lives in `index.html` with the only dependency being Three.js loaded from a CDN.

## Play

Open `index.html` in any modern browser (or serve it, e.g. `python3 -m http.server`, and visit `http://localhost:8000`). Pick a difficulty and click to lock the mouse.

## Goal

You're trapped in Granny's house. Find the **4 items** hidden in randomized spots — Hammer, Cutting Pliers, Screwdriver, and Master Key — and use them on the front door to escape. Every time she catches you, you lose a day. Get caught on **Day 5** and it's game over.

## Controls

| Key | Action |
|---|---|
| WASD | Move |
| Mouse | Look |
| Shift | Run (loud!) |
| C | Crouch (quiet, harder to see) |
| F | Flashlight (she can spot the beam) |
| E | Pick up items / hide in wardrobes / use the front door |

## Granny AI

She patrols the house on a waypoint graph. She **hears** noise (running, prying planks, slamming wardrobe doors) and comes to investigate. She **sees** you with a line-of-sight raycast and a view cone, then chases with pathfinding and a memory of where you were. Hide in wardrobes — but if she watches you climb in, she'll pull you right back out.

## Difficulty

- **Very Easy** — slow Granny, glowing item hints, forgiving senses
- **Easy** — slow Granny, hints, short chase memory
- **Normal** — the intended experience
- **Hard** — fast, sharp ears, long memory
- **Extreme** — very fast, 360° instant detection on sight, hears a pin drop

## Features

- Full first-person controller: sprint, crouch, head-bob, collision with walls and furniture
- Five-room house with procedural canvas textures, flickering bulbs, and a shadow-casting flashlight
- Randomized item spawns from 15 locations each run; progress persists across days
- Front door escape sequence: pry planks → cut padlock → unscrew plate → master key
- Fully procedural WebAudio: ambient drone, proximity heartbeat, footsteps, chase sting, and a layered jumpscare scream — no audio files
- Canvas-drawn jumpscare face, day-transition cards, win/lose endings
