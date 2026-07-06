# GRANNY'S HOUSE

A complete single-file Three.js first-person horror game inspired by *Granny*. Everything — engine setup, procedural textures, enemy AI, WebAudio sound design, UI — lives in `index.html` with the only dependency being Three.js loaded from a CDN.

## Play

Open `index.html` in any modern browser (or serve it, e.g. `python3 -m http.server`, and visit `http://localhost:8000`). Hit ENTER GAME, pick a difficulty, and click to lock the mouse.

## Multiplayer (2–4 player co-op)

Escape together over peer-to-peer WebRTC (PeerJS — no game server needed, works on static hosting like Vercel):

- **HOST CO-OP** — pick the difficulty, get a 4-letter room code, and share it. Press START when everyone's in.
- **JOIN CO-OP** — type the room code and wait in the lobby.

How co-op plays:

- Everyone hunts items into a **shared team inventory**; anyone can strip a door lock or start the car, and **one player escaping wins it for the whole team**.
- The host simulates Granny; she hears and chases **whoever** is closest/loudest, and the HUD tells you who she's after.
- When a player is caught, only they get jumpscared and dragged back to the bedroom — but the **whole team loses the day**. Day 5 still ends it for everyone.
- Other players appear as colored avatars with name tags; you'll see their flashlights sweep the dark.
- The house was widened to a 28×20 m footprint (from 20×16) on both storeys to give a full lobby room to spread out.

## Goal

You're trapped in Granny's **two-storey** house, and there are **two ways out**:

1. **The front door** — find the Hammer, Cutting Pliers, Screwdriver, and Master Key, and strip its four locks.
2. **Granny's car** — find the Car Key and Gas Can and take the back door in the kitchen.

All six items spawn in randomized spots split across both floors (the staircase is in the storage room). Every time she catches you, you lose a day. Get caught on **Day 5** and it's game over.

## Controls

| Key | Action |
|---|---|
| WASD | Move |
| Mouse | Look |
| Shift | Run (loud!) |
| C | Crouch (quiet, harder to see) |
| F | Flashlight (she can spot the beam) |
| E | Pick up items / hide / use doors |
| Q | Fire the tranq dart |

### Mobile / touch

Works on phones and tablets: a virtual joystick (bottom left) moves you, dragging anywhere on the right side of the screen looks around, and on-screen buttons handle RUN (hold), CROUCH (toggle), LIGHT, DART, and E (interact). Touch controls appear automatically on touch devices.

## Granny AI

She patrols both storeys on a waypoint graph and uses the staircase like you do. She **hears** noise (running, shattering vases, creaky boards — muffled through the floor) and comes to investigate. She **sees** you with a line-of-sight raycast and a view cone, then chases with pathfinding and a memory of where you were. And when she loses you… on higher difficulties she sometimes **ambushes**: standing dead silent near where she last saw you, senses sharpened, waiting.

## Hazards & tools

- **Tranq dart** — one spawns somewhere in the house every day. Aim at her and press Q to knock her out cold (45s on Very Easy down to 10s on Extreme). One shot; misses are wasted.
- **Creaky floorboards** — darker patches of floor that groan loudly when crossed at speed. Crouch over them.
- **Vases** — brush against one and it shatters. She *will* hear that.
- **Bear traps** — on Normal and above she scatters them each day. Step in one and you're stuck for a few agonizing seconds while it makes a racket.
- **Hiding** — five wardrobes across both floors, plus you can crawl **under the beds** and watch her feet walk past. If she sees you go in, she'll drag you right back out.

## Difficulty

- **Very Easy** — slow Granny, glowing item hints, forgiving senses, no traps, long stuns
- **Easy** — slow Granny, hints, short chase memory
- **Normal** — the intended experience; bear traps appear
- **Hard** — fast, sharp ears, long memory, frequent ambushes
- **Extreme** — very fast, 360° instant detection on sight, hears a pin drop, 5 traps, 10-second stuns

## Features

- Two-storey, nine-room, 28×20 m house with a working staircase, procedural canvas textures, flickering bulbs, and a shadow-casting flashlight
- **2–4 player online co-op** via PeerJS: room codes, lobby, host-authoritative Granny, shared inventory, synced items/traps/vases/doors, player avatars with flashlights
- Landing page ("by savage") → single player or host/join co-op → difficulty select → play
- Two escape routes with separate item sets; randomized spawns from 26 locations, always split across both storeys; progress persists across days
- Fully procedural WebAudio: ambient drone, proximity heartbeat, footsteps, creaks, shattering glass, trap snaps, dart shots, engine start, chase sting, and a layered jumpscare scream — no audio files
- Canvas-drawn jumpscare face, day-transition cards, win/lose endings with your escape time
- Best escape day saved per difficulty (localStorage) and shown on the menu; volume and look-speed settings that persist
