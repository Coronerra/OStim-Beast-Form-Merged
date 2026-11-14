# AI_CONTEXT: how OStim Beast Form Merged works

This file is for AI assistants, bots and modders who want to understand this mod quickly and build their own (new packs, bodies, textures, a full Vampire Lord version...). Everything written by That Guy (Coronerra) is MIT. Third-party assets belong to their authors (see LICENSE).

## 1. What problem it solves
Transforming changes the player's race to `WerewolfBeastRace` (Skyrim.esm 0x000CDD84) or `DLC1VampireBeastRace` (Dawnguard.esm 0x0000283A). OStim Standalone has no actor type for those races, beast form blocks normal activation, and the beast-form timer keeps running during scenes. This mod makes the beast-form player a normal, sentient OStim actor: actor typing, scene start, hubs, a body/head that work in scenes, OCum climax handling and SkyrimNet awareness.

## 2. Since 0.7: one installer, TWO body for everyone
0.7 folds four earlier downloads into one FOMOD zip. Every setup uses the **TWO - Total Werewolf Overhaul 4.1** body (Frosferes; required, never shipped). The older repos (OStim-Beast-Form-TWO, OStim-Beast-Form-Merged-TWO-Patch, OStim-Beast-Form-TWO-Herm-Patch, OStim-Beast-Form) are deprecated and point here.

Installer pages (`fomod/ModuleConfig.xml`, FOMOD 5.0, validated against the schema):
1. **TWO user or Growl user** (SelectExactlyOne; Growl first and `Recommended` so it is pre-selected) -> flag `body` = `growl` / `two`.
2. **Do you use softbody?** (SelectExactlyOne; No first and `Recommended`) -> flag `softbody` = `no` / `yes`.
3. **Hermaphrodite patch? A.K.A. Fruta?** (SelectAny, Optional) -> flag `herm` = `on`.
4. **Read and acknowledge** (SelectAll, one `Required` plugin "I have read and understand").

Zip folders and when they install (`conditionalFileInstalls`):

| Folder | Installed when | Contents |
|---|---|---|
| `00 Common` | always | scripts shared by both editions (incl. the 0.7 `OBL_Main`), scene/hub JSON, OStimNet descriptions, HKX fallback idles, Vampire Lord meshes/textures, OCum urethra node, hub icon, docs |
| `10 Growl` | body=growl | `OStim_Beast_Form_Merged.esp` (0.6, byte-identical), `OStim_Beast_Form_Merged_TWO_Patch - BFA Heads.esp`, BFA TRI, `coronerra\twopatch\werewolfsheath.nif`, Merged `OBF_MCM`, Merged actor properties and SkyrimNet manifests |
| `11 Growl Softbody` | growl + yes | `OStim_Beast_Form_Merged_TWO_Patch.esp` = TWO Patch 0.1, byte-identical |
| `12 Growl No Softbody` | growl + no | `OStim_Beast_Form_Merged_TWO_Patch.esp` = TWO Patch 0.1 + one override of Merged's `OBL_WerewolfAddonAA` (0x833) -> TWO `CreatureFramework\CanineRedHard.nif` |
| `20 TWO` | body=two | `OStim_Beast_Form_TWO - BFA Heads.esp`, BFA TRI, TWO `OBF_MCM` (has the `BeastPie` property), TWO actor properties and SkyrimNet manifests |
| `21 TWO Softbody` | two + yes | `OStim_Beast_Form_TWO.esp` = TWO Edition 0.2 with `OBL_WerewolfAddonAA` (0x833) -> `MoreNastyCritters\werewolf\Addon_Dog_Black_Hard.nif` (the Merged record, byte-identical) |
| `22 TWO No Softbody` | two + no | `OStim_Beast_Form_TWO.esp` = TWO Edition 0.2, byte-identical |
| `30 Softbody` | softbody=yes | GT Softbody `MoreNastyCritters\werewolf\Addon_Dog*.nif` (Goutou) + `werewolf_balls*` / `werewolf_canine_penis_*` textures |
| `40 Herm` | herm=on | `OStim_Beast_Form_TWO_Herm_Patch.esp` (Herm Patch 0.1, byte-identical), `OBFHerm_*.pex` (0.7 `OBFHerm_Main`), `OBLWerewolfHerm.json` |

**Softbody-only content** is exactly: the three GT Softbody cock meshes, their seven textures, and the 0x833 model path. Nothing else in the mod depends on GT Softbody.

Text sources in this repo: `Data/` = `00 Common` + `10 Growl` text files; `options/20 TWO/`, `options/40 Herm/` = the TWO and Herm text files; `fomod/` = the installer. Binaries (ESP, PEX, NIF, DDS, HKX, TRI) are only in the release zip.

## 3. Plugins
### Growl option: `OStim_Beast_Form_Merged.esp` (ESL, 8 masters) + `OStim_Beast_Form_Merged_TWO_Patch.esp`
Merged masters: Skyrim, Update, Dawnguard, Dragonborn, `JS Emissive Eyes SE - Johnskyrim.esp`, `Growl - Werebeasts of Skyrim.esp`, `OStim.esp`, `OCum.esp`.

| FormID (local) | Type | EditorID | Purpose |
|---|---|---|---|
| 800-803 | HDPT | BFA_Male/Female Head/Mouth/Eyes Werewolf | 0.1-0.6 werewolf heads. Unused since 0.7 (the patch's race uses TWO's heads); files no longer shipped |
| 804 | FLST | BFA_HeadPartsVampireLord | VL head part list |
| 805-808 | HDPT | BFA_* VampireLord | Talking VL head parts |
| 810-813 | PERK | OBL_{Werewolf,VampireLord}{Male,Female}Condition | Conditions referenced by the OStim actor-property JSONs (level 19, below OCR's 20) |
| 820 | QUST | OBF_BeastFormQuest | OBF_Main + OBF_MCM + OBF_PlayerAlias |
| 821 | QUST | BA_BeastAwareQuest | BA_Main + BA_MCM + BA_PlayerAlias |
| 822 | QUST | OCumBeastPieQuest | OCumBeastPie + OCumBeastPieAlias |
| 830 | ARMA | OCumUrethraNodeWerewolfAA | OCum urethra node on bone WWD 9 |
| 831 / 832 | GLOB | OBL_SwapEnabled / OBL_OCreaturesPresent | Aroused-swap switch / OCR detected flag |
| 833-836 | ARMA/ARMO | OBL_WerewolfAddon(AA), OBL_VampireLordAroused(AA) | Aroused werewolf cock (slot 52) / VL hard mesh |
| 837 | QUST | OBL_MainQuest | OBL_Main + OBL_PlayerAlias |
| 838 | KYWD | OBL_NoStrip | Keeps the swap item from being stripped |
| Override | RACE / ARMA / ARMO | WerewolfBeastRace, NakedTorsoWerewolfBeast, DLC1VampireBeastRace, DLC1NakedVampireLord, OCumUrethraNodeSOS(AA) | as 0.6; the werewolf race and body are overridden again by the patch |

Patch masters: the first six above + `MonsterLipSync1.esp`, `Werewolves.esp` (TWO), `OStim_Beast_Form_Merged.esp`. Records: RACE `WerewolfBeastRace` (Merged's record with TWO's head parts and a new skin), ARMA `NakedTorsoWerewolfBeast` (TWO's record), ARMO `OBFTWO_SkinNakedWerewolfBeast` (TWO body + sheath), ARMA `OBFTWO_WerewolfSheathAA` (slot 49), HDPT `FemaleMouthWerewolf` (TWO record with the TRI path fixed); the no-softbody build adds ARMA 0x833. Load it directly after the Merged plugin; `Werewolves.esp` / `WerewolvesGrowl.esp` load after OCreatures and the Growl patches.

### TWO option: `OStim_Beast_Form_TWO.esp` (ESL)
Masters: Skyrim, Update, Dawnguard, Dragonborn, `Werewolves.esp`, `MonsterLipSync1.esp`, `OStim.esp`, `OCum.esp` (the TWO/MFA masters sit in the slots JS Eyes and Growl hold in Merged, so every other index and all local FormIDs match). Same records as Merged without the werewolf race/body override and without HDPT 800-803. TWO keeps the werewolf race.

### BFA head plugins (always installed)
`OStim_Beast_Form_Merged_TWO_Patch - BFA Heads.esp` (Growl) / `OStim_Beast_Form_TWO - BFA Heads.esp` (TWO). Masters Skyrim, MonsterLipSync1, Werewolves.esp. Override TWO's `MaleHeadWerewolf` / `FemaleHeadWerewolf` NAM1 to `coronerra\two\ExpHeadWerewolf_BFA.tri` (TWO's TRI, byte-identical geometry and 36 morphs, plus `browupleft` / `browupright`). The TWO version also fixes `FemaleMouthWerewolf`.

### Hermaphrodite option: `OStim_Beast_Form_TWO_Herm_Patch.esp` (ESL, master Skyrim.esm only)
MGEF 801 / SPEL 802 condition ability, PERK 803 (level 50: race WerewolfBeastRace + HasMagicEffect 801), QUST 804 running `OBFHerm_Main`. `OBLWerewolfHerm.json` points OStim at perk 803. Soft-detects `WerewolvesExtras.esp` (`TWO_PlayerHermVal` 0xC09); herm value 1 or 2 in werewolf form adds the ability. Resolves the loaded Beast Form plugin (Merged first, then TWO) at runtime, so one set of files serves both options.

## 4. Scripts
| Script | Extends | What it does |
|---|---|---|
| OBF_Main | Quest | Start-scene hotkey (`RegisterForKey`; it can be the same key as OStim's). `TryStart()` checks beast form, finds a partner, explains refusals, optionally StopCombat, starts an OStim thread. Pauses `PlayerWerewolfShiftBackTime` (Skyrim 0x2BA19) during scenes, optionally for ANY scene. TWO Extras' werewolf script still uses that global. |
| OBF_MCM | SKI_ConfigBase | MCM "OStim Beast Form". The TWO build has an `OCumBeastPie Property BeastPie` filled by its plugin, falling back to `GetFormFromFile(0x822, "OStim_Beast_Form_Merged.esp")`. |
| OBF_PlayerAlias | ReferenceAlias | OnInit/OnPlayerLoadGame -> Maintenance + `OBF_OCRCompat.RestoreKeywords()`. |
| OBF_OCRCompat | (Hidden, global) | If OCreatures.esp is loaded, adds OCR race keywords at runtime with powerofthree's Papyrus Extender. No OCR master. |
| OBL_Main | Quest | Male-only aroused swap on `ostim_thread_start`, restore on thread end/load; steps aside if OCreatures.esp is loaded; females never touched. **0.7:** `Setup()` sets `WerewolfMesh` from `OBL_WerewolfAddon.GetNthArmorAddon(0).GetModelPath(false, false)` before the `MiscUtil.FileExists` check, so the plugin's 0x833 record (softbody choice) decides, not a value stored in an old save. |
| OBL_PlayerAlias | ReferenceAlias | Re-runs OBL setup on load. |
| BA_Main / BA_MCM / BA_PlayerAlias | | Beast Aware: SkyrimNet events on race switch and load, "currently in beast form" context. |
| OCumBeastPie / OCumBeastPieAlias | Quest / ReferenceAlias | Beast Load: on `ostim_actor_orgasm` for male WW / werebear / VL, classifies the finish and calls OCum's functions directly (ThreadID -1), equips Tull/Liquid meshes, stacks rounds (StorageUtil `OBF_BL_Round`, MaxRounds). |
| OBFHerm_Main / OBFHerm_PlayerAlias | Quest / ReferenceAlias | Herm option. **0.7:** reads the aroused mesh from the 0x835 item's armor addon too. |

Compile with Caprica (game=skyrim) or the CK compiler. Imports: vanilla, SKSE, SkyUI SDK, OStim Standalone, OCum Ascended, PapyrusUtil, PO3 Papyrus Extender, RaceMenu/NiOverride, SkyrimNet API.

## 5. OStim data
- **Actor properties** (`SKSE/Plugins/OStim/actor properties/OBL*.json`): `"type": "Werewolf"` / `"VampireLord"`, gated by the PERK conditions; `"mod"` is the edition's plugin name (that's why they are per option).
- **Hub model** (OStim NG has no hub feature; a hub is an idle/intro scene whose navigations are buttons):
  - Main hubs: `scenes/OCreatures/OCrWerewolf/<fm|ffm|fmm|fmmm|fmmmm|ff>/OCrWerewolfIdle*.json` and `OCrVampireLord/...`, tagged `idle,intro,creature,werewolf,hub`. Same IDs/paths as OCR, so they override cleanly.
  - Each pack page (e.g. `BillyyCreatures/BillyyWerewolf/fm/BillyyWerewolfHubFM.json`) adds its own button to the main hub with `"origin": "OCrWerewolfIdleFM"`, has `noRandomSelection: true`, and lists stage 1 of each animation. It returns with a medallion icon (`OBeastLite/hub/hub`).
  - `OBFMerged/OBFWerewolfIdleMF.json`: female werewolf + male human hub with no buttons of its own. Separate female-werewolf scene packs add their button with `"origin": "OBFWerewolfIdleMF"`.
  - `OBeastLite/...`: old 0.2 IDs kept as non-random forwarding aliases.
- Fallback animation events `OBF_B_*` (project `OBFMerged`, 21 HKX) let the idles play without OCR. That's why Pandora must be run.

## 6. Load order rules
- Left pane: frameworks -> OStim -> OCum -> MFA -> Growl/JS Eyes -> GT Softbody -> Tull/Liquid -> OCR (optional) -> animation packs -> SkyrimNet/OStimNet -> **this mod** -> TWO (+ Alternate Textures, BodySlide output) -> BFA -> Pandora output. No file of this mod overlaps a TWO file except seven byte-identical MoreNastyCritters textures (softbody Yes).
- Plugins: Growl option `... Werewolves.esp, WerewolvesGrowl.esp, OStim_Beast_Form_Merged.esp, OStim_Beast_Form_Merged_TWO_Patch.esp, ... - BFA Heads.esp, [Herm]`. TWO option `... Werewolves.esp, OStim_Beast_Form_TWO.esp, ... - BFA Heads.esp, [Herm]`. `Werewolves.esp` after OCreatures.esp. On Nolvus: as low as possible but above the Paper Maps plugins.
- Never enable `OStim_Beast_Form_TWO.esp` together with `OStim_Beast_Form_Merged.esp` (same scripts).

## 7. How to extend
- **New animation pack with werewolf scenes:** best case, the pack's page uses `"origin": "OCrWerewolfIdleFM"` (or the matching actor-count idle), so it appears on the main hub automatically. Otherwise add a pack-page JSON with that origin, list stage 1 of each animation, and add a Return navigation. Use actor `"type": "Werewolf"` with the male werewolf first.
- **Female werewolf scenes (most wanted):** actor type `Werewolf` with `intendedSex: female`. Attach to `OBFWerewolfIdleMF` or `OCrWerewolfIdleFF` with `origin` from your own pack instead of editing these files.
- **A different aroused mesh:** override ARMA 0x833 (`OBL_WerewolfAddonAA`) in your own plugin loaded after this mod's plugins. Since 0.7 the scripts follow the record's model path; keep slot 52.
- **Vampire Lord version:** the plumbing exists (actor types, VL hubs, OBL VL swap, Beast Load, BFA VL heads). `OBF_Main.IsPlayerBeast()` checks only `WerewolfBeastRace`, so the hotkey and timer guard are werewolf-only.
- **OCR:** never add OCreatures.esp as a master. Gate on `Game.GetModByName("OCreatures.esp") != 255`.
- **TWO:** never add TWO, TWO Alternate Textures, MFA or Growl files to this repo or the zip. Reference paths and records only. If Frosferes asks, the mod is taken down.

## 8. Other Coronerra repos
See the list in README.md.
