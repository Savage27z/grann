# GRANNY'S HOUSE

A complete single-file Three.js first-person horror game inspired by *Granny*. Everything — engine setup, procedural textures, enemy AI, WebAudio sound design, UI — lives in `index.html` with the only dependency being Three.js loaded from a CDN.

## Play

Open `index.html` in any modern browser (or serve it, e.g. `python3 -m http.server`, and visit `http://localhost:8000`). Pick a difficulty and click to lock the mouse.

## Goal

You're trapped in Granny's **two-storey** house. Find the **4 items** hidden in randomized spots across both floors — Hammer, Cutting Pliers, Screwdriver, and Master Key — and use them on the front door to escape. The staircase is in the storage room. Every time she catches you, you lose a day. Get caught on **Day 5** and it's game over.

## Controls

| Key | Action |
|---|---|
| WASD | Move |
| Mouse | Look |
| Shift | Run (loud!) |
| C | Crouch (quiet, harder to see) |
| F | Flashlight (she can spot the beam) |
| E | Pick up items / hide in wardrobes / use the front door |

### Mobile / touch

Works on phones and tablets: a virtual joystick (bottom left) moves you, dragging anywhere on the right side of the screen looks around, and on-screen buttons handle RUN (hold), CROUCH (toggle), LIGHT (flashlight), and E (interact). Touch controls appear automatically on touch devices.

## Granny AI

She patrols both storeys of the house on a waypoint graph and uses the staircase like you do. She **hears** noise (running, prying planks, slamming wardrobe doors) and comes to investigate. She **sees** you with a line-of-sight raycast and a view cone, then chases with pathfinding and a memory of where you were. Hide in wardrobes — but if she watches you climb in, she'll pull you right back out.

## Difficulty

- **Very Easy** — slow Granny, glowing item hints, forgiving senses
- **Easy** — slow Granny, hints, short chase memory
- **Normal** — the intended experience
- **Hard** — fast, sharp ears, long memory
- **Extreme** — very fast, 360° instant detection on sight, hears a pin drop

## Features

- Full first-person controller: sprint, crouch, head-bob, collision with walls and furniture
- Two-storey, nine-room house with a working staircase, procedural canvas textures, flickering bulbs, and a shadow-casting flashlight
- Landing page → difficulty select → play; five wardrobes to hide in across both floors
- Randomized item spawns from 26 locations each run (always split across both storeys); progress persists across days
- Front door escape sequence: pry planks → cut padlock → unscrew plate → master key
- Fully procedural WebAudio: ambient drone, proximity heartbeat, footsteps, chase sting, and a layered jumpscare scream — no audio files
- Canvas-drawn jumpscare face, day-transition cards, win/lose endings
