# YSAP Level Picker

A BepInEx mod for **You Suck at Parking**:

- **Level Picker** (F7 in a private match lobby): the host chooses the level for each round and can share custom levels with everyone in the lobby.
- **Level Editor** (main menu button, RT/R2 or F8): create levels or edit copies of official ones, then play or test them alone.

Every player in a lobby needs the mod.

## Install

Download `YSAP-LevelPicker-<version>.zip` from the [latest release](https://github.com/MartinKleinschrot/ysap-levelpicker/releases/latest) and extract it into the game folder (Steam: right-click the game > Manage > Browse local files), next to `YSAP.exe`. See `INSTALL - YSAP Level Picker.txt` in the zip for details.

## Updates

At every game start the mod checks this repository's latest release. If it is newer, it downloads `YSAP.LevelPicker.dll`, verifies its SHA-256 against the release, replaces the installed plugin and offers to restart the game. To turn this off, set `AutoUpdate = false` in `BepInEx/config/ysap.levelpicker.cfg`.
