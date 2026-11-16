# OStim Beast Form Merged: build notes (0.1 to 0.7.2)

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

## 0.7.1: no Vampire Lord meshes
- `stage.py` adds `meshes/actors/vampirelord/character assets/`, `meshes/MoreNastyCritters/vampirelord/` and `textures/MoreNastyCritters/vampirelord/` to the dropped list (13 files). Everything else, including all six plugins, is byte-identical to 0.7.
- Conflict re-check against TWO 4.1, TWO Alternate Textures, MFA, OStim 7.5.1c, OCum 4.1.1 (+ Tull/Liquid add-ons), GT Softbody 3.37.2, OCR 1.9, Growl (BSA), JS Emissive Eyes, BFA 5.0.6, Ostrands with Werewolves, OCum Werewolf Shot and ABC: 34 overlaps left (was 49), none with MFA. Remaining: OCR idle JSONs (ours must win), softbody `addon_dog*.nif` (identical to GT Softbody, ours must win vs OCR/ABC), the 7 softbody MNC textures (identical) and OCum Werewolf Shot's urethra node (identical; keep Werewolf Shot off).
- FOMOD acknowledgement text updated ("TWO is used with Frosferes's blessing"). `verify.py` checks it, and that no VL nif/tri/dds is shipped. Static checks: `STATIC_CHECKS_0.7.1.txt`.

## 0.7.2: softbody-ready TWO cock and female body
- Inputs: TWO 4.1 Core (`femalebodywerewolf_0/_1.nif`, `femalebodywerewolf.tri`, `CreatureFramework/CanineRedHard.nif`, `HDTWerewolfFemale.xml` df0ee695..., `HDTWerewolfGenitals.xml` 6ef59460..., `Werewolves.esp` 687df73c...) and GT Softbody 3.38 (`Physical GT/.../Xml Addon/FemaleCollisionHandVaginaAnal.xml`, values only).
- GT 3.38 has no werewolf body support; its creature options are MNC cock meshes or ABC collision XMLs. TWO's female body already has full SMP (breasts, belly, butt, thighs, vulva, anus, tail) and its collision accepts GT's `penis` tag, but it has no collision between the vulva (z 66-69) and the cervix cap (z 75-77.6).
- Canal bones: GT frame convention (local y = outward radial, local z = canal axis pointing deep, chain 00 deep -> 03 opening along local -z), offset 0.2 from the fitted canal centerline, spacing 1.80. Locals are relative to the skeleton's `VaginaDeep1` (0, -4.2409, 71.04), which matches the shapes' skin-to-bone data (the body nif's flat nodes are 0.28 off in y).
- FSMP `doSkeletonMerge` attaches armor nodes missing from the skeleton under their matched parent, so the 16 bones need no XPMSE/TWO skeleton change and no MuSkeletonEditor.
- Weights: quadrant cosine blend x linear blend between levels, alpha ramps from 0 at the vestibule to 1 in the canal and back to 0 at the cervix cap, max 4 influences, renormalized. Identical on `_0` and `_1`.
- XML: named `bone-default` / `generic-constraint-default` templates only (an unnamed default would change the template FSMP uses for undeclared collision-shape bones). Canal shape: per-triangle, margin 0.2, penetration 0.4, tag `pussy`, no-collide body/pussy/anus (TWO's Collision Vagina rules). Values are a starting point for in-game tuning.
- Plugins: built by `esp/build_variants_072.py` from the 0.7.1 softbody variants; FormIDs unchanged, HEDR +1 record each.
- Not done: GT's 56-bone `Soft_*` breast grid (TWO already simulates breasts, belly, butt and thighs), GT anus chains, GT guide tubes on the werewolf. Not tested in game.
- OCum script (softbody Yes, `30 Softbody/Scripts`): `OCumMaleScript.pex` 444b98cf... + `Source/OCumMaleScript.psc` 635b1f5f... = the OCum-Tull-Liquid-Softbody-Patch v1.0 release files. The pex disassembles identically to the build-machine merge (9a4931ae...) the author runs in game; only the pex header's compiler user/machine strings differ. GT Softbody 3.38's optional `Patch/OCum/Scripts/OCumMaleScript.pex` is byte-identical to 3.37.2's (42b46226...), so the merge is current for 3.38. Beast Load (`OCumBeastPie`) calls `ApplyCum*` / `CumOntoArea`, whose signatures are unchanged in the merged script.
- OCum spurt direction checked: `UrethraNodeWerewolf.nif` `Urethra` node, local T (2,0,0) and R [[0,1,0],[1,0,0],[0,0,-1]] under `WWD 9` (Prn). OCum aims along the node's world y axis = WWD 9's local x = the shaft axis, so it already fires straight out of the tip; the nif is unchanged.
- Frosferes wording (installer acknowledgement, READMEs, AI_CONTEXT): "Frosferes is okay with patches but I will not repackage any files he made that I did not have to patch. So non-softbody female bodies and all Male bodies are still dependant on his TWO bodies." TWO-derived files shipped, none byte-identical to any TWO 4.1 file (checked): softbody `CanineRedHard.nif` (SMP config path changed), `femalebodywerewolf_0/_1.nif` (canal bones, reweights, canal collision), `femalebodywerewolf.tri` (+ morphs for the new shape), `OBF_TWOSoftbodyFemale.xml` / `OBF_TWOSoftbodyGenitals.xml` (TWO's XMLs + canal chains / `VirtualPenis` tag), `ExpHeadWerewolf_BFA.tri` x2 (TWO's TRI + `browupleft` / `browupright`).

## 0.8 (beta) notes
- Base: the 0.7.2 release package. The 0.8 scene files, OStimNet descriptions, unlock table, FOMOD page and static checks were generated by build-machine scripts (not in this repo); see STATIC_CHECKS_0.8.txt / 0.8.1.txt in Data/Docs.
- OStim sorts the penis-having actor first on its own start key -> male-first (MF) copies with animationIndex remap; OCR-style [F,M] idles kept too.
- Scene ID = filename; her hub overrides use the same relative path so MO2 replaces them (BF below her pack).
- Public wording: forced scenes are described as "forcefully taking" or "aggressively taking". Lirael = converter, animators are Billyy, Anub, FlufyFox, Baka, FunnyBizness, MNC team, MadMansGun.
- No herm/futa unlocks (author decision; herm handling stays with the Herm option). 0.8 animations tested in game by the author; the 0.8.1 face fix is not.

## 0.8.1 notes
- OCumBeastPie.FaceFinish(sid, pos, tp, oral, vag, anal, outside, guessed) decides face per partner from the climax stage's actions: beast is actor of vaginalsex/wwfvaginalsex/analsex on anyone -> no face; partner is actor of blowjob/deepthroating/penilelicking/handjob/footjob/boobjob on him, or he is actor of facial/rubbingpenisagainstface on her -> face; he is in another partner's mouth/face -> no face; else tags (internal tag beats oral tag; guessed outside -> no face).
- GlazeActorFace(..., face): face=false strips ApplyCumFacial/ApplyCumMouth/BreastFace and sets meshSet bit 8, which ItemMask uses to drop face items 4/5/6 (also from round stacking).
- Compile: Caprica 0.3.0 (game=skyrim, OStim 7.5.1c sources, OCum Ascended 4.1.1 + merged OCumMaleScript, SkyrimNet headers, NiOverride/MiscUtil/SkyUI stubs). Baseline recompile of the 0.8 source disassembles identically to the shipped 0.8 pex (only a case difference in one property-name string). PEX header strings carry only the script name.
