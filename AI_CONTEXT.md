# AI_CONTEXT: how OStim Beast Form Merged works

This file is for AI assistants, bots and modders who want to understand this mod quickly and build their own (new packs, bodies, textures, a full Vampire Lord version...). Everything written by That Guy (Coronerra) is MIT. Third-party assets belong to their authors (see LICENSE).

## 1. What problem it solves
Transforming changes the player's race to `WerewolfBeastRace` (Skyrim.esm 0x000CDD84) or `DLC1VampireBeastRace` (Dawnguard.esm 0x0000283A). OStim Standalone has no actor type for those races, beast form blocks normal activation, and the beast-form timer keeps running during scenes. This mod makes the beast-form player a normal, sentient OStim actor: actor typing, scene start, hubs, a body/head that work in scenes, OCum climax handling and SkyrimNet awareness.

## 2. Repository layout
```
Data/                         mirrors the game Data folder (text sources only)
  Scripts/Source/*.psc         Papyrus sources (compiled .pex ship in the release zip)
  SKSE/Plugins/OStim/actor properties/   OStim actor types (OBLWerewolfMale/Female, OBLVampireLordMale/Female)
  SKSE/Plugins/OStim/scenes/   hub, idle, forwarding and pack scene JSON overrides
  SKSE/Plugins/OStimNet/animationsDescriptions/   OStimNet scene descriptions for this mod's own scenes
  SKSE/Plugins/SkyrimNet/external/coronerra.beastaware/         SkyrimNet prompt bundle (Beast Aware)
  SKSE/Plugins/SkyrimNet/external/coronerra.beastform_ostimnet/ SkyrimNet prompt bundle (OStimNet bridge)
  Docs/                        changelog README, static checks, hub graphs, integration notes
BUILD_NOTES.md                 build history and record-level details
```
Binaries (ESP, PEX, NIF, DDS, HKX, TRI) are in the release zip, not in git.

## 3. Plugin records (`OStim_Beast_Form_Merged.esp`, ESL, 8 masters)
| FormID (local) | Type | EditorID | Purpose |
|---|---|---|---|
| 800-803, 805-808 | HDPT | BFA_Male/FemaleHead/Mouth/Eyes Werewolf/VampireLord | Separate talking head parts (MFA/BFA morphs) |
| 804 | FLST | BFA_HeadPartsVampireLord | VL head part list |
| 810-813 | PERK | OBL_{Werewolf,VampireLord}{Male,Female}Condition | Conditions referenced by the OStim actor-property JSONs (level 19, below OCR's 20) |
| 820 | QUST | OBF_BeastFormQuest | Runs OBF_Main + OBF_MCM + OBF_PlayerAlias |
| 821 | QUST | BA_BeastAwareQuest | Runs BA_Main + BA_MCM + BA_PlayerAlias |
| 822 | QUST | OCumBeastPieQuest | Runs OCumBeastPie + OCumBeastPieAlias |
| 830 | ARMA | OCumUrethraNodeWerewolfAA | OCum urethra node on the ABC werewolf cock tip |
| 831 / 832 | GLOB | OBL_SwapEnabled / OBL_OCreaturesPresent | Aroused-swap switch / OCR detected flag |
| 833-836 | ARMA/ARMO | OBL_WerewolfAddon(AA), OBL_VampireLordAroused(AA) | Aroused GT Softbody cock / VL hard mesh |
| 837 | QUST | OBL_MainQuest | Runs OBL_Main + OBL_PlayerAlias (aroused swap) |
| 838 | KYWD | OBL_NoStrip | Keeps the swap item from being stripped |
| Override | RACE | WerewolfBeastRace | Growl/JS Eyes base + BFA HEAD parts, FaceGen flag on |
| Override | RACE | DLC1VampireBeastRace | BFA HEAD parts + JS VL eye spell |
| Override | ARMA | NakedTorsoWerewolfBeast (CDD87) | Body without head slot 30, paths to `coronerra\bfa\` |
| Override | ARMA | DLC1NakedVampireLord | Headless VL body |
| Override | ARMO/ARMA | OCumUrethraNodeSOS(AA) (OCum.esp) | Werewolf Shot: OCum shot from the werewolf tip |

The plugin must load after HDT Werewolves, Growl, MFA patches and OCreatures, because its race and ARMA overrides have to win.

## 4. Scripts
| Script | Extends | What it does |
|---|---|---|
| OBF_Main | Quest | Start-scene hotkey (`RegisterForKey`; it can be the same key as OStim's). `TryStart()` checks beast form, finds a partner (`FindTarget`, SearchRadius), explains refusals (`RefuseReason`), optionally StopCombat, starts an OStim thread. Listens to `ostim_thread_start/end` and pauses the beast-form timer (`ShiftBackTime` GLOB, Skyrim 0x2BA19) during scenes (`BeginGuard`/`PushTimer`/`EndGuard`), optionally for ANY scene. |
| OBF_MCM | SKI_ConfigBase | MCM "OStim Beast Form": hotkey, radius, StopCombat, timer guard, debug, and the "Beast climax (OCum)" section (reads OCumBeastPie via GetFormFromFile 0x822). |
| OBF_PlayerAlias | ReferenceAlias | OnInit/OnPlayerLoadGame -> Maintenance + `OBF_OCRCompat.RestoreKeywords()`. |
| OBF_OCRCompat | (Hidden, global) | If OCreatures.esp is loaded, adds OCR race keywords at runtime with powerofthree's Papyrus Extender. No OCR master. |
| OBL_Main | Quest | Male-only aroused swap: on `ostim_thread_start` equips the GT aroused cock (WW) or vampirelord_Hard (VL) on male beasts; restores on thread end/load. Steps aside if OCreatures.esp is loaded. Females are never touched. Mesh existence checked with PapyrusUtil `MiscUtil.FileExists`. |
| OBL_PlayerAlias | ReferenceAlias | Re-runs OBL setup on load. |
| BA_Main | Quest | Beast Aware: detects werewolf / VL / werebear (`DetectForm`) on race switch and load, sends SkyrimNet events (direct narration or silent), and keeps a "currently in beast form" context note. |
| BA_MCM / BA_PlayerAlias | | Beast Aware MCM; `OnRaceSwitchComplete` / load hooks. |
| OCumBeastPie | Quest | Beast Load. Listens to `ostim_actor_orgasm` (+ `ocumtl_pie`, `obf_beastload_mesh`). For male WW/werebear/VL climaxes, classifies the finish (oral / vaginal / anal / foot / hand / outside) from scene tags and actions and calls OCum's functions directly (OCumScript 0x800, OCumMaleScript 0xF38, stage/slot factions 0xF3C-0xF41, AppliedCumKeyword 0xF16) with ThreadID -1. It equips Tull/Liquid meshes by slot, handles multi-round stacking (StorageUtil `OBF_BL_Round`, MaxRounds) and keeps meshes until OCum's timer or a bath clears them. |
| OCumBeastPieAlias | ReferenceAlias | Re-registers on load. |

Compile with Caprica or the CK compiler (game: skyrim). Imports needed: vanilla, SKSE, SkyUI SDK, OStim Standalone, OCum Ascended (OCumScript, OCumMaleScript), PapyrusUtil, PO3 Papyrus Extender, RaceMenu/NiOverride, SkyrimNet API.

## 5. OStim data
- **Actor properties** (`SKSE/Plugins/OStim/actor properties/OBL*.json`): `"type": "Werewolf"` / `"VampireLord"`, gated by the PERK conditions above, with requirement flags (penis, anus, mouth...). OStim then matches pack scenes whose actors are typed Werewolf/VampireLord.
- **Hub model** (OStim NG has no hub feature; a hub is an idle/intro scene whose navigations are buttons):
  - Main hubs: `scenes/OCreatures/OCrWerewolf/<fm|ffm|fmm|fmmm|fmmmm|ff>/OCrWerewolfIdle*.json` and `OCrVampireLord/...`, tagged `idle,intro,creature,werewolf,hub`. Same IDs/paths as OCR, so they override cleanly.
  - Each pack page (e.g. `BillyyCreatures/BillyyWerewolf/fm/BillyyWerewolfHubFM.json`) adds its own button to the main hub with `"origin": "OCrWerewolfIdleFM"`, has `noRandomSelection: true`, and lists stage 1 of each animation. It returns with a medallion icon (`OBeastLite/hub/hub`).
  - Stages chain Next/Back. Return -> pack page; medallion -> main hub.
  - `OBFMerged/OBFWerewolfIdleMF.json`: female werewolf + male human hub (WWF_OnTop). ⚠️ The WWF_OnTop/WWFCowgirl animation is an experimental proof of concept that badly deforms the female werewolf. Don't use it as a reference for good animation.
  - `OBeastLite/...`: old 0.2 IDs kept as non-random forwarding aliases so old saves and installs don't break.
- Fallback animation events `OBF_B_*` (project `OBFMerged`, 21 HKX) let the idles play without OCR. That's why Pandora must be run.

## 6. Load order rules
- Left pane: frameworks -> OStim -> OCum -> ABC -> HDT Werewolves (+MFA/Growl patch) -> MFA -> Growl/JS Eyes -> GT Softbody -> Tull/Liquid -> **OCR (optional)** -> animation packs -> SkyrimNet/OStimNet -> **this mod** -> BFA -> Pandora output.
- Plugins: this ESP after OStim, OCum, OCreatures, MFA, Growl and its patches, and the HDT Werewolves patch. On Nolvus: as low as possible but above the Paper Maps plugins.

## 7. How to extend
- **New animation pack with werewolf scenes:** best case, the pack's page uses `"origin": "OCrWerewolfIdleFM"` (or the matching actor-count idle), so it appears on the main hub automatically. Otherwise add a pack-page JSON with that origin, list stage 1 of each animation, and add a Return navigation. Use actor `"type": "Werewolf"` with the male werewolf first.
- **Female werewolf scenes (most wanted):** actor type `Werewolf` with `intendedSex: female` (OBLWerewolfFemale gives vagina/breasts). Attach to `OBFWerewolfIdleMF` (female WW + man) or `OCrWerewolfIdleFF`, which stays untagged until real FF scenes exist. Tag it `hub` once it has content.
- **Vampire Lord version:** the plumbing already exists (actor types, VL hubs, OBL VL swap, Beast Load, BFA VL heads). What's missing: `OBF_Main.IsPlayerBeast()` currently checks only `WerewolfBeastRace`, so the start-scene hotkey and the beast-timer guard are werewolf-only. Add `DLC1VampireBeastRace` there (VL scenes can still start through OStim/OStimNet). Also needed: a VL aroused mesh with confirmed authorship, and more VL scenes.
- **Custom bodies/textures:** replace the files under `meshes/actors/werewolfbeast/character assets/coronerra/bfa/` keeping names, or point ARMA CDD87 elsewhere in your own override plugin loaded after this one. Keep the head (slot 30) off the body, because the head comes from the HDPT records.
- **OCR:** never add OCreatures.esp as a master. Gate on `Game.GetModByName("OCreatures.esp") != 255` as `OBF_OCRCompat` and `OBL_Main` do.

## 8. Other Coronerra repos
See the list in README.md.
