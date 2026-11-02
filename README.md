# Tower Defense Game App (working title)

A mobile-first **tower defense roguelite**. You defend an icebreaker ship stuck in a frozen sea against waves of polar creatures that advance across the ice on multiple paths.

> Status: **early development**. The repository is being set up; the first playable prototype is the next milestone.

**Who it is for:** mobile players who like tower defense and roguelite games.

## The game

### Premise

An icebreaker got trapped in the pack ice. Penguins, seals, walruses and sharks come from every direction to take it over. The player places and upgrades defensive towers on the ice to stop them before they reach the ship. If enough enemies get through, the hull breaks and the run ends.

### Core loop

1. Enemies advance in waves along several paths that lead to the ship.
2. The player spends **coins** to place and upgrade towers.
3. Each enemy defeated gives coins.
4. Enemies that reach the ship damage its **hull** (life). Hull at zero ends the run.

### Roguelite layer

- Between waves, the player picks **1 of 3 random cards**: tower upgrades, new towers, ship upgrades or run modifiers.
- At the end of a run, the player earns a permanent currency to unlock content between runs (meta-progression).
- Every run is different: card synergies, random events and bosses.
- All randomness comes from a seeded RNG, so any run can be reproduced.

### Signature mechanic: breakable ice

The map is not static. Heavy enemies crack the ice, opening holes that block or change paths during the wave. Sharks can burst out of holes in the middle of a path. Some towers interact with the ice too (for example, a heater that melts it under enemies).

### Initial content (MVP)

**Towers**

| Tower        | Role                                           |
| ------------ | ---------------------------------------------- |
| Harpoon      | Single target, long range, high damage         |
| Snow Cannon  | Area damage and slow, slow fire rate           |
| Lighthouse   | Stuns enemies in its beam, no damage           |
| Heater       | Melts the ice under enemies, changes the paths |

**Enemies**

| Enemy   | Trait                                                |
| ------- | ---------------------------------------------------- |
| Penguin | Fast, low health, comes in groups                    |
| Seal    | Average speed and health                             |
| Walrus  | Slow, high health, cracks the ice                    |
| Shark   | Travels under the ice and surfaces through the holes |
| Orca    | Boss                                                 |

**Map:** 1 map, 10 waves, boss on wave 10.

Graphics start as simple placeholder shapes. Art comes later and only from open licenses (CC0, CC-BY, OFL) or made by the author, each asset listed in `ASSETS.md`.

## Platforms

- **PWA (main target):** plays in any browser and installs on iPhone and Android from "Add to Home Screen". Works offline.
- **Android APK:** the same build packaged with Capacitor.
- Landscape orientation, touch-only input, base resolution 1280×720.

## Stack

| Layer          | Technology                    |
| -------------- | ----------------------------- |
| Engine         | Phaser 3 (WebGL)              |
| Language       | TypeScript (strict)           |
| Build/dev      | Vite                          |
| PWA            | vite-plugin-pwa               |
| Mobile         | Capacitor (Android)           |
| Tests          | Vitest                        |
| Quality        | ESLint + Prettier             |
| CI             | GitHub Actions (lint, test, build) |

## Architecture

The central rule: **game logic is separate from rendering.**

- `src/core` holds the rules (combat, waves, economy, cards, pathfinding, RNG, save) in pure TypeScript, with **no Phaser import**. Everything there has unit tests.
- `src/config` holds all balance numbers (towers, enemies, waves, cards). Nothing is hardcoded in scenes.
- `src/scenes`, `src/entities` and `src/ui` only draw the game state and capture touch input.

## Privacy

No accounts, no login, no online ranking, no analytics and no personal data collection. All progress is saved locally on the device.

## Development environment

- Node.js LTS and npm
- Git
- Development runs on Linux, macOS, or Windows through **WSL2**

## How to run

The game cannot be run yet: the repository holds the design and the plan, and the scaffold is Phase 0 of the roadmap. The install, dev and test commands will be documented here as part of that phase.

## Roadmap

The planned work, phase by phase, is in [ROADMAP.md](ROADMAP.md).

## License

The code is released under the [MIT License](LICENSE). Third-party assets keep their own licenses, listed in `ASSETS.md`.
