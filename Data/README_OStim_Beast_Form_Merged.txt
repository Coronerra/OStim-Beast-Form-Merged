OStim Beast Form Merged 0.6 - public release (Skyrim SE/AE, tested on SE 1.5.97)
By That Guy (Coronerra). Everything made by coronerra is open source (MIT);
third-party assets belong to their original authors (see credits on the mod page).

0.6 CHANGELOG
1. Removed the experimental WWF_OnTop female cowgirl test scenes
   (SKSE/Plugins/OStim/scenes/WWF_OnTop/WWFCowgirl1-1..5.json) and their
   "WW Female Cowgirl 1 (TEST)" button on the female werewolf + man hub
   (OBFWerewolfIdleMF). Their five OStimNet descriptions are gone too.
2. Female werewolf scenes are not bundled with this mod. They come from a
   separate, optional female-werewolf scene pack (for example an OStim
   conversion of Dayelyte's female werewolf animations). Such a pack adds its
   own button to the female werewolf hubs. Without one, the female werewolf +
   man hub is an idle with no buttons, which is expected.
3. Docs: the old WWF_OnTop warnings, hub graphs 0.3/0.4 and mentions were
   removed or marked as removed. Docs/.../STATIC_CHECKS_0.6.txt and
   hub_graph_0.6.json describe the current scene graph.
Plugin, scripts, meshes, textures and HKX are byte-identical to 0.5: same
ESL plugin, same FormIDs, same 8 masters (Growl is still a hard master).
Saves stay compatible. No new animations: NO Pandora run needed.

0.6 INSTALL
1. Close Mod Organizer AND Skyrim.
2. Back up the mod folder, then DELETE the old folder
   SKSE/Plugins/OStim/scenes/WWF_OnTop inside it (or install 0.6 as a clean
   replacement of the mod). Extracting over the old folder alone would leave
   the five old test-scene files behind.
3. Extract 0.6 over the mod folder, overwrite all. Plugin order unchanged.
   Don't run LOOT.

0.5 CHANGELOG
1. Male werewolf body restored WITH its original limp penis, sheath and knot.
   coronerra/bfa/malebodywerewolf_0/_1.nif are rebuilt from the v1.3 fluffy
   body; only the head, eyes and teeth are removed (BFA heads supply those).
   The groin cap from 0.1-0.4 is gone. The "second balls" were the knot.
   The Lite aroused swap is unchanged: the GT aroused cock sits over the base
   genitals, so you only see one set. The sheath/tip textures it needs
   (morenastycritters/werewolf/werewolfballs*, werewolfpenis_red/_n/_sk, from
   BakaFactory Animated Beasts Cocks) now ship, because that mod is off here.
2. Beast Load (OCum). When a MALE werewolf, werebear or Vampire Lord climaxes
   in any OStim scene (yours or NPC-only), his partners get heavy cum:
   - Vaginal / anal: creampie overlays + Tull/Liquid creampie meshes.
   - Footjob, handjob, masturbation, "aircum"/outside finishes: belly, chest,
     butt, legs (+ feet / hands) coverage. Mislabeled creature scenes (e.g.
     the Billyy footjob that lists only vaginalsex) are read from their tags.
   - Blowjob / oral: NOT swallowed. Heavy face, mouth, neck and chest, with
     Liquid Pack face drips.
   - Huge load (default on): heaviest OCum textures on every area, full
     mesh set, and the beast never runs dry.
   - Works no matter what OCum's MCM says about meshes off, vaginal/anal
     overlays off or creampie chance. OCum's cum-shot spurts also play on
     outside finishes in your own scenes.
   - Stays on after the scene for OCum's cleanup timer (default 5 real
     minutes, counted from her first cum and renewed while a scene is still
     running) and is washed off in water like normal OCum cum. Raise OCum's
     "cum cleanup timer" if you want it to last longer.
   - After the scene, meshes are only put back while she is naked, so her
     own armor is never fought over.
3. Multi-round stacking (default on, max 5 rounds). If OStim keeps the scene
   going after he cums, every climax adds more: one more layer per area and
   two more Tull/Liquid meshes, until every free slot is used. All of it
   clears together with OCum's timer or a bath.
   Mesh slots used (never two items on one slot): 59 Tull creampie OR Tull
   oral, 60 Tull drip, 47 Liquid bottom, 43 Liquid bottom SMP, 55 Liquid
   face, 57 Liquid face SMP, 36 Liquid torso. Extra rounds add them in this
   order: 60, 47, 55, 57, 36, 43, then 59. Body (32), hands, feet, pelvis
   underwear slots (49/52) and cloak/shoulder armor slots are never used.
   Slot 36 is the ring slot: a ring she wears is taken off while the torso
   drip is on.
4. MCM: OStim Beast Form > Settings > "Beast climax (OCum)": on/off, Huge
   load, Tull/Liquid meshes, Spurts on outside finishes, Stack cum across
   rounds, Max stacked rounds (1-10).
5. Not merged: the OCum TL SceneFix pex. It isn't a no-op for people without
   Tull/Liquid, and it would replace OCum's own script. Beast Load gets the
   beast result without replacing any OCum script. Keep "OCum TL SceneFix +
   GT Softbody Merge" as its own mod.
Plugin: OStim_Beast_Form_Merged.esp is byte-identical to 0.4 (same records,
masters, ESL flag; no OCreatures master). No new HKX: NO Pandora run.

0.5 INSTALL
1. Close Mod Organizer AND Skyrim.
2. Back up the mod folder "OStim_Beast_Form_Merged" (copy it next to itself as
   "OStim_Beast_Form_Merged_bak_0.4").
3. Extract the zip over "OStim_Beast_Form_Merged", overwrite all.
4. Don't move the plugin or the mod, don't run LOOT. Plugin order unchanged.
5. In game: open the MCM once to see the new "Beast climax (OCum)" options.
   Existing saves pick up the new defaults on load.

0.5 TEST (not performed in-game)
- Werewolf body out of a scene: limp penis, sheath and knot visible, no hole,
  no purple texture. Aroused in a scene: only one set visible (GT over base).
- Werewolf + woman, any vaginal scene to climax: creampie overlays + Tull/
  Liquid meshes, still on after the scene, gone about 5 minutes later or
  when she swims.
- Billyy footjob to climax: belly/chest/legs/feet cum + spurts, no creampie.
- Blowjob scene: face/mouth/neck/chest covered, Liquid face drip.
- OStim set to keep the scene going after orgasm: climax 3 times. Each
  climax should add coverage and more meshes. Stops growing at max rounds.
- An NPC-only werewolf scene (if you have one): partner gets the same.
- Vampire Lord: same as werewolf.
- Human scenes: unchanged.
- Papyrus log (if on): "[OBF BeastLoad] ... climax, thread N, scene ..." on
  every beast climax.

0.4 HUB FIX (how OStim's hub actually works)
OStim NG has no "hub" feature or tag in code: a hub is just an idle/intro
scene whose navigations are menu buttons (icon + name). OCR's design: the
OCr*Idle scene is the main hub; each animation pack attaches ONE button to
it (its pack page, via "origin"), and the pack page lists that pack's
animations (first stage only); stages chain Next/Back; Return goes to the
pack page, the medallion to the main hub.
0.3 instead put every stage of every animation (183 for WW FM, mostly
icon-less, stages 2-6 too) straight into the main hub. 0.4 restores the
OCR model:
- WW FM main hub: 3 buttons = Baka, Billyy, FlufyFox werewolf pages
  (3 / 26 / 6 animations). FMM, FFM, FMMM, FMMMM: Billyy page each.
  VL main hub: Baka, Billyy, FunnyBiz vampire lord pages (2 / 2 / 2).
  Female werewolf + man hub: one test-scene button (removed in 0.6).
- Every pack page button has an icon; Baka/Fluffy got the medallion
  (VL: OStim's vampire-bite icon), Billyy/FunnyBiz keep their own.
- Pack pages are no longer random start scenes, so every beast scene
  starts on the matching populated main hub. All 267 scenes still
  reachable; only werewolf (or VL) + human actors on each page.
- FF stays an untagged, never-random idle: there are no FF scenes.

0.4 SKYRIMNET / OSTIMNET (metadata + prompt only)
No plugin, script or HKX changes: NO Pandora run, no new masters.
- zz OStim Beast Form Merged SkyrimNet.json: OStimNet descriptions for Beast
  Form's own scenes only (female-werewolf hub, OBF/OBL forwarding pages;
  the test-scene descriptions were removed in 0.6). OCR idle and Billyy/Baka/Fluffy/FunnyBiz scenes keep the
  descriptions from the Lirael/OCR patches; nothing there is duplicated.
- New SkyrimNet bundle coronerra.beastform_ostimnet: while you are a werewolf
  or Vampire Lord, a nearby free NPC is told you can still be picked for
  OStimNet StartNewSex (OStimNet's partner list skips beast races). They still
  decide by personality. Leave OStimNet "Nearby actors humanoid only" ON.
- ttlb_* / 'faction' decorator errors: from TT BodyLanguage / SkyrimNet core,
  not fixable from this mod. See BodyLanguage_decorator_errors_0.4.txt.
- Details: OStimNet_SkyrimNet_Integration_0.4.txt.

0.3 HUB FIX
OCrWerewolfIdleFM/FFM/FMM/FMMM/FMMMM and OCrVampireLordIdleFM are the real
hub+intro+idle scenes again. They use the existing unique OBF_B_* animation
 events and OBFMerged HKX, NOT OCR's event project. Exact OCR JSON paths are
overridden, so OCR's enabled loose files cannot create duplicate idle IDs.
Every installed compatible scene was scanned and added to the matching hub.
WW pages contain only Werewolf + human actors; VL only VampireLord + humans.
Pack pages remain linked, but no longer carry the global hub tag. All sex
scenes have a medallion return to their matching main hub. Old Beast Lite
and OBF pages are non-random forwarding aliases, not empty selectable hubs.
A separate OBFWerewolfIdleMF hub (female WW + male human) was added, using
an existing idle animation event. (Its 0.3-0.5 test scenes were removed in 0.6.)
OCrWerewolfIdleFF is preserved as an intro/idle but NOT hub-tagged: there are
zero installed compatible FF sex scenes. This avoids another empty hub.
Hub direct scene counts: WW FM 183, FFM 6, FMM 33, FMMM 6, FMMMM 6;
VL FM 28. (0.3 also counted 5 female WW test scenes, removed in 0.6.)
Packs: Billyy COMPLETE, Baka, FlufyFox, FunnyBiz.
Future packs added later require regenerating the static direct-link list if
they do not provide origins to the standard OCr*Idle IDs themselves.

0.3 MALE AROUSED SWAP
Lite's original OBL_Main + player alias quest/scripts are restored. Only male
werewolves equip Addon_Dog_Black_Hard.nif, and only male vampire lords swap
to vampirelord_Hard.nif. Both loose meshes and required addon textures ship.
Females are never changed. OBL_SwapEnabled defaults to 1; set it to 0 to stop.
When OCreatures.esp is loaded the Lite swap steps aside; OCR owns that job.
OCreatures.esp can stay OFF: no OCR master has been added. Missing loose mesh
is safely skipped by MiscUtil.FileExists (PapyrusUtil required).
The 23 previous records are unchanged; eight new records occupy 0x831-0x838.

ICON
coronerra's werewolf medallion is interface/OStim/icons/OBeastLite/hub/hub.dds:
128x128 DXT5, eight mip levels. Main-hub return navigations use it.
Billyy's own OCreatures/werewolf/werewolf icon paths are unchanged.
No separate icon pack was folded in.


GROWL / OTHER WEREWOLF OVERHAULS
Growl - Werebeasts of Skyrim.esp is a hard master of this plugin (0.5 and 0.6).
Without Growl, the plugin will not load. That is because the werewolf
race override was built on Growl's WerewolfBeastRace record (it still
carries a Growl keyword and Growl attack-data form IDs). The scripts
do not call Growl scripts: they only check for the standard
WerewolfBeastRace (Skyrim.esm 0x000CDD84) and pause the vanilla timer
PlayerWerewolfShiftBackTime (Skyrim.esm 0x0002BA19) during OStim scenes.

There is no official patch yet for vanilla werewolves, Twilight
Werewolf Overhaul, or another overhaul. If that overhaul still uses
WerewolfBeastRace, you can retarget a copy of this ESP in SSEEdit:
keep this mod's talking heads, FaceGen flag, and body addon changes;
replace the Growl form IDs with the target race's equivalents; then
Clean Masters to drop Growl. If the overhaul uses a different timer,
point ShiftBackTime in OBF_Main at that global. Skip HDT Werewolves'
MFA and Growl Patch if you are not using Growl. A brand-new
transformation race is not handled. See the GitHub README section
"Growl dependence" for the full steps:
https://github.com/Coronerra/OStim-Beast-Form-Merged#growl-dependence

REQUIREMENTS / ORDER
Same eight masters: Skyrim, Update, Dawnguard, Dragonborn,
JS Emissive Eyes SE - Johnskyrim.esp, Growl - Werebeasts of Skyrim.esp,
OStim.esp, OCum.esp. Also existing SKSE/SkyUI/PapyrusUtil/RaceMenu,
SkyrimNet, ABC skeleton + WWD bones, HDT/GT Softbody dependencies.
OBF_OCRCompat remains unchanged (optional PO3 keyword restore when OCR loads).
Keep existing female texture providers. Existing other Nolvus plugins may
still need MFA; this merged ESL itself does not master MFA or OCreatures.
Vampire lord hotkey support remains as in 0.2; no new claim it is finished.
OCum TL SceneFix + GT Softbody Merge remains separate.

INSTALL
Close ModOrganizer AND SkyrimSE before replacing files. Back up existing mod,
then extract over OStim Beast Form Merged. Same plugin filename; do not move
plugin order: OStim_Beast_Form_Merged.esp stays LAST after Werewolves.esp
and OCreatures.esp if present. Keep merged originals disabled. Do not run LOOT.
Do not enable/disable OCR just for this update: either setup is supported.
No new events/HKX were added in 0.3 or 0.4: NO Pandora regeneration for this update.
The existing 0.2 OBFMerged behavior generation must already be present.

TEST (not performed in-game)
Use a backed-up test save. Open matching beast scene, hit Hub: expect installed
matching packs/scenes, never horse/dog/wolf/werebear scenes; return medallion
should reach the populated main hub. Male WW/VL aroused mesh should appear
at scene start with OCR plugin off, restore at scene end and after save load.
With OCR on, only OCR should own the aroused swap (no double addon).
MCM works as in 0.2; preserve/recheck your hotkey.

0.4 TEST (not performed in-game)
- Male werewolf, OStimNet on: talk to a willing companion; she may propose sex
  and name you. Confirm a werewolf scene starts (not a human-only scene).
  Same as Vampire Lord. A refusal is also a pass.
- Hub: male werewolf + woman. Start: main hub shows Baka / Billyy /
  FlufyFox buttons (with icons). Each opens a page of that pack's werewolf
  animations; Return goes back to the page, medallion to the main hub.
  Vampire Lord: Baka / Billyy / FunnyBiz. 3-5 actors: Billyy button.
- During a Beast Form hub scene, NPC comments should describe the scene
  (OStimNavigator.log: "Loaded 15 animation descriptions from ...zz OStim
  Beast Form Merged SkyrimNet.json" as of 0.6).
- SkyrimNet bundle list should show "Beast Form OStimNet Bridge".
- ttlb_* errors will still appear; expected (see BodyLanguage notes).

