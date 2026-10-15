# CDDA Mods by CrystalysGolem

A collection of small mods for [Cataclysm: Dark Days Ahead](https://github.com/CleverRaven/Cataclysm-DDA) —
mostly compatibility glue and rebalance tweaks around **Aftershock: Exoplanet**, **Magiclysm**,
**Xedra Evolved** and **Mind Over Matter**.

## Compatibility (CDDA versions)

| | |
|---|---|
| **Made for** | Cataclysm-DDA **0.I experimental**, builds of late February – early March 2026 (reference commit [`0880a5e5`](https://github.com/CleverRaven/Cataclysm-DDA/commit/0880a5e503ce2161b042d49fcd79068f6c9b30a5), 2026-03-01) |
| **Updated & verified for** | `cdda-0.I-2026-09-19-2324` — commit [`7b2efa5c`](https://github.com/CleverRaven/Cataclysm-DDA/commit/7b2efa5cea38e4d4d97dd0e63b28b9148623da59), validated with the game's own `--check-mods` validator |
| **Probably not for** | stable 0.H and older, or builds much newer than the ones above |

These are mods for experimental builds: the data they touch changes between daily builds. If you
update the game and something breaks, re-run the validator (see [Testing](#testing-after-a-game-update)).

## Installation

1. Copy the mod folders (each contains `modinfo.json`) into the `mods/` directory next to
   `cataclysm-tiles.exe` (it survives game updates). On older builds without that folder, use
   `data/mods/` instead.
2. Enable the mods you want in the world's **mod list**, enabling the dependency mods first
   (e.g. Xedra Evolved before `Xedra_All_Classes`).

## The mods

| Folder (mod id) | Requires | What it does |
|---|---|---|
| `Aftershock_Genemod_Psionics` (`aftershock_genemod_psionics`) | Aftershock: Exoplanet | Removes the incompatibility between genemods and psionics: espers can use gene clinics, genemodded characters can become espers. |
| `Aftershock_No_Bionic_Slots` (`aftershock_no_bionic_slots`) | Aftershock: Exoplanet | Disables the bionic-slot limits of Aftershock: install any number of CBMs per body part. |
| `Chronomancer_Item` (`chronomancer_item`) | Xedra Evolved | Adds a rare consumable (temporal catalyst) that transforms the user into a full Chronomancer package; spawns rarely in Xedra office/junk/cabinet item groups. |
| `Magiclysm_All_Classes` (`magiclysm_all_classes`) | Magiclysm | All eight spellcasting classes and all attunements simultaneously (removes their mutual exclusions). Adds the "Master of All Arts" hobby covering all eight base classes. |
| `Magiclysm_No_Bionic_Mana_Penalty` (`magiclysm_no_bionic_mana_penalty`) | Magiclysm | Trait "Mana-Bionic Decoupling": stored bionic power no longer reduces your maximum mana. |
| `Max_Stats_200` (`max_stats_200`) | DDA | Raises the cap on maximum effective stats (STR/DEX/INT/PER) to 200 via the `PLAYER_MAX_*` external options. See the note below for which builds it works on. |
| `MOM_Psychic_Knack_Fix` (`MOM_PSI_KNACK_FIX`) | Mind Over Matter | Removes the awakening-chance penalty of Psychic Knacks (no longer slows learning new psionic powers). |
| `Xedra_All_Classes` (`xedra_all_classes`) | Xedra Evolved | All four Xedra classes (Eater, Dreamer, Inventor, Dreamsmith) simultaneously; adds the "Awakened All" hobby. |
| `Xedra_Living_Paradox_Upgrades` (`xedra_living_paradox_upgrades`) | Xedra Evolved | Insight-purchasable upgrades for Living Paradox chronomancers: Sleep Acceleration I–III and Insight Grip, via the "Paradox Upgrades" menu. |

More detail (usage, load order) is in each mod folder's own `README.md` where present.

### Max_Stats_200 and game builds

Stat caps are enforced through the `PLAYER_MAX_STR_VALUE` and friends external options
([upstream PR #83001](https://github.com/CleverRaven/Cataclysm-DDA/pull/83001)). The build
`2026-09-19-2324` shipped **without** those options — and without any stat cap at all — so on that
build this mod is a harmless no-op (effective stats are already uncapped there). Upstream
re-introduced the cap system in October 2026; on builds that have the options the mod works as
intended. Keep the mod **after** Magiclysm / Xedra Evolved in the load order so its values win.

## Testing after a game update

Windows builds include a headless validator; from the game directory:

```
cataclysm-tiles.exe --check-mods max_stats_200 magiclysm_all_classes magiclysm_no_bionic_mana_penalty
```

It loads each listed mod together with its dependencies and reports errors (exit code 0 = clean).
All nine mods in this repository pass on build `2026-09-19-2324`.

## Known upstream noise on build 2026-09-19-2324

In strict validation the *bundled* mods themselves log a couple of messages; none of them come
from these mods:

- `MindOverMatter` — `holy_symbol_fifth_sun ... has two definitions from the same source` when both
  the Bombastic Perks and Xedra Evolved interaction files are loaded (upstream issue).
- `Xedra_Evolved` — `EOC_CONDITIONS_LILIN_DINOMOD_RUACH_DRAIN ... two definitions` (its DinoMod
  compatibility file re-defines an EOC that also exists as a stub definition).
- `Xedra_Evolved` — a math-expression note about `xedra_chronomancer_level` in
  `chronomancer_insight_menu.json`, visible only in strict validation; the function exists in
  Xedra's `jmath.json` and works in normal play.

## License

None of these mods ship with a license; they are personal mods shared as is. Cataclysm: DDA and
its bundled mods are CC-BY-SA 3.0, and anything derived from them follows the same license.
