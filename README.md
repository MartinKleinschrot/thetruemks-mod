# TheTrueMK's mod

A BepInEx mod for **You Suck at Parking**:

- **Private match lobby** (F7 / "Lobby options"): everyone votes for the next map before each round, rates maps after playing them and sees how often each map was played. The host can also pick the levels by hand and share custom levels with everyone in the lobby.
- **Level Editor** (main menu button, RT/R2 or F8): create levels or edit copies of official ones, then play or test them alone.

Every player in a lobby needs the mod.

## Install

Download `TheTrueMKs-mod-<version>.zip` from the [latest release](https://github.com/MartinKleinschrot/thetruemks-mod/releases/latest) and extract it into the game folder (Steam: right-click the game > Manage > Browse local files), next to `YSAP.exe`. See `INSTALL - TheTrueMK's mod.txt` in the zip for details.

## Updates

At every game start the mod checks this repository's latest release. If it is newer, it downloads `TheTrueMKsMod.dll`, verifies its SHA-256 against the release, replaces the installed plugin and offers to restart the game. To turn this off, set `AutoUpdate = false` in `BepInEx/config/thetruemk.mod.cfg`.
