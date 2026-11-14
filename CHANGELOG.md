# Changelog: OStim Beast Form Merged

## 0.7
- **One download, one installer.** OStim Beast Form Merged, OStim Beast Form - TWO Edition, OStim Beast Form Merged - TWO Patch and OStim Beast Form TWO Herm Patch are now one zip (`OStim_Beast_Form_Merged_0.7.zip`) with a four-page FOMOD:
  1. **TWO user or Growl user**: pick one; Growl is ticked by default and recommended for Nolvus users.
  2. **Do you use softbody?**: No (default) or Yes.
  3. **Hermaphrodite patch? A.K.A. Fruta?**: optional, unticked.
  4. **Read and acknowledge**: one required "I have read and understand" box with the TWO / takedown notice and the source link.
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
