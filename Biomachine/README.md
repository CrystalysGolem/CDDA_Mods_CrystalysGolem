# Biomachine

Biomachine is a CDDA mod that adds training-based "potential" traits and configuration menus.

## Features

- Stamina potential: spend stamina to increase max stamina.
- Focus potential: spend focus to increase learning focus.
- Physical potential: spend stamina to gain STR/DEX over time.
- Mind potential: spend focus to gain INT/PER over time.
- In-game settings menu and startup dialog for tuning coefficients.
- Optional Bombastic Perks integration: perks that boost Biomachine efficiency.

## Traits

- Stamina potential (`STAMINA_POTENTIAL`)
- Focus potential (`FOCUS_POTENTIAL`)
- Physical potential (`PHYSICAL_POTENTIAL`)
- Mind potential (`MIND_POTENTIAL`)
- Biomachine Settings (`BIOMACHINE_MENU`) opens the configuration menu.

## Configuration

Open the Biomachine Settings menu in-game to:
- Adjust stamina efficiency multiplier.
- Adjust Physical/Mind base coefficients and rise coefficients.
- Toggle whether the startup dialog shows on game start.

## Notes

- Stat caps are overridden to 200 when the mod is enabled (see `external_options.json`).
- Physical/Mind scaling uses stage-based exponential growth tied to base stats and Biomachine bonuses.
- Focus potential uses `LEARNING_FOCUS` since there is no direct max-focus stat in JSON.

## Files

- `traits.json`: traits and enchantments
- `eocs.json`: training and menu logic
- `dialogue.json`: configuration dialogs
- `external_options.json`: stat cap overrides
- `bombastic_perkmenu.json`: Bombastic Perks menu entries (optional)

## Compatibility

Designed for CDDA experimental builds and tested against the 2026-01-25-1149 build.
