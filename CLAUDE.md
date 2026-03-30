# Crawl of Cthulhu — Project Context

## What This Is
A Cthulhu Mythos-themed ASCII roguelike built as a **single HTML file** (index.html) — no build tools, no frameworks, no external dependencies. All game logic, rendering, and audio are self-contained in `<script>` tags using vanilla JS. The game runs in a browser.

## Design Philosophy
- **Survival horror roguelike**: The core tension is resource management (HP, SAN, ammo, torch fuel, inventory space). Running away should be a valid and often optimal strategy.
- **Lovecraftian atmosphere**: Fear of the unknown is a mechanic, not just flavor. The identification/bestiary system, the FOV limitations, the ambient event chains — all serve the theme.
- **Meaningful choices over busywork**: If a mechanic feels like "extra clicks" rather than a "real decision," it should be redesigned. Example: the identification system was iterated several times to avoid UI friction.
- **No over-engineering**: Keep solutions simple and focused. A single file is part of the charm. Magic numbers should be replaced with proportional values, but don't add abstraction for its own sake.

## Architecture Overview
- ~4000+ lines of JS in a single `index.html`
- ASCII rendering via DOM spans with inline styles
- Procedural dungeon generation with room placement, L-shaped corridors, flood-fill validation
- Raycasting FOV with 4-directional facing and 120° (or 150° for Detective) view cone
- Turn-based game loop: player action → monster AI → regen/decay ticks → render
- Web Audio API for procedural ambient audio (drone + sequencer + SFX)
- localStorage for high score persistence

## Key Systems
- **Professions**: Soldier (combat), Doctor (sustain), Detective (awareness) — each with unique stats, loadouts, and passives
- **Inventory**: 10 shared slots for equipment + carried items. Equipment takes slots. Ammo stacking varies by type.
- **Firearms**: M1911 (magazine), .38 revolver (single-load), coach shotgun. Aim system (tile-based, not target-based — leading shots is intended).
- **Identification/Bestiary**: Monsters appear as `?` at range, auto-identify visually within 4 tiles (showing glyph/color). Name and stats only revealed after killing one of that type. Accuracy penalty for shooting unidentified targets.
- **Sanity**: d100 roll-under system. SAN loss on seeing eldritch creatures, ambient events, altar use. Recovery from killing identified creatures. Dreamlands shop sells SAN restoration.
- **Torch/Light**: Consumable resource. Toggleable. FOV radius shrinks as fuel depletes. Darkness accelerates sanity events.
- **Monster AI**: Normal (chase), Ambush (wait behind doors/in water), Stalker (maintain distance), Freeze (only moves when not observed). Per-monster aggression levels for de-aggro.
- **Dreamlands Shop**: Between-floor menu with Bast's cats. Gold → items/SAN restoration. Contextual cat dialogue.
- **Audio**: Procedural ambient drone (reactive to depth/SAN/darkness), step sequencer with 4 tracks (dungeon/deep/dream/title), synthesized SFX (melee/gunfire/doors), heartbeat at low HP.
- **Ambient Event Chains**: Multi-turn narrative sequences that build tension over 3 beats before delivering a SAN roll.

## Collaboration Style
- The user (Lucas) playtests extensively and gives specific, well-reasoned feedback. Trust his gameplay instincts.
- He prefers brainstorming before implementation — discuss design first, then build.
- When suggesting features, frame them as options with tradeoffs rather than prescriptions.
- He's comfortable with experimental branches for uncertain features.
- Keep commits atomic and descriptive. Push to GitHub after each meaningful change.
- Update README and TODO.md when appropriate.
- He values atmosphere and "feel" over mechanical complexity. If a system doesn't feel right in play, redesign it rather than patching it.

## Common Pitfalls (Learned from Experience)
- **Dungeon generation**: Rooms can be sealed off if corridor carving doesn't overwrite walls. Flood-fill validation is the safety net.
- **Door generation**: Naive door placement creates long lines of doors. Requires doorframe pattern detection (walls on two opposite sides).
- **Torch thresholds**: Use crossing-based checks (`prev > mark && current <= mark`) rather than `===` to avoid missing non-integer boundaries.
- **Magic numbers**: All thresholds (torch warnings, SAN events, stat bar colors) should use proportions of max values, not hardcoded absolutes.
- **Identification friction**: Manual "press X to examine" felt like busywork. Auto-identification by proximity + bestiary-through-kills is the current (working) approach.
- **Grammar in combat messages**: Check for "You" as attacker to select correct verb forms ("hit" vs "hits").

## Repository
- GitHub: LucasFinney/Crawl-Of-Cthulhu
- Main branch: `main`
- Feature branches used for experimental systems (e.g., `feature/auto-identify`)
- TODO.md tracks ideas backlog

## File Structure
```
index.html    — The entire game
README.md     — Documentation, controls, features
TODO.md       — Ideas backlog
.gitignore    — OS/editor files, .claude/
CLAUDE.md     — This file
```
