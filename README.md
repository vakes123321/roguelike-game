[README.md](https://github.com/user-attachments/files/35408563/README.md)
# Tower of Shadows

**Tower of Shadows** is a browser-based, mouse-controlled roguelike card game inspired by deck-building dungeon crawlers. Climb a twenty-floor tower, choose doors without knowing what is behind them, build a deck, collect risk-and-reward artifacts, and defeat the Lich King.

The entire game is implemented in one `index.html` file: HTML, CSS, Canvas rendering, game state, card logic, enemy AI, and pixel-art sprites. It uses plain JavaScript and no build tools or runtime libraries.

## Features

- Twenty-floor campaign with ten visual zones, from dungeons to the Cursed Kingdom's throne room
- Dark Knight and Mage starting classes
- Closed doors: the room type is hidden until you open the door
- Deck viewer with card descriptions
- Procedural music for each five-floor stretch and simple attack/block animations
- Turn-based combat with energy and a draw/discard deck
- Single-target and area-of-effect cards
- Poison, frost, burn, bleed, and weakness status effects
- Rat, skeleton, bat, spider, zombie, worm, and Cursed Kingdom enemies (mimic chests, black priests, gargoyles, royal guards)
- Bosses: Necromancer (floor 10), Captain of the Cursed Guard (floor 15), Lich King (floor 20, two phases)
- Combat, trap, chest, event, and rest rooms
- Merchant visits after each floor
- Cards, potions, and 19 artifacts with both bonuses and penalties; six relics are Mage-only
- Procedurally selected room layouts and enemy compositions
- Runs that start fresh; no persistent progression or save system
- Pixel-art graphics generated entirely in Canvas

## Requirements

- A modern desktop or mobile browser with HTML5 Canvas support
- A local web server for the recommended setup
- Internet access only for loading the optional Google Font `Press Start 2P`

The game has no Node.js, package, database, or asset-download requirements.

## Quick Start

Clone or download the repository, enter the project directory, and open `index.html` in your browser:

```bash
cd tower-of-shadows
open index.html
```

On Linux or Windows, open `index.html` directly from your file manager or your browser's **Open File** command.

For local development, a static server is recommended because it matches normal browser deployment behavior:

```bash
cd tower-of-shadows
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

You can use any static server instead, for example:

```bash
npx serve .
```

## How to Play

1. Select **Dark Knight** or **Mage** at the start of a run.
2. Choose one of the closed doors on each tower floor.
3. In combat, select cards in the bottom hand and a target if multiple enemies are present.
4. Spend energy to play cards, then select **End Turn**.
5. Defeat all enemies before reaching zero HP.
6. Earn gold and choose a floor reward, then visit the merchant.
7. Reach floor 20 and defeat the Lich King.

All controls are mouse-based. Hover over relic icons to view their bonus and penalty.

### Dark Knight

The Dark Knight starts with 60 HP and focuses on vampirism (healing from damage), bleed, weakening enemies, and multi-enemy attacks.

### Mage

The Mage starts with 68 HP and focuses on burn, magical shields, healing, fire, and expensive ice spells.

### Room Types

- **Fight:** defeat one to three enemies
- **Trap:** make a risk-based choice or pay a cost
- **Chest:** receive gold, a card, an artifact, or healing
- **Event:** encounter a shrine, merchant ghost, or wandering mage
- **Rest:** heal or search for gold (floors 12, 14, 17, 19)
- **Boss:** Necromancer (floor 10), Captain of the Cursed Guard (floor 15), Lich King (floor 20)

## Game Structure

```text
tower-of-shadows/
├── index.html                 # Complete game implementation
├── docs/
│   ├── features.md            # Mechanics and balance reference
│   └── prompt-en.md           # Original English recreation prompt
└── data/
    └── tower-of-shadows-data.xlsx
                               # Historical balance/design spreadsheet
```

`index.html` contains the complete, maintained implementation. `docs/features.md` is the easiest reference for room types, classes, cards, enemies, and relic effects.

`data/tower-of-shadows-data.xlsx` contains design and balance notes for relics, enemy HP, and floor scaling. Treat it as historical reference: the code is authoritative, and the workbook still uses the enemy scaling and boss multipliers from before the latest rebalance.

## Development Guide

No build step or dependency installation is required. Edit `index.html` and refresh the browser to test changes.

The source is organized into clearly separated JavaScript sections:

- `PAL` and `SP`: sprite palette and pixel-art data
- `CD`: card definitions
- `ENV` and `BOSS`: enemy definitions
- `RL`: artifact definitions
- `TRAPS` and `EVTS`: room event definitions
- `newRun`, `genFloor`, `fight`, `play`, and `endTurn`: run and combat logic
- `dMenu`, `dFloor`, `dFight`, `dShop`, and related functions: Canvas screens
- `loop`: rendering and input cycle

When changing balance or mechanics, keep these files in mind:

- Update card, enemy, artifact, and room constants in `index.html`.
- Update the mechanics summary in `docs/features.md`.
- Treat `data/tower-of-shadows-data.xlsx` as legacy reference until it is updated to match the code.

## Usage Examples

Run locally with Python:

```bash
python3 -m http.server 8000
```

Run with Node.js if no Python installation is available:

```bash
npx serve .
```

Deploy to GitHub Pages:

1. Push `index.html` and the other project files to a GitHub repository.
2. Open **Settings → Pages**.
3. Set **Source** to **Deploy from a branch**.
4. Select the `main` branch and `/ (root)` folder.
5. Wait for deployment and open `https://<username>.github.io/<repository>/`.

The game can also be hosted by any service that serves static files.

## Troubleshooting

- **The page is blank:** open browser developer tools and confirm that JavaScript has no runtime errors.
- **The font looks different:** `Press Start 2P` requires Google Fonts; the game automatically falls back to monospace fonts when offline.
- **The canvas is clipped on a small screen:** use a larger viewport or zoom out in the browser.
- **A browser extension blocks the page:** try an incognito/private window or serve the project over a local HTTP server.

## Contributing

Contributions are welcome for gameplay mechanics, balance, accessibility, visual effects, bug fixes, documentation, and tests.

Before submitting changes:

1. Fork the repository and create a descriptive branch.
2. Keep changes scoped and preserve the single-file architecture unless a build system is deliberately introduced.
3. Test in a modern desktop browser and a mobile browser when the change affects layout or input.
4. Verify new cards, relics, enemies, or room events in a complete run, not only in isolation.
5. Update `docs/features.md` for any player-facing mechanic or balance change.
6. Open a pull request with a concise description, reproduction steps, and screenshots or a recording when relevant.

For bug reports, include browser and operating system details, steps to reproduce, expected behavior, actual behavior, and the browser console output when available.

## Project Status

This is a self-contained browser game with no automated test suite or package manager. Balance data in `index.html` is the source of truth for the current implementation.

## License

No license is currently specified. Until a license is added, the repository's source should be considered privately owned and is not granted for reuse under an open-source license.
