# Maximum Stats 200

Raises the cap on maximum effective character stats — Strength, Dexterity,
Intelligence, Perception — from the game's default (20) to 200.

## How it works

The mod sets four **external options**, first introduced upstream in
[PR #83001](https://github.com/CleverRaven/Cataclysm-DDA/pull/83001):

- `PLAYER_MAX_STR_VALUE`
- `PLAYER_MAX_DEX_VALUE`
- `PLAYER_MAX_PER_VALUE`
- `PLAYER_MAX_INT_VALUE`

## Compatibility (important)

The effect depends on the game build:

- **CDDA 0.I experimental, late 2025 – early 2026** (the era this mod was made
  for): the options exist and are enforced in the engine's stat getters. The
  mod works as intended.
- **Build `2026-09-19-2324`**: upstream had temporarily removed both the
  options and the stat cap itself — effective stats are already uncapped
  there. This mod is a harmless no-op on that build (no errors, there is
  simply no cap to raise).
- **October 2026 and later builds** (after the stat cap was re-introduced
  upstream): the options exist again, and the mod works as before.

## Load order

If you play Magiclysm or Xedra Evolved, enable this mod **after** them in the
world's mod list so its option values override their stat-cap values.
