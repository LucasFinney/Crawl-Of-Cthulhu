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
- **1920s firearms** — randomly assigned starting weapon (M1911, .38 revolver, or coach shotgun) with realistic ammo capacity, reload times, and scarce ammunition
- **Aim system** — spend turns steadying your aim for better accuracy; fire beyond max range at a penalty
- Sanity system — eldritch encounters and ambient dread erode your mind; reach 0 and you're lost to madness
- Passive HP regeneration balanced by ambient sanity decay with atmospheric narration
- Inventory system (10 slots) — equipment, ammo, and carried items all share limited space
- Dark altars that offer power at a cost
- Doors that block line of sight until opened
- Local high score leaderboard (localStorage)
- Death screens that differ based on cause of death (HP loss vs. sanity loss)

## Controls

| Key | Action |
|---|---|
| `Arrow keys` / `WASD` / `Numpad` | Move (8-directional) |
| `L` | Look/Aim mode — move cursor to inspect or target |
| `F` | Fire weapon (in look mode) |
| `.` | Aim — spend a turn steadying (+10% accuracy, in look mode) |
| `R` | Reload firearm (takes multiple turns) |
| `[` / `]` | Rotate facing (counter-clockwise / clockwise) |
| `G` | Pick up item |
| `I` | Open inventory |
| `1`–`9` | Use inventory item (while inventory is open) |
| `>` | Descend stairs |
| `.` or `5` | Wait a turn (outside look mode) |
| `?` | Help screen |
| `H` | Hall of Investigators (title screen) |

## Firearms

| Weapon | Damage | Range | Magazine | Reload | Base Accuracy |
|---|---|---|---|---|---|
| M1911 pistol | 5–9 | 8 | 7 | 2 turns | 65% |
| .38 revolver | 4–7 | 6 | 6 | 3 turns | 60% |
| Coach shotgun | 10–18 | 4 | 2 | 3 turns | 70% |

- Pistol ammo: each magazine takes 1 inventory slot (no stacking)
- Shotgun shells: stack up to 6 per inventory slot
- Aiming: +10% accuracy per turn spent (max +30%), costs real turns
- Out-of-range shots: allowed, but -10% accuracy and -30% damage per tile beyond max range
- Gunfire wakes all monsters within earshot

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
| `=` | Ammo |
| `!` | Potion / consumable |
| `)` | Weapon |
| `[` | Armor |
| `?` | Scroll |
| `*` | Elder Sign |

## Tech

Single-file vanilla HTML/CSS/JavaScript. No frameworks, no canvas — pure DOM-rendered ASCII in a `<pre>`-style monospace layout. Runs in any modern browser.

## License

MIT
