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
- **Monster identification** — creatures appear as `?` until examined; identifying eldritch horrors costs sanity (sometimes ignorance is safer)
- **1920s firearms** — randomly assigned starting weapon (M1911, .38 revolver, or coach shotgun) with realistic ammo capacity and scarce ammunition
- **Aim system** — spend turns steadying your aim for better accuracy; aiming is tile-based, so you must lead your shots
- **Reload mechanics** — M1911 swaps magazines in fixed turns; revolver and shotgun load one round per turn (cancel mid-reload to fire with a partial load)
- **Sanity system** — SAN loss uses a roll-under mechanic (higher sanity = better chance to resist); each monster instance provokes a SAN check only once
- **Ambient dread** — atmospheric events during peaceful exploration erode your mind; surreal events become more common on deeper levels
- **Stamina & running** — sprint mode doubles movement speed at the cost of stamina; melee attacks also consume stamina
- Passive HP regeneration balanced by ambient sanity decay
- Inventory system (10 slots) — equipment, ammo, and carried items all share limited space
- Dark altars — step on to sense, press G to pray; may heal, empower, or corrupt
- Doors that block line of sight until opened
- Stairs remain highlighted on the map once discovered
- Local high score leaderboard (localStorage)
- Death screens that differ based on cause of death (HP loss vs. sanity loss)

## Controls

| Key | Action |
|---|---|
| `Arrow keys` / `WASD` / `Numpad` | Move (8-directional) |
| `L` | Look/Aim mode — move cursor to inspect or target |
| `[` / `]` | Cycle cursor between visible targets (in look mode) |
| `Enter` | Examine / identify creature (in look mode) |
| `F` | Fire weapon (in look mode) |
| `.` | Aim — spend a turn steadying (+10% accuracy, in look mode) |
| `R` | Reload firearm (press again to stop single-load early) |
| `Tab` | Toggle run mode (double movement, costs stamina) |
| `[` / `]` | Rotate facing (outside look mode) |
| `G` | Pick up item / Pray at altar |
| `I` | Open inventory |
| `1`–`9` | Use inventory item (while inventory is open) |
| `>` | Descend stairs |
| `.` or `5` | Wait a turn (outside look mode) |
| `?` | Help screen |
| `H` | Hall of Investigators (title screen) |

## Firearms

| Weapon | Damage | Range | Magazine | Reload | Base Accuracy |
|---|---|---|---|---|---|
| M1911 pistol | 5–9 | 8 | 7 | 2 turns (magazine swap) | 65% |
| .38 revolver | 4–7 | 6 | 6 | 1 turn/round (single load) | 60% |
| Coach shotgun | 10–18 | 4 | 2 | 1 turn/shell (single load) | 70% |

- M1911 ammo: each magazine takes 1 inventory slot (no stacking); full magazine swap on reload
- Revolver / shotgun: load one round per turn; press R again to stop early and fire with a partial load
- Shotgun shells: stack up to 6 per inventory slot
- Aiming: +10% accuracy per turn spent (max +30%), tile-based (lead your shots!)
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
