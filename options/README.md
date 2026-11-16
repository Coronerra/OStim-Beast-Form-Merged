# Installer option sources

Text sources for the installer folders that differ from `Data/` (which holds `00 Common` + `10 Growl`):
- `20 TWO/`: the TWO option's `OBF_MCM.psc`, OStim actor properties (`"mod": "OStim_Beast_Form_TWO.esp"`), SkyrimNet manifests and OStimNet bridge prompt.
- `40 Herm/`: the Hermaphrodite (Fruta) option's Papyrus sources and actor property.
- `30 Softbody/`: the softbody Yes merged `OCumMaleScript.psc` (the TWO-derived meshes and SMP configs are only in the release zip).
- `50 WVL Werewolf/`, `51 WVL Female Werewolf/`, `52 WVL Vampire Lord/`, `53 WVL Beast Couples/` (0.8+): optional integration with Lirael Atelier's [Werewolf and Vampire Lord OStim 0.2.3](https://www.patreon.com/LiraelAtelier/posts/werewolf-and-for-175434973): her hub overrides (same paths as hers, so this mod must load below her pack), extra-cast scenes (`OBFWVL*`), couple starts and OStimNet descriptions. Scene JSON only; the animations stay in her pack.

Plugins, compiled scripts, meshes and textures are only in the release zip. See [AI_CONTEXT.md](../AI_CONTEXT.md).
