# Changelog: OStim Beast Form Merged

## 0.7.2
- **Beta: the softbody Yes female body and the softbody cock setup are not tested in game yet.**
- Docs: cover image (`docs/OStim_Beast_Form_cover.jpg`) and a link to the separate, LoversLab-exclusive [OStim Beast Form Starter Animation Pack](https://www.loverslab.com/files/file/52869-ostim-beast-form-starter-animation-pack/).
- **Known Incompatibilities (as of this release)** section added to both READMEs and the installer: [Diverse Werewolves Collection SE](https://www.nexusmods.com/skyrimspecialedition/mods/7009) by opusGlass; [TWO's TWO_SkinSwapper.dll (v0.2.1, part of TWO Extras)](https://www.loverslab.com/topic/159911-two-total-werewolf-overhaul/) by Frosferes.
- **Softbody Yes no longer ships GT Softbody files.** Removed `meshes/MoreNastyCritters/werewolf/Addon_Dog.nif`, `Addon_Dog_Black_Hard.nif`, `Addon_Dog_Red_Hard.nif` and the seven `werewolf_balls*` / `werewolf_canine_penis_*` textures from `30 Softbody`.
- **Softbody TWO cock:** `meshes/actors/werewolfbeast/character assets/coronerra/twosoftbody/CanineRedHard.nif` = TWO 4.1's `CreatureFramework/CanineRedHard.nif` with only its SMP config path changed, to `SKSE/Plugins/hdtSkinnedMeshConfigs/coronerra/OBF_TWOSoftbodyGenitals.xml` (TWO's `HDTWerewolfGenitals.xml` + a second tag, `VirtualPenis`, so GT Softbody's vaginal/anal guide tubes react to it). Geometry, weights and TWO's textures are unchanged.
- **Softbody TWO female body:** `coronerra/twosoftbody/femalebodywerewolf_0.nif` / `_1.nif` = TWO 4.1's female body with:
  - 16 new bones `VaginaD{B,F,R,L}00`-`03` (GT Softbody names) as children of `VaginaDeep1`, placed along TWO's canal (z 69.4 to 74.8). FSMP merges them into the skeleton at runtime, so no skeleton edit or extra DLL is needed.
  - `Female Insides`: the 177 canal vertices are reweighted onto those chains (vulva, anus and the outer body untouched; geometry, UVs, textures unchanged).
  - New hidden shape `Collision Vagina Deep` (133 vertices, 222 triangles, no shader): the canal wall, weighted like the visible canal. TWO's own collision covers only the vulva and the cervix cap.
  - SMP config `coronerra/OBF_TWOSoftbodyFemale.xml` = TWO's `HDTWerewolfFemale.xml` + the canal chains (GT Softbody 3.38 values, named templates only) + the new collision shape. Morph file `coronerra/twosoftbody/femalebodywerewolf.tri` = TWO's TRI + the same morphs for the new collision shape.
- **Plugins (softbody Yes only):** `11 Growl Softbody/OStim_Beast_Form_Merged_TWO_Patch.esp`: ARMA `NakedTorsoWerewolfBeast` (000CDD87) female paths -> the softbody body, plus ARMA `OBL_WerewolfAddonAA` (0x833) -> the softbody TWO cock. `21 TWO Softbody/OStim_Beast_Form_TWO.esp`: 0x833 -> the softbody TWO cock, plus an ARMA 000CDD87 override (TWO 4.1's `Werewolves.esp` record with only MOD3/MOD5 changed). Same FormIDs and masters; saves keep working.
- **Softbody Yes: OCum script patch included.** `30 Softbody/Scripts/OCumMaleScript.pex` + `Scripts/Source/OCumMaleScript.psc` = [OCum-Tull-Liquid-Softbody-Patch](https://github.com/Coronerra/OCum-Tull-Liquid-Softbody-Patch) v1.0 (OCum Ascended 4.1.1 `OCumMaleScript` + Tull/Liquid add-on + Scene Change Fix + GT Softbody's two OCum fixes). Falls back to OCum's own meshes without Tull/Liquid Pack. Must win over GT Softbody's optional `Patch/OCum` file (same in GT 3.37.2 and 3.38): load this mod after GT - Softbody.
- Softbody No: unchanged from 0.7.1.
- Docs: Diverse Werewolves Collection SE (Nexus 7009) reported as not compatible (camera locks to the side).
- Installer acknowledgement, README and docs: the Frosferes wording is now "Frosferes is okay with patches but I will not repackage any files he made that I did not have to patch. So non-softbody female bodies and all Male bodies are still dependant on his TWO bodies." (replaces 0.7.1's wording).

## 0.7.1
- **Removed every Vampire Lord mesh, head morph and texture** from `00 Common` (13 files), so the mod no longer overwrites other mods' files:
  - `meshes/actors/vampirelord/character assets/`: `vampirelordhead.nif`, `vampirelordfemalehead.nif`, `vampirelordeyes.nif`, `vampirelordfemaleeyes.nif`, `body/vampirelord.nif`, `body/vampirelordfemale.nif` (byte-identical to MFA's), `vampirelordhead.tri`, `vampirelordfemalehead.tri` (MFA + BFA extended versions that overwrote MFA's).
  - `meshes/MoreNastyCritters/vampirelord/vampirelord_Hard.nif` and `textures/MoreNastyCritters/vampirelord/vampirelord_penis_{color,m,normal,sk}.dds` (identical to OCreatures Reforged's; the color map overwrote ABC's different one).
- Plugins are unchanged (same md5s as 0.7). Their Vampire Lord head parts point at MFA's paths, which MFA provides. `OBL_VampireLordAroused` still points at `MoreNastyCritters\vampirelord\vampirelord_Hard.nif`; `OBL_Main` already skips the VL swap when that loose file is missing.
- Kept: Vampire Lord scene/hub JSONs, actor properties, scripts and the Billyy VL fallback HKX (`Vamp_B_Dog_A2_S1.hkx` + FNIS list).
- Load order: no file overlap with MFA any more, so the "this mod must win against MFA" rule is gone. Still below OCreatures Reforged (idle JSONs; softbody Yes `addon_dog*.nif`) and still above TWO.
- FOMOD acknowledgement, README and docs now say "TWO is used with Frosferes's blessing". The rest of the acknowledgement is unchanged.
- Docs: note that TWO Extras' `TWO_SkinSwapper.dll` (0.2.1, 2022) doesn't support Skyrim 1.7.99 / 1.7.104 (new Address Library format), so TWO's herm / urta body swap doesn't work there. Not caused by this mod.

## 0.7
- **One download, one installer.** OStim Beast Form Merged, OStim Beast Form - TWO Edition, OStim Beast Form Merged - TWO Patch and OStim Beast Form TWO Herm Patch are now one zip (`OStim_Beast_Form_Merged_0.7.zip`) with a four-page FOMOD:
  1. **TWO user or Growl user**: pick one; Growl is ticked by default and recommended for Nolvus users.
  2. **Do you use softbody?**: No (default) or Yes.
  3. **Hermaphrodite patch? A.K.A. Fruta?**: optional, unticked.
  4. **Read and acknowledge**: one required "I have read and understand" box with the TWO notice and the source link.
- **Every setup uses the TWO - Total Werewolf Overhaul 4.1 body (Frosferes).** TWO is required and not included. The HDT Werewolves female body, the ABC / Fluffworks-style male body, their SMP config and the BFA werewolf heads are no longer shipped (the 0.6 plugin's records for them stay, unused, so FormIDs don't change).
- **Growl option** installs `OStim_Beast_Form_Merged.esp` (byte-identical to 0.6) and `OStim_Beast_Form_Merged_TWO_Patch.esp` (byte-identical to TWO Patch 0.1 with softbody Yes). Saves from Merged 0.6 + TWO Patch 0.1 keep working.
- **TWO option** installs `OStim_Beast_Form_TWO.esp` (byte-identical to TWO Edition 0.2 with softbody No). Saves from TWO Edition 0.2 keep working.
- **Softbody choice.** No: no GT Softbody files; male werewolves wear TWO's own hard canine (`CreatureFramework\CanineRedHard.nif`, TWO Core) in scenes. Yes: the GT Softbody cock (`MoreNastyCritters\werewolf\Addon_Dog_Black_Hard.nif`) and its textures, as in 0.6. The Growl+No and TWO+Yes plugins differ from the published ones only in `OBL_WerewolfAddonAA` (0x833).
- **Hermaphrodite option** installs `OStim_Beast_Form_TWO_Herm_Patch.esp` (byte-identical to Herm Patch 0.1) with a recompiled `OBFHerm_Main` that follows the softbody choice.
- **BFA brow morphs** for TWO's heads are always installed (they were an optional add-on in the TWO Edition and TWO Patch).
- `OBL_Main` and `OBFHerm_Main` read the aroused mesh path from the aroused item's armor addon (SKSE `Armor.GetNthArmorAddon` / `ArmorAddon.GetModelPath`) instead of a saved string, so existing saves follow the softbody choice. No new properties; same FormIDs.
- The ABC sheath textures (`werewolfballs*`, `werewolfpenis_*`) are no longer shipped: byte-identical copies come with TWO Core.
- The TWO Edition, TWO Patch, Herm Patch and original OStim Beast Form repos are marked deprecated and point here. Their releases stay up.

## 0.6
- Removed the experimental WWF_OnTop female cowgirl test scenes (`WWFCowgirl1-1` to `1-5`), their "WW Female Cowgirl 1 (TEST)" button on `OBFWerewolfIdleMF` and their OStimNet descriptions.
- Female werewolf scenes come from separate, optional scene packs, which add their own button to the female werewolf hubs.
- Plugin, FormIDs, masters, scripts, meshes, textures and HKX unchanged from 0.5. Saves compatible. No Pandora run needed.

## 0.5
- Male werewolf body restored with its sheath and knot; Beast Load (OCum) heavy beast climax with multi-round stacking; new "Beast climax (OCum)" MCM section.

## 0.4
- Hub model fix (OCR-style main hub with one button per pack), group hubs, SkyrimNet / OStimNet scene descriptions and the OStimNet bridge prompt bundle.

## 0.3
- Standard `OCr*Idle` hub IDs restored; male-only aroused swap (Beast Lite) added back.

## 0.2
- OCreatures made optional (no master; OCR keywords restored at runtime); fallback idles with their own animation events.

## 0.1
- First merge of OStim Beast Form, OStim Beast Lite, Beast Aware, OCum Werewolf Shot, OCum Beast Pie and the BFA heads/bodies into one ESL.

See [BUILD_NOTES.md](BUILD_NOTES.md) for record-level details.
