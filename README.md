# Crawl of Cthulhu

A classic roguelike dungeon crawler inspired by the Cthulhu Mythos, built entirely in a single HTML file with ASCII graphics.

## Play

Open `index.html` in any modern browser. No build step, no dependencies.

## About

You are an investigator descending into the cyclopean tunnels beneath Arkham. Survive 9 levels of procedurally generated dungeons, fight eldritch horrors, and keep your sanity intact — or die trying.

**Features:**

- Procedural dungeon generation with rooms, corridors, and doors
- Directional field of view — 120° forward cone with limited peripheral vision
- Turn-based combat against 9 Mythos-themed monster types (cultists, ghouls, deep ones, mi-go, shoggoths, and more)
- Sanity system — eldritch encounters and ambient dread erode your mind; reach 0 and you're lost to madness
- Passive HP regeneration balanced by ambient sanity decay with atmospheric narration
- Inventory system with weapons, armor, consumables, and rare artifacts (Elder Signs, Necronomicon pages)
- Dark altars that offer power at a cost
- Doors that block line of sight until opened
- Local high score leaderboard (localStorage)
- Death screens that differ based on cause of death (HP loss vs. sanity loss)

## Controls

| Key | Action |
|---|---|
| `Arrow keys` / `WASD` / `Numpad` | Move (8-directional) |
| `R` / `T` | Rotate facing (clockwise / counter-clockwise) |
| `G` | Pick up item |
| `I` | Open inventory |
| `1`–`9` | Use inventory item (while inventory is open) |
| `L` | Look mode — move a cursor to inspect tiles |
| `>` | Descend stairs |
| `.` or `5` | Wait a turn |
| `?` | Help screen |

## Symbols

| Symbol | Meaning |
|---|---|
| `→` (arrow) | You (arrow shows facing direction) |
| `#` | Wall |
| `.` | Floor / corridor |
| `+` | Closed door (blocks vision — bump to open) |
| `/` | Open door |
| `>` | Stairs down |
| `_` | Dark altar |
| `~` | Water |
| `$` | Gold |
| `!` | Potion / consumable |
| `)` | Weapon |
| `[` | Armor |
| `?` | Scroll |
| `*` | Elder Sign |

## Tech

Single-file vanilla HTML/CSS/JavaScript. No frameworks, no canvas — pure DOM-rendered ASCII in a `<pre>`-style monospace layout. Runs in any modern browser.

## License

MIT
