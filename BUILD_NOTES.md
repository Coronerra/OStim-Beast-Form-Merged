# OStim Beast Form Merged: build notes (0.1 to 0.7)

Technical history of the merged plugin. Only static checks were done on the build; in-game testing was by the author.

## Plugin `OStim_Beast_Form_Merged.esp`
- ESL flag 0x200, 31 records (25 new ESL forms + 6 overrides), local IDs 0x800-0x838.
- Masters (8): Skyrim.esm, Update.esm, Dawnguard.esm, Dragonborn.esm, JS Emissive Eyes SE - Johnskyrim.esp, Growl - Werebeasts of Skyrim.esp, OStim.esp, OCum.esp.
  - Update and Dragonborn are kept so the copied Growl race record's master indices stay byte-identical.
  - No OCreatures.esp master (since 0.2) and no MFA master.
- Master order lists Growl before OStim/OCum. That's fine in SSE, but xEdit may warn.

## 0.1: first merge
- Merged OStim Beast Form (GitHub v0.1), Beast Aware (v1.1), OBeast Lite 0.2, OCum Werewolf Shot (v1.0), OCum Beast Pie 0.1 and the BFA heads/bodies into one ESL.
- Root cause of the "head fell off" bug: HDT Werewolves' `Werewolves.esp` overrides ARMA 000CDD87 with slot 30 (head) on, and OCreatures overrides both beast races with no HEAD parts and no FaceGen flag. The merged plugin's race and ARMA overrides must load after both.
- Race overrides: WerewolfBeastRace = Growl/JS Eyes record plus BFA HEAD parts with FaceGen on; DLC1VampireBeastRace = MFA-style record plus BFA HEADs and the JS VL eye spell.
- ARMA CDD87: BOD2 0x59C (slots 32/33/34/37/38/40, no 30), paths into `coronerra\bfa\`.

## 0.2: OCR made optional
- Removed OCreatures.esp as a master and the two baked OCR keywords. Every other record byte matches 0.1 after the self-index change (9 -> 8).
- `OBF_OCRCompat.RestoreKeywords()` (global) adds OCR's `OCrWerewolfRace` (OCreatures.esp 0x5C58) and `OCrVampireLordRace` (0x5C57) keywords at runtime, only if `Game.GetModByName("OCreatures.esp") != 255`. It uses `PO3_SKSEFunctions.AddKeywordToForm` (Form.AddKeyword doesn't exist in Skyrim SKSE).
- Added 7 uniquely named `OBF*Idle` scenes and `OBF_B_*` fallback animation events (project `OBFMerged`) so the mod can coexist with OCR/Billyy without duplicate IDs. Pandora/FNIS must be regenerated after installing.
- Compiled with Caprica 0.3.0 (game=skyrim). W7000 warnings for `OnPlayerLoadGame` are header-stub noise.

## 0.3: hubs and the male aroused swap
- Restored the standard `OCr*Idle` IDs at OCR's exact scene paths.
- Added the Lite male-only aroused swap back: 831 `OBL_SwapEnabled` GLOB (1), 832 `OBL_OCreaturesPresent` GLOB (0), 833/834 ARMA, 835/836 ARMO, 837 `OBL_MainQuest` + player alias, 838 `OBL_NoStrip` KYWD. The swap returns early when OCreatures.esp is loaded.
- Added `OBFWerewolfIdleMF` for female werewolf + male human (with the WWF_OnTop test scenes, removed in 0.6).

## 0.4: hub model fix and SkyrimNet/OStimNet
- OStim NG has no "hub" concept in code. A hub is an idle/intro scene whose navigations are menu buttons. Another file can add a button to someone else's scene with `origin`. Thread start picks a random node tagged intro/idle that isn't `noRandomSelection`.
- OCR model, now followed: `OCr*Idle` = main hub; each pack adds one pack-page button via `origin`; pack pages list stage 1 of each animation; stages chain Next/Back; Return -> pack page; medallion -> main hub.
- WW FM main hub: Baka / Billyy / FlufyFox pages (3 / 26 / 6 animations). FFM/FMM/FMMM/FMMMM: Billyy. VL: Baka / Billyy / FunnyBiz (2 / 2 / 2). 267/267 sex scenes reachable. FF stays an untagged idle (no FF scenes exist).
- OStimNet: `zz OStim Beast Form Merged SkyrimNet.json` (descriptions for this mod's own scenes only), intent tags on the test scenes (removed in 0.6), and the new prompt-only bundle `coronerra.beastform_ostimnet`.

## 0.5: male body and Beast Load
- Male body `coronerra/bfa/malebodywerewolf_0/_1.nif` rebuilt from the fluffy body with only the head, eyes and teeth removed. WereWolfSheath and WereWolfPenisTip are kept (the knot is back, no groin cap). Shapes match the source vertex for vertex.
- Added BakaFactory ABC `werewolfballs*` and `werewolfpenis_red/_n/_sk` textures needed by the sheath/tip.
- `OCumBeastPie` gained Beast Load and round stacking; `OBF_MCM` gained the "Beast climax (OCum)" section.
- Plugin byte-identical to 0.4 apart from the public-release header description.

### Beast Load design
- Listens to `ostim_actor_orgasm` and exits right away unless the sender is a male werewolf, werebear or Vampire Lord.
- Works in all threads, including NPC-only ones.
- Classifies the finish from scene tags plus actions. Decals use OCum's functions with ThreadID -1, so OCum TL never starts its own 60 s pies from these calls.
- One mesh loop per actor (mod event `obf_beastload_mesh`), with a StorageUtil stamp and item mask. Polls every 2 s during the scene, then every 10 s. After the scene it only re-equips while body slot 32 is empty. Ends when OCum's AppliedCumKeyword effect is gone (timer or bath).
- Round stacking: per-target `OBF_BL_Round` (StorageUtil), capped at MaxRounds (default 5). Each round adds +1 layer per region (max 6) plus 2 mesh items, in slot order 60, 47, 55, 57, 36, 43, 59.
- Not merged: the OCum TL SceneFix pex (it would replace OCum's own script). Keep the [OCum Tull/Liquid/Softbody patch](https://github.com/Coronerra/OCum-Tull-Liquid-Softbody-Patch) as its own mod.

## 0.6: test scenes removed
- Deleted `SKSE/Plugins/OStim/scenes/WWF_OnTop/WWFCowgirl1-1..5.json` (the experimental female cowgirl test). 0.5 shipped those JSONs only; there were no WWF HKX or FNIS lists in the zip.
- `OBFWerewolfIdleMF`: `navigations` is now empty. Tags, actors and the idle animation event are unchanged, so separate female-werewolf packs can still attach to it with `origin`.
- `zz OStim Beast Form Merged SkyrimNet.json`: the five `WWFCowgirl1-*` descriptions removed (15 remain).
- Docs: hub_graph_0.3/0.4.json replaced by hub_graph_0.6.json; STATIC_CHECKS_0.6.txt added; WWF mentions in older docs marked as removed.
- Plugin, PEX, NIF, DDS, HKX byte-identical to 0.5. Same FormIDs and masters; saves stay compatible; no Pandora run.
- Female werewolf scenes are not bundled; they come from separate optional packs.

## 0.7: one installer, TWO body for everyone
- Inputs (published release zips, md5-checked): Merged 0.6 (`OStim_Beast_Form_Merged.esp` d19870fd...), TWO Edition 0.2 (`OStim_Beast_Form_TWO.esp` e21abc1c...), Merged TWO Patch 0.1 (`OStim_Beast_Form_Merged_TWO_Patch.esp` e3a9c335...), TWO Herm Patch 0.1 (`OStim_Beast_Form_TWO_Herm_Patch.esp` c206051c...). All four plugins ship unchanged.
- FOMOD (`fomod/ModuleConfig.xml`): pages Growl/TWO, softbody No/Yes, Herm, acknowledgement; folders `00 Common`, `10 Growl`, `11/12 Growl (No) Softbody`, `20 TWO`, `21/22 TWO (No) Softbody`, `30 Softbody`, `40 Herm`. Validated against the FOMOD 5.0 `ModuleConfig.xsd` (fomod-schema 5.0; its one stray space in `type=" xs:string"` was fixed locally for the validator).
- `00 Common` = the 354 files Merged 0.6 and TWO Edition 0.2 share byte for byte, plus the new `OBL_Main`. Per-option: `OBF_MCM`, actor-property JSONs (`"mod"`), SkyrimNet manifests and the OStimNet bridge prompt.
- Two new plugin builds, each one record away from a published plugin:
  - `12 Growl No Softbody/OStim_Beast_Form_Merged_TWO_Patch.esp`: TWO Patch 0.1 records unchanged + ARMA `08000833` (Merged's `OBL_WerewolfAddonAA`) = TWO Edition's 0x833 record (MOD2 `actors\werewolfbeast\character assets\CreatureFramework\CanineRedHard.nif`, slot 52; RNAM/SNDD point at Skyrim.esm only). HEDR 5 -> 6 records.
  - `21 TWO Softbody/OStim_Beast_Form_TWO.esp`: TWO Edition 0.2 with ARMA `08000833` replaced by Merged 0.6's record byte for byte (MOD2 `MoreNastyCritters\werewolf\Addon_Dog_Black_Hard.nif`).
- Dropped from the Growl files (unused once TWO's body and heads win): `coronerra\bfa\` bodies, `werewolfhead*`, `werewolfteeth`, `eyesmalewerewolfbeast` NIF/TRI, `hdtSkinnedMeshConfigs\WerewolfFemale.xml`, `textures\actors\character\werewolf\coronerra\`. The ABC `werewolfballs*` / `werewolfpenis_*` textures used by the sheath are byte-identical in TWO Core and no longer shipped.
- Softbody-only content (`30 Softbody`): `MoreNastyCritters\werewolf\Addon_Dog.nif`, `Addon_Dog_Black_Hard.nif`, `Addon_Dog_Red_Hard.nif` (GT Softbody, Goutou) and `werewolf_balls{,_n,_sk}.dds`, `werewolf_canine_penis_{black,red,n,sk}.dds`.
- Scripts (Caprica, game=skyrim): `OBL_Main` gains `AddonMeshPath()`; `Setup()` sets `WerewolfMesh` from the 0x833 armor addon's male model before `MiscUtil.FileExists`. `OBFHerm_Main` resolves `AddonMesh` the same way, with the 0.1 logic as fallback. No properties or variables added or removed. PEX headers carry only the script name.
- BFA head plugins are installed with both options (they were optional add-ons).
- Static checks: `Data/Docs/OStim Beast Form Merged/STATIC_CHECKS_0.7.txt` (schema, folder references, all 8 installer combinations simulated: no file conflicts, expected plugins, winning 0x833 path and mesh present, every mesh texture resolvable, no TWO file shipped, plugin identities, privacy).
- Not tested in game.
