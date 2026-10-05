<p align="center"><img src="github_social.png" alt="Echelon - mod manager for Helldivers 2" width="720"></p>

# Echelon

A mod manager for Helldivers 2. Keep a library of mods, arrange them into profiles, and deploy a whole profile to the game in one click.

**Status: beta.** Back up anything you care about, and please report problems (see below).

## Download

Get **Echelon-Setup-x.y.z.exe** from the [latest release](../../releases/latest) and run it. It installs for your user only, with no admin prompt.

The installer is code-signed. Windows may still say "Windows protected your PC" for a while, because the signature is new. Click **More info → Run anyway**.

Echelon is also on:

- [Nexus Mods](https://www.nexusmods.com/helldivers2/mods/16613). That build works fully offline and has no update check, as Nexus asks of tools it hosts. New versions are posted on the page.
- [AyakaMods](https://ayakamods.com/mods/echelon-mod-manager.4486/).

## What it does

- **Library and profiles:** add mods from .zip, .rar, .7z or folders; build profiles with load order, separators, tags and per-mod options.
- **One-click deploy:** puts exactly the active profile into the game (and can purge the game back to unmodded).
- **Bingus Shared Loader support:** recognises the loader and the mods that need it, warns when a profile is missing it, and keeps it in the right load-order spot automatically so Bingus mods actually start.
- **Import from HD2 Arsenal:** bring your mods, profiles and option choices over.
- **Share profiles:** as short codes (`EC-XXXX-XXXX`) or links.
- **Solo-only mods:** mark Lua mods that change the game for everyone in the lobby. They get a SOLO badge, and Echelon reminds you to turn them off before public lobbies when you deploy them.
- **Developer Suite for mod authors:** Mod Builder, Repatcher, Mod Inspector and Crash Finder, plus a shortcut to [HD2 Retagger](https://www.nexusmods.com/helldivers2/mods/15413) by soulls00. The Repatcher and Mod Inspector are for your own mods: before opening a mod they ask you to confirm it's yours or that its author allows it (many authors do in their Nexus page's Permissions section).
- **Languages:** English, Simplified Chinese, Japanese.

## Credits

- **RaidingForPants**: the Repatcher is based on [hd2-repatcher](https://github.com/RaidingForPants/hd2-repatcher) (MIT licence).
- **eigeen**: the Repatcher follows rules from [hd2-mod-crates](https://github.com/eigeen/hd2-mod-crates) (MIT licence).
- **xypwn**: the text-file reader follows the format as read by [filediver](https://github.com/xypwn/filediver) (BSD licence).
- **soulls00**: [HD2 Retagger](https://www.nexusmods.com/helldivers2/mods/15413), which the Retagger shortcut opens. It's their tool, not part of Echelon: get it from their page and endorse it if it helps.
- **cowboybingus**, for the Bingus Shared Loader.
- Developed with the help of AI (Claude).

## Privacy

Echelon works offline. Its online features are off until you turn them on in the first-time setup or Settings: update checks (GitHub), mod-text translation (MyMemory), and profile sharing (only when you share or open a profile). It has no tracking or advertising.

## Support

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/E1E81DSD9)

Echelon is free, and every feature is available to everyone. If you'd like to support its development, you can leave a tip on [Ko-fi](https://ko-fi.com/avaleine). Donations are entirely optional and don't unlock anything.

## Reporting a problem

Open an [issue](../../issues) and attach your latest log from `%APPDATA%\Echelon\logs` (Settings > System > About shows the exact path).

## Legal

Echelon is an unofficial fan-made tool, not affiliated with or endorsed by Arrowhead Game Studios or Sony Interactive Entertainment. Using it means accepting the [end-user licence agreement](EULA.txt). Third-party components and their licences are listed in [THIRD_PARTY_NOTICES.txt](THIRD_PARTY_NOTICES.txt).
