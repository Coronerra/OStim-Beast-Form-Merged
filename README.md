# OStim Beast Form Merged 0.7

> **GitHub edition of the mod page.** Download the mod from the **[v0.7 release](https://github.com/Coronerra/OStim-Beast-Form-Merged/releases/tag/v0.7)** (`OStim_Beast_Form_Merged_0.7.zip`). This repo holds the open-source parts: Papyrus sources, SkyrimNet bundles, OStim JSON, the FOMOD installer and docs. AI assistants: start with **[AI_CONTEXT.md](AI_CONTEXT.md)**. History: [CHANGELOG.md](CHANGELOG.md) and [BUILD_NOTES.md](BUILD_NOTES.md). License: [MIT for coronerra's work; third-party assets belong to their authors](LICENSE).

**Skyrim SE / AE · OStim Standalone · ESL-flagged plugins · FOMOD installer · by coronerra**

Play as a werewolf in OStim with your mind intact.

---

## ⚠️ One download for everyone (new in 0.7)

**0.7 replaces every earlier OStim Beast Form download.** There is now **one zip with one installer**, and every setup uses the **[TWO - Total Werewolf Overhaul](https://www.loverslab.com/topic/159911-two-total-werewolf-overhaul/) 4.1 body by Frosferes**. TWO is **required** for everyone and is **not included**. Get it from its LoversLab page.

The installer asks four things:

| Page | Question | Choices |
|---|---|---|
| 1 | **TWO user or Growl user** | **Growl user** (ticked by default, **recommended for Nolvus users**) or **TWO user** (no Growl). Pick one. |
| 2 | **Do you use softbody?** | **No** (ticked by default) or **Yes**. Pick one. |
| 3 | **Hermaphrodite patch? A.K.A. Fruta?** | Optional checkbox, unticked. Only for TWO Extras' herm / urta player werewolf. |
| 4 | **Read and acknowledge** | One required box: "I have read and understand". |

**Read every page.** If you pick the wrong options, the mod won't work.

The old separate downloads are **deprecated**. Their repos and releases stay up, but they are no longer updated: [OStim Beast Form - TWO Edition](https://github.com/Coronerra/OStim-Beast-Form-TWO), [OStim Beast Form Merged - TWO Patch](https://github.com/Coronerra/OStim-Beast-Form-Merged-TWO-Patch), [OStim Beast Form TWO Herm Patch](https://github.com/Coronerra/OStim-Beast-Form-TWO-Herm-Patch) and the original [OStim Beast Form](https://github.com/Coronerra/OStim-Beast-Form). Coming from one of them? See [Updating to 0.7](#updating).

> **About the TWO body:** this mod uses the TWO body made by Frosferes, at the LoversLab community's request. If Frosferes comes out of retirement and asks for it to be taken down, it will be taken down with no further support, no questions asked. Until then, anyone is free to make their own patches, hubs and mods based on this one.

---

## ⚠️ WARNINGS

**1. THIS IS NOT A CREATURE OR CRITTER MOD!** THIS IS A MOD TO UNLOCK ONE OF THE 2 SENTIENT RACES OSTIM LEAVES OUT (WEREWOLVES AND VAMPIRE LORDS). THIS MOD FOCUSES ON THE WEREWOLF. IF IT IS A SUCCESS, I WILL CREATE A VAMPIRE LORDS ONE TO CREATE A WHOLE OSTIM UNDERWORLD MOD.

**2. THIS HAS NO ANIMATIONS.** LIRAEL HAS PROMISED TO MIX HER CONVERTED OSTIM ANIMATION PACKS TO CREATE A MERGER PACK WITH ONLY VAMPIRE LORD AND WEREWOLF ANIMATIONS, FREE FOR THE PUBLIC, WHEN I'M READY TO TRY RELEASING THIS ON NEXUS. IN THE MEANTIME YOU WILL NEED TO USE HER OTHER PACKS.

*The scene menus in this download point at animations from Lirael Atelier's converted OStim packs. If none of her packs are installed, there is nothing to play. The packs used during development (Billyy, BakaFactory, FlufyFox, FunnyBiz) are **not** included, but Lirael has posted many of them **for free on LoversLab**: see [her LoversLab uploads](https://www.loverslab.com/profile/6654496-lauffey/content/?type=downloads_file) (her LoversLab account is **Lauffey**). Links are under Requirements.*

---

## 📖 Description

**This is not a bestiality mod.** It is a sentient race mod. It treats werewolves the same way the game treats Argonians and Khajiit: as people.

When you transform, the game itself changes your race to werewolf. OStim then has no idea what to do with you. This mod fills that gap. As a werewolf you keep the full mind of a sentient being, the way a Khajiit would, and you can be intimate with your partner without first turning back.

If you ever wanted it all in one werewolf (the body, the talking head, the scenes, the cum, NPCs who know what you are) but the mods kept fighting each other, this is as close as I could come to giving you that.

I made this just to see if it could be done. **Everything I made for it is open source.** If you want to make custom bodies, textures or anything else for it, you're welcome to. Go for it.

### What it does (0.7)

**Beast-form scenes**
- A start-scene hotkey that works while transformed. Beast form blocks normal activation, so the mod uses its own key. You set it in the MCM. It can be the same key as OStim's activation key, and that works fine (I use the Up Arrow for both).
- Your beast-form timer pauses during a scene and picks up again when the scene ends.
- OStim recognizes werewolves (and Vampire Lords) as their own actor types, so it picks matching scenes from any installed pack.
- **Hub menus:** the werewolf hub shows one button for each installed pack that has werewolf scenes (for example Baka, Billyy and FlufyFox). Each button opens a page with only that pack's werewolf animations. A werewolf medallion icon takes you back to the main hub. Group hubs (3 to 5 actors) are included too.

**Werewolf body: TWO**
- Werewolves use TWO's bodies, heads, skeleton, SMP and textures (and TWO Alternate Textures, if you use them). Nothing of TWO's is shipped or edited. You need your own copy of TWO 4.1.
- **Growl option:** Growl keeps its gameplay, and male werewolves keep the limp sheath, penis tip and knot from earlier versions, sitting on TWO's body.
- **TWO option:** the werewolf race stays TWO's. Outside scenes, male genitals are whatever you picked in TWO's own installer.
- **Aroused cock in scenes (male werewolves):** with softbody **Yes**, the GT Softbody cock with softbody physics. With softbody **No**, TWO's own hard canine (from TWO's Core files), so nothing extra is needed. If OCreatures is loaded, the swap steps aside and lets OCreatures handle it.

**Talking heads**
- TWO's werewolf heads talk and emote through Monster Facial Animation (MFA). The installer also adds the two brow-raise morphs Better Facial Animations (BFA) needs, so BFA works on them too. Without BFA, they are simply unused.
- Vampire Lord heads are separate talking head parts, built so that MFA and BFA can animate them.

**Beast climax (OCum)**
- When a **male werewolf** climaxes in any OStim scene, his partner gets a massive load. That includes your scenes and NPC-only scenes. Werebears and Vampire Lords are handled the same way.
  - **Vaginal / anal:** heavy creampie overlays, plus Tull/Liquid creampie meshes if you have those mods.
  - **Footjob, handjob, masturbation and other outside finishes:** belly, chest, butt and legs are covered, plus feet or hands where it fits. OCum's cum-shot spurts also play on outside finishes in your own scenes.
  - **Blowjob / oral:** not swallowed. Her face, mouth, neck and chest are left covered and dripping.
  - **Huge load** (on by default): OCum's heaviest textures on every area, the full mesh set, and the beast never runs dry.
- This works whatever OCum's own MCM says about meshes, vaginal/anal overlays or creampie chance.
- **Multi-round stacking** (on by default): if OStim keeps the scene going after he cums, each climax adds another layer and more meshes. **Max stacked rounds** goes from 1 to 10, default 5.
- **How long it lasts:** it follows OCum's cleanup timer, which defaults to about 5 real minutes. Raise OCum's "cum cleanup timer" for longer. It washes off in water like normal OCum cum.
- After the scene, meshes are only put back on while she's naked, so they never fight her armor.
- ⚠️ **Ring slot:** the torso drip mesh uses slot 36, the ring slot. A ring she's wearing comes off while the torso drip is on.

**Hermaphrodite (Fruta) option**
- For TWO Extras' herm / urta **player** werewolf (TWO Extras' "Toggle Herm Werewolf" spell). OStim then treats your herm or urta werewolf as having a penis as well as a vagina and breasts, so the male-werewolf-role scenes can be offered. The aroused cock and Beast Load climax run for her too. Regular female werewolves (including Aela) are unchanged.
- Needs TWO Extras (`WerewolvesExtras.esp`), and TWO's `WerewolvesExtrasGrowl.esp` if you use Growl. Leave OStim's MCM option "Futas use male role" on (the default).
- I am not going to test this myself. If you use TWO's herm or urta werewolf, please test it and report any problems in the support section of the [OStim Beast Form Merged](https://www.loverslab.com/files/file/52768-ostim-beast-form-merged/) page on LoversLab.

**SkyrimNet / OStimNet (optional)**
- **Beast Aware:** SkyrimNet NPCs are told when you shift into or out of beast form.
- **Beast Form OStimNet Bridge:** while you're a werewolf or Vampire Lord, nearby NPCs know they can still pick you as an OStimNet partner. They still decide by their own personality. Leave OStimNet's "Nearby actors humanoid only" **ON**.
- OStimNet scene descriptions are included for this mod's own scenes.

**MCM: OStim Beast Form**
- Start-scene hotkey, fallback search radius, Try StopCombat, Pause beast timer for ANY OStim scene, and debug messages.
- **Beast climax (OCum):** Werewolf/VL cum on partner, Huge load, Tull/Liquid meshes, Spurts on outside finishes, Stack cum across rounds, and Max stacked rounds (1 to 10).

### 🐾 Vampire Lords
Vampire Lord support is early groundwork: actor typing, hubs, the aroused swap, climax handling and talking heads. It is **not finished**. A full Vampire Lord release is planned if the werewolf release goes well.

### 🙏 CALL FOR HELP: FEMALE WEREWOLF ANIMATIONS
This works fine for **male** werewolves. **Female werewolf scenes are not bundled with this mod.** The female werewolf body now comes from TWO, and the mod includes a female werewolf + man hub and a female werewolf + woman hub that separate, optional scene packs can add buttons to. Without such a pack, the female werewolf + man hub is just an idle with no buttons.

**Animators, this is a call-out to you.** If you can make female werewolf scenes, or want to try, please get in touch in the support thread. The community can help too: test, give feedback and spread the word. The body is waiting. It needs animations.

---

## 📋 Requirements

Get every requirement from its original page and support its author. **Nothing below is bundled** unless I say so.

### Everyone
- **[TWO - Total Werewolf Overhaul](https://www.loverslab.com/topic/159911-two-total-werewolf-overhaul/) 4.1** by **Frosferes** (LoversLab). Core is required. See [TWO installer choices](#two-choices).
- **[Monster Facial Animation (MFA) - Special Edition](https://www.nexusmods.com/skyrimspecialedition/mods/22878)** (`MonsterLipSync1.esp`). It is a **hard master** of TWO and of this mod's plugins. The game won't start without it.
- [OStim Standalone](https://www.nexusmods.com/skyrimspecialedition/mods/98163) by **VersuchDrei** and the OStim team (`OStim.esp`)
- [OCum Ascended](https://www.nexusmods.com/skyrimspecialedition/mods/77506) by **Aietos** (with OsmosisWrench and Sairion350) (`OCum.esp`)
- [SKSE64](https://skse.silverlock.org/), [Address Library for SKSE Plugins](https://www.nexusmods.com/skyrimspecialedition/mods/32444) (**meh321**), [SkyUI](https://www.nexusmods.com/skyrimspecialedition/mods/12604) (**schlangster**), [PapyrusUtil SE](https://www.nexusmods.com/skyrimspecialedition/mods/13048) (**exiledviper** and **meh321**), [RaceMenu](https://www.nexusmods.com/skyrimspecialedition/mods/19080) (**expired6978**), [powerofthree's Papyrus Extender](https://www.nexusmods.com/skyrimspecialedition/mods/22854) (**powerofthree**), [XPMSSE](https://www.nexusmods.com/skyrimspecialedition/mods/1988) (**Groovtama**)
- [FSMP - Faster HDT-SMP](https://www.nexusmods.com/skyrimspecialedition/mods/57339) by **DaydreamingDay** and contributors (TWO's physics)
- **Pandora** or another behavior engine: [Pandora Behaviour Engine+](https://www.nexusmods.com/skyrimspecialedition/mods/133232) by **Monitor221hz**. This mod adds a small set of fallback animation events, so you have to regenerate behaviors.
- **At least one OStim animation pack with werewolf scenes.** Right now that means **Lirael Atelier's** converted packs. Many of them are **free on LoversLab**: [all of Lirael's LoversLab uploads](https://www.loverslab.com/profile/6654496-lauffey/content/?type=downloads_file) (account **Lauffey**). Built and tested against:
  - OCreatures - Billyy Animation Pack COMPLETE (animations by **Billyy**): [Byllis Creature Animation pack Complete - OStim edition](https://www.loverslab.com/files/file/51449-byllis-creature-animation-pack-complete-ostim-edition) (free on LoversLab)
  - FlufyFox OStim - Creatures v0.5.2 (animations by **FlufyFox**): [FluffyFox Creatures animation pack - OStim Conversion](https://www.loverslab.com/files/file/51860-fluffyfox-creatures-animation-pack-) (free on LoversLab)
  - FunnyBiz OStim - Creatures v0.2.3 (animations by **FunnyBiz**, Vampire Lord): [FunnyBiz Creature Animations for OStim Standalone](https://www.loverslab.com/files/file/52667-funnybiz-creature-animations-for-ostim-standalone) (free on LoversLab)
  - OCreatures - Baka Animation Pack v0.1-dev (animations by **BakaFactory**): the creature version isn't on LoversLab yet. Check [Lirael's Patreon](https://www.patreon.com/LiraelAtelier) [LINK NEEDED]
  - You can support Lirael on [Patreon](https://www.patreon.com/LiraelAtelier). Her free updates and new conversions are posted there too.
- **Other OStim animation packs that include werewolf animations may work, but they haven't been tested yet.** Please report what you find.

### Growl option only
- [Growl - Werebeasts of Skyrim](https://www.nexusmods.com/skyrimspecialedition/mods/31245) by **EnaiSiaion** (hard master)
- [JS Emissive Eyes SE](https://www.nexusmods.com/skyrimspecialedition/mods/60108) by **johnskyrim** (hard master)
- TWO's own Growl patch (`WerewolvesGrowl.esp`, ticked in TWO's installer)

### Softbody Yes only
- [SOFTBODY (GT - Softbody)](https://www.nexusmods.com/skyrimspecialedition/mods/152103) by **Goutou** (see its own requirements). Pick **No** on the softbody page if you don't run it. That includes UNP users, and CBBE or UBE users without softbody.

### Hermaphrodite option only
- TWO Extras (`WerewolvesExtras.esp`, part of TWO), plus `WerewolvesExtrasGrowl.esp` if you use Growl.

### Not needed any more
HDT Werewolves, Animated Beast's Cocks (ABC), Creature Framework, HCOS, SOS and SexLab are **not** needed. **HDT Werewolves must be off:** its plugin is also named `Werewolves.esp` and cannot run next to TWO.

### Optional
- [Better Facial Animations (BFA)](https://www.nexusmods.com/skyrimspecialedition/mods/193598) by **Cyberquach**. In BFA's race filters, tick **WerewolfBeastRace** and **DLC1VampireBeastRace**.
- [OCreatures Reforged](https://dwemermods.com/mods/5173) 0.1.9 by **Lirael Atelier** ([Patreon](https://www.patreon.com/LiraelAtelier)). **Not required, but fully compatible.** See **OCreatures Reforged compatibility** below.
- [SkyrimNet](https://www.nexusmods.com/skyrimspecialedition/mods/198346) by **MinLL** and the SkyrimNet team, [OStimNet](https://dwemermods.com/mods/2761) by **tetherball88**, and [OStim Navigator](https://github.com/tetherball88/OStimNavigator) by **tetherball88**. These are needed for Beast Aware and the OStimNet bridge.
- [Tull Animated Creampie](https://dwemermods.com/mods/3535) by **Tullius Channel** and **Emotional Trash Can**, plus **[Predator] Liquid Pack v2** by **PredatorRJ** [LINK NEEDED]. Without them you still get all of OCum's textures.
- [OCum Ascended - Tull and Liquid Pack Meshes](https://dwemermods.com/mods/5304) by **Blacksheepo815**, and my [OCum + Tull/Liquid + GT Softbody merged script patch](https://github.com/Coronerra/OCum-Tull-Liquid-Softbody-Patch). Keep that patch as its own mod.
- TWO - Alternate Textures (textures only; any choice is fine).
- **Ostrands with Werewolves** (separate download, see [below](#ostrands)).

---

<a id="two-choices"></a>

## 🐺 TWO installer choices

Install TWO 4.1 with its own installer **before** this mod:
- **Core:** yes (required).
- **Genitals:**
  - Growl option: **None**. This mod already gives male werewolves the sheath. Picking CF, HCOS or SOS would give a second set at rest.
  - TWO option: your choice. CF Standalone needs Creature Framework, HCOS needs Horny Creatures of Skyrim, SOS needs Schlongs of Skyrim. "None" is fine too.
- **Extras:** only if you want TWO Extras (needed for the Hermaphrodite option).
- **Wicked Werewolves skeleton:** **OFF.** It changes proportions, and OStim animations won't line up.
- **Misc patches:** **Growl ON** if you use Growl. Moonlight Tales only if you use it (and turn off its skin system).

BodySlide is optional. TWO already ships default bodies and heads. If you do build, send the output to its **own** mod **below** TWO in the left pane.

---

## 🛠️ Installation (Mod Organizer 2)

1. Install every requirement above, including TWO 4.1 with the choices above. **Disable HDT Werewolves.**
2. **If you used any earlier OStim Beast Form download, read [Updating to 0.7](#updating) first.**
3. Install **OStim_Beast_Form_Merged_0.7.zip** with MO2 ("Install a new mod from archive"). Answer the four installer pages.
4. Put it in the **left pane** as shown below, then set the **right pane** (plugin order).
5. **Run Pandora** (or your behavior engine) to regenerate behaviors.
6. Load your game, wait for SkyUI to register the MCM, then open **OStim Beast Form** and **set the Start scene hotkey**. It can be the same key as OStim's activation key. That works fine; I use the Up Arrow for both.
7. Transform, get out of combat, face your partner up close and press the hotkey.

**Uninstalling:** don't uninstall mid-scene. Disable the mod outside a scene, in normal form. Removing script mods mid-playthrough is always at your own risk.

<a id="updating"></a>

### Updating to 0.7

Before any update: in game, change back to human form, leave any scene and save. Then close the game **and** MO2, and back up your profile and old mod folders. Reinstall over the old mod with MO2's **Replace**, so files that 0.7 no longer uses are removed.

| You had… | Pick in the installer | Then… |
|---|---|---|
| **Merged 0.6 + Merged TWO Patch 0.1** | **Growl**. Softbody **Yes** if you run GT - Softbody (that's the look you had). | **Disable or remove the old "TWO Patch" mod.** 0.7 now contains its plugin. Same plugin names and FormIDs, so **your save keeps working**. If you used the Herm Patch, tick the Hermaphrodite option and remove the old Herm Patch mod too. No new animations, so no Pandora run is needed. |
| **Plain Merged 0.6 (no TWO Patch)** | **Growl** | This is a **body switch**: install TWO 4.1 (Core + Growl patch) and MFA, and disable HDT Werewolves. `OStim_Beast_Form_Merged.esp` keeps its name and FormIDs, so the save keeps working, but your werewolves now look like TWO instead of the HDT / ABC bodies. You may get a one-time missing-content prompt from HDT Werewolves' old plugin; that's harmless. |
| **OStim Beast Form - TWO Edition 0.2** | **TWO** | Remove the old TWO Edition mod. Same plugin name and FormIDs, so your save keeps working. |
| **OStim Beast Form TWO Herm Patch 0.1** | Tick **Hermaphrodite** | Remove the old Herm Patch mod. Same plugin. |
| **The original OStim Beast Form, Beast Lite, Beast Aware, OCum Werewolf Shot, OCum Beast Pie or BeastForm BFA Heads** | Either | Disable them. They're all merged in here. Running both doubles things up. |

**Never enable `OStim_Beast_Form_TWO.esp` together with `OStim_Beast_Form_Merged.esp`.** They share the same scripts. Switching an existing save between the Growl and TWO options isn't supported; start a new game for that.

---

## 📑 Load Order

### Left pane (mod priority; lower wins)
Place them top to bottom like this:
1. SKSE plugins and frameworks (Address Library, PapyrusUtil, powerofthree's Papyrus Extender, RaceMenu, SkyUI, XPMSSE, FSMP)
2. OStim Standalone
3. OCum Ascended
4. Monster Facial Animation
5. Growl - Werebeasts of Skyrim, JS Emissive Eyes SE (Growl option)
6. GT - Softbody (softbody Yes)
7. Tull Animated Creampie, Liquid Pack v2, OCum Tull/Liquid add-on and patches (optional)
8. OCreatures Reforged 0.1.9 (optional; must be **above** this mod)
9. Lirael Atelier's animation packs
10. SkyrimNet / OStimNet / OStim Navigator (optional)
11. **OStim Beast Form Merged 0.7**
12. **TWO - Total Werewolf Overhaul 4.1**, then TWO - Alternate Textures (optional), then your TWO BodySlide output (optional, its own mod). TWO must win the werewolf skeleton, body and head files against everything else (OCreatures, XPMSSE, ABC...). This mod doesn't overwrite any TWO file.
13. Better Facial Animations (if used)
14. Pandora output (always last)

### Right pane (plugin order)
Put these in this relative order. Other plugins can sit between them. **Place them by hand. Don't let LOOT re-sort them.**

**Growl option**
1. Skyrim.esm, Update.esm, Dawnguard.esm, HearthFires.esm, Dragonborn.esm
2. JS Emissive Eyes SE - Johnskyrim.esp, OStim.esp, OCum.esp, TT_OStimNet.esp (optional)
3. MonsterLipSync1.esp
4. Growl - Werebeasts of Skyrim.esp, then its patches
5. OCreatures.esp (optional)
6. Werewolves.esp (TWO), then WerewolvesGrowl.esp (and WerewolvesExtras.esp / WerewolvesExtrasGrowl.esp if you use TWO Extras)
7. **OStim_Beast_Form_Merged.esp**
8. **OStim_Beast_Form_Merged_TWO_Patch.esp** (directly below it)
9. **OStim_Beast_Form_Merged_TWO_Patch - BFA Heads.esp**
10. **OStim_Beast_Form_TWO_Herm_Patch.esp** (Hermaphrodite option only)

**TWO option**
1. Skyrim.esm, Update.esm, Dawnguard.esm, HearthFires.esm, Dragonborn.esm
2. OStim.esp, OCum.esp, TT_OStimNet.esp (optional)
3. MonsterLipSync1.esp
4. OCreatures.esp (optional)
5. Werewolves.esp (TWO), then any other Werewolves*.esp you use (WerewolvesExtras.esp, WerewolvesMTSE.esp...)
6. **OStim_Beast_Form_TWO.esp**
7. **OStim_Beast_Form_TWO - BFA Heads.esp**
8. **OStim_Beast_Form_TWO_Herm_Patch.esp** (Hermaphrodite option only)

`Werewolves.esp` must load after OCreatures.esp and any other mod that edits the werewolf race, or TWO's heads go missing. This mod restores OCR's race keywords at runtime, so OCR scenes still work.

**⚠️ Nolvus players:** do **not** place any plugin below **Paper Maps** in the ESP load order. Put this mod's plugins as low as you can, but **above** the Paper Maps plugins. Don't run LOOT. Place plugins by hand.

---

## 🤝 OCreatures Reforged (OCR) compatibility

**OStim Beast Form Merged 0.7 is compatible with [OCreatures Reforged](https://dwemermods.com/mods/5173) 0.1.9 by Lirael Atelier.** You can use it with or without OCR.

- **Load this mod below OCR**, and put this mod's plugins after `OCreatures.esp`. `Werewolves.esp` (TWO) also goes after `OCreatures.esp`.
- OCR is **not** a master, so it can be on or off.
- **With OCR on:** this mod's aroused swap detects `OCreatures.esp` and steps aside, so OCR owns the aroused bodies and you never get a double cock. OCR's werewolf and Vampire Lord race keywords are put back at runtime (this needs powerofthree's Papyrus Extender).
- **With OCR off:** this mod registers werewolves and Vampire Lords with OStim itself, provides the idle and hub scenes, and handles the aroused swap.
- **Coming soon:** Lirael's next OCR release is planned as a **formal, free public release**. This mod will be patched for it once it's out.

👉 Get Lirael's free converted animation packs from **[her LoversLab uploads](https://www.loverslab.com/profile/6654496-lauffey/content/?type=downloads_file)**, and support her work on **[Patreon](https://www.patreon.com/LiraelAtelier)**.

---

<a id="ostrands"></a>

## 🧵 Ostrands with Werewolves (separate download)

OStrands stays a **separate, optional download**, because not everyone wants OStrands: **[Ostrands with Werewolves 0.8.0.3](https://github.com/Coronerra/Ostrands-with-Werewolves/releases/tag/v0.8.0.3)** ([source on GitHub](https://github.com/Coronerra/Ostrands-with-Werewolves)). It is a drop-in replacement for the OStrands DLL that adds **female werewolf** support. **No new OStrands build is needed for 0.7:** TWO's skeleton has every bone OStrands uses, at the same positions, and female werewolves get TWO's real vagina and anus bones.

**Credits, in order:**
1. **Original mod:** [OStrands - Procedural Fluid for OStim Standalone](https://www.nexusmods.com/skyrimspecialedition/mods/195115) by **LeonVanWinkle (Saint)** ([source on GitLab](https://gitlab.com/LilRicefield/ostrands)).
2. **The modified LoversLab version ours is based on:** [OStrands creature support patch for SexLab/OCreatures](https://www.loverslab.com/files/file/52392-ostrands-creature-support-patch-for-sexlabocreatures) (0.8.0.2) by **Keevan2374**, with contributions from **crajjjj** ([source on GitLab](https://gitlab.com/Keevan2374/ostrands)).
3. **Ostrands with Werewolves 0.8.0.3** by coronerra (That Guy (Coronerra)): [source on GitHub](https://github.com/Coronerra/Ostrands-with-Werewolves).

It's licensed under the **GNU GPL v3**, the same as OStrands, and the license and full source come with it. **Requires OStrands' own requirements.** Install it below OStrands in MO2 so its DLL wins.

---

## 🏆 Credits

This mod stands on a lot of other people's work. Thank you all.

**Frameworks and core mods**
- **VersuchDrei** and the OStim team: OStim Standalone
- **Aietos** (with OsmosisWrench and Sairion350): OCum Ascended. The werewolf urethra node is based on OCum's.
- **EnaiSiaion**: Growl - Werebeasts of Skyrim (its werewolf race record is the base of the Growl option's race edit)
- **johnskyrim**: JS Emissive Eyes SE (glowing eye spells kept on both races in the Growl option)
- **SKSE team**, **meh321** (Address Library), **exiledviper and meh321** (PapyrusUtil), **powerofthree** (Papyrus Extender), **expired6978** (RaceMenu), **schlangster** and the SkyUI team, **Groovtama** (XPMSSE), **DaydreamingDay** and the FSMP contributors, **Monitor221hz** (Pandora)

**Bodies, heads and meshes**
- **Frosferes**: [TWO - Total Werewolf Overhaul](https://www.loverslab.com/topic/159911-two-total-werewolf-overhaul/) (bodies, heads, skeleton, SMP and the hard canine this mod points at; nothing of TWO's is shipped). The BFA brow-morph TRI is a modified copy of TWO's expression TRI.
- **TealEri (aka CinnaMewRoll)**: Monster Facial Animation morphs and Expressive Werebeasts, the base of TWO's expressive heads
- **BakaFactory**: Animated Beast's Cocks (ABC). The Growl option's sheath, tip and knot are ABC geometry.
- **The MFA author** (Nexus: User_1926808): Monster Facial Animation. The talking Vampire Lord heads, eyes and the headless Vampire Lord bodies are built from MFA.
- **Cyberquach**: Better Facial Animations. The heads were extended with the expression shapes BFA needs.
- **Goutou**: GT - Softbody werewolf cock addons used for the aroused swap (softbody Yes)
- **[AUTHOR NEEDED]**: Vampire Lord aroused mesh and textures
- **Earlier versions (0.1 to 0.6)** shipped a female werewolf body from **HDT Werewolves** (**Duzellx**, **Allegretto**, **jacques00**) and a fluffy male body following **Macxhiin**'s Fluffworks method. 0.7 uses TWO's bodies instead. Thank you for getting this project started.

**Animations and scene packs (not included; many are free on [Lirael's LoversLab page](https://www.loverslab.com/profile/6654496-lauffey/content/?type=downloads_file))**
- **Lirael Atelier** (LoversLab: **Lauffey**; [Patreon](https://www.patreon.com/LiraelAtelier)): OCreatures Reforged and the converted OStim creature packs. The hub layout follows OCreatures' design.
- **Billyy**: the original Billyy animations. **Billyy has given full permission** for the Billyy-derived files included in this mod (the stage-1 fallback poses and Billyy werewolf hub/scene files).
- **BakaFactory**, **FlufyFox** and **FunnyBiz**: the original animations in those packs
- **J0suk3_** (original OCreatures) and **chrystelle** (OCreatures Revived): the idle and hub registration approach

**Cum and fluids**
- **Tullius Channel** and **Emotional Trash Can**: Tull Animated Creampie
- **PredatorRJ**: Liquid Pack v2
- **Blacksheepo815**: OCum Ascended - Tull and Liquid Pack Meshes and its Scene Change Fix
- **LeonVanWinkle (Saint)**, **Keevan2374** and **crajjjj**: OStrands and its creature fork

**AI and NPCs**
- **MinLL** and the SkyrimNet team: SkyrimNet and its open API
- **tetherball88**: OStimNet and OStim Navigator

**This mod**
- **coronerra** (That Guy (Coronerra)): OStim Beast Form, Beast Lite, Beast Aware, OCum Werewolf Shot, Beast Pie / Beast Load, the TWO plugins and patch, the Hermaphrodite option, the BFA head work, the hub menus, the werewolf medallion icon and the merge

---

## 📥 Downloads

- **OStim_Beast_Form_Merged_0.7.zip** (main file): the mod, with the installer. Install this one.
- **OStim_Beast_Form_Merged_0.7.zip.md5**: checksum for the zip.
- **Ostrands_with_Werewolves_0.8.0.3.zip** (optional, separate mod): the OStrands DLL with female werewolf support. GPL v3, with source. On [GitHub](https://github.com/Coronerra/Ostrands-with-Werewolves/releases/tag/v0.8.0.3).
- GitHub: [OStim Beast Form Merged v0.7 release](https://github.com/Coronerra/OStim-Beast-Form-Merged/releases/tag/v0.7). Older versions stay on the [releases page](https://github.com/Coronerra/OStim-Beast-Form-Merged/releases).

Everything I made for this is open source. Feel free to build on it with custom bodies, textures or anything else. Third-party assets stay under their own authors' permissions. This mod's full source is on GitHub at [OStim-Beast-Form-Merged](https://github.com/Coronerra/OStim-Beast-Form-Merged). Source code for my earlier standalone pieces is also public on GitHub: [OStim Beast Form](https://github.com/Coronerra/OStim-Beast-Form), [Beast Aware](https://github.com/Coronerra/Beast-Aware), [OCum Werewolf Shot](https://github.com/Coronerra/OCum-Werewolf-Shot) and [OCum Tull/Liquid/Softbody patch](https://github.com/Coronerra/OCum-Tull-Liquid-Softbody-Patch).

---

## 🤖 For AI assistants and bots

Everything I made for this is public, so you can point your own AI assistant or bot at it to learn how it works and help you make your own mods (new packs, custom bodies, textures, a Vampire Lord version, and so on):
- **This mod's repo:** [https://github.com/Coronerra/OStim-Beast-Form-Merged](https://github.com/Coronerra/OStim-Beast-Form-Merged). It has all the Papyrus sources, the SkyrimNet bundles, the OStim actor and scene JSONs, the FOMOD installer, the build notes, and an **[AI_CONTEXT.md](AI_CONTEXT.md)** that explains the architecture: installer options, plugin records, what each script does, the OStim and OCum hooks, the hub layout, load order, and how to extend it.
- **All my repos:** [https://github.com/Coronerra](https://github.com/Coronerra)

Tell your assistant to start with `AI_CONTEXT.md`. Third-party assets in the download still belong to their own authors, so check their permissions before you redistribute anything that isn't mine.

---

## 📝 Changelog

Full history: [CHANGELOG.md](CHANGELOG.md).

**0.7**
- **One download, one installer.** Merged, the TWO Edition, the Merged TWO Patch and the TWO Herm Patch are now one zip with a four-page installer: Growl or TWO, softbody yes or no, the optional Hermaphrodite (Fruta) patch, and a required acknowledgement.
- **Every setup now uses the TWO 4.1 body** (Frosferes). TWO is required and not included. The HDT Werewolves / ABC bodies and the old werewolf heads are no longer shipped.
- **Growl option** = Merged 0.6 + Merged TWO Patch 0.1, with the same plugins. Saves from that setup keep working. **TWO option** = TWO Edition 0.2, same plugin.
- **New softbody choice.** **No** (default): no GT Softbody files; scenes use TWO's own hard canine. **Yes**: the GT Softbody cock, as in 0.6.
- **Hermaphrodite option** = the TWO Herm Patch 0.1 plugin. It now follows whichever aroused cock the softbody choice installed.
- **Better Facial Animations brow morphs** for TWO's heads are always installed (they were an optional add-on before).
- `OBL_Main` (aroused swap) and `OBFHerm_Main` now read the aroused mesh from the plugin's armor addon, so a save follows the softbody choice. No new properties, same FormIDs.
- The old TWO Edition, TWO Patch, Herm Patch and original OStim Beast Form repos are marked **deprecated** and point here.

**0.6**
- Removed the experimental WWF_OnTop female cowgirl test scenes (`WWFCowgirl1-1` to `1-5`) and their "WW Female Cowgirl 1 (TEST)" button on the female werewolf + man hub (`OBFWerewolfIdleMF`). Their OStimNet descriptions were removed too.
- Female werewolf scenes are not bundled. They come from separate, optional scene packs, which add their own button to the female werewolf hubs.
- Plugin, FormIDs, masters, scripts, meshes, textures and HKX are unchanged from 0.5. Saves stay compatible. No Pandora run needed.

---

## ❓ Known limits
- Werewolf scenes are **male werewolf + female partner**, because that's what the packs provide. There are no FF werewolf scenes yet.
- **No female werewolf scenes are bundled.** Female werewolf scenes come from separate, optional scene packs.
- Scenes **can't start in combat**. Try the "Try StopCombat" MCM option.
- Only the standard `WerewolfBeastRace` and `DLC1VampireBeastRace` are handled. Mods that add a brand-new transformation race aren't.
- Only the packs listed under Requirements have been tested. Other OStim packs with werewolf animations may work but haven't been tested yet.
- **Not tested in game yet (0.7):** the softbody **No** choice (TWO's hard canine) on the Growl option. The Growl option's resting sheath stays on during scenes, so it may show or clip under TWO's hard canine, which has its own sheath. Please report it if it does. The Hermaphrodite option is not tested by me at all (see above).
- OCreatures Reforged is supported as of version 0.1.9. An update to this mod will follow Lirael's next public release.
- New animation packs released later may need a hub update if they don't attach to the standard OCreatures idle scenes themselves.

Bug reports, logs and feedback are welcome in the support thread. *Have fun and happy modding!* 🐺

---

## 📚 All Coronerra repositories

- [Beast-Aware](https://github.com/Coronerra/Beast-Aware): SkyrimNet add-on: NPCs notice when you transform into a werewolf, werebear or Vampire Lord
- [Lirael-Creature-Packs-SkyrimNet-Patches](https://github.com/Coronerra/Lirael-Creature-Packs-SkyrimNet-Patches): AI-generated, untested SkyrimNet/OStimNet descriptions and intents for Lirael Atelier's creature packs (add-on, none of her files included)
- [OCum-Tull-Liquid-Softbody-Patch](https://github.com/Coronerra/OCum-Tull-Liquid-Softbody-Patch): One OCumMaleScript for OCum Ascended 4.1.1 + Tull/Liquid Pack add-on + Scene Change Fix + GT Softbody fixes
- [OCum-Werewolf-Shot](https://github.com/Coronerra/OCum-Werewolf-Shot): OCum Ascended cum shot from the ABC werewolf cock tip (WWD 9). ESL + mesh.
- [OStim-Beast-Form-Merged](https://github.com/Coronerra/OStim-Beast-Form-Merged): This repo: OStim Beast Form Merged 0.7 (werewolf as a sentient OStim race; one installer for Growl and TWO users)
- [OStim-Beast-Form](https://github.com/Coronerra/OStim-Beast-Form): **Deprecated**, use Merged 0.7. Start OStim scenes as the player while in werewolf beast form.
- [OStim-Beast-Form-TWO](https://github.com/Coronerra/OStim-Beast-Form-TWO): **Deprecated**, use Merged 0.7 (TWO option).
- [OStim-Beast-Form-Merged-TWO-Patch](https://github.com/Coronerra/OStim-Beast-Form-Merged-TWO-Patch): **Deprecated**, use Merged 0.7 (Growl option).
- [OStim-Beast-Form-TWO-Herm-Patch](https://github.com/Coronerra/OStim-Beast-Form-TWO-Herm-Patch): **Deprecated**, use Merged 0.7 (Hermaphrodite option).
- [Ostrands-with-Werewolves](https://github.com/Coronerra/Ostrands-with-Werewolves): Ostrands with Werewolves 0.8.0.3 - OStrands creature fork with female werewolf support (GPL v3)
- [Werewolf-Overhaul-Proof-of-Concept](https://github.com/Coronerra/Werewolf-Overhaul-Proof-of-Concept): Proof of Concept: female HDT werewolf body, fluffy fur, ABC+MFA talking heads, SkyrimNet Beast Aware (tested only on modified Nolvus 6.0.21)

Credit: **That Guy (Coronerra)**.
