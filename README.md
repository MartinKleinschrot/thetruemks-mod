# TheTrueMK's mod

A BepInEx mod for **You Suck at Parking**:

- **Private match lobby** (F7 / "Options"): the host can turn on a map vote (everyone votes for the next map before each round), pick the levels by hand and share custom levels with everyone in the lobby. Without either, the match plays the selected biomes as usual. After each round everyone rates the map with D-pad up or down (👍 / 😭), and each player's rating pops up next to their name in the results. The vote cards show who made each map, how often you've played it and its 👍 / 😭 counts.
- **Change your car in the private lobby** (F6 / "Car"): every car you own plus the mod cars, without going back to the garage. Everyone in the lobby sees the new car.
- **Invite Steam friends** (F8 in the private lobby): a list of your Steam friends (who's playing You Suck at Parking first). Tick as many as you like and invite them all with one click, or invite everyone who's playing right now. They accept in Steam and land in your lobby, no lobby code needed. Steam's own invite dialog is still there as a button.
- **Level Editor** (main menu button, RT/R2 or F8): create levels or edit copies of official ones, then play or test them alone.
- **TheTrueMK's maps**: tricky custom levels that install themselves and update automatically. They're in "My levels" and can be shared in a private lobby like your own:
  - *Teleporter Tangle*: islands linked only by one-way teleporter gates. Which gates lead to the parking spots?
  - *Minefield*: an open square full of land mines and spiked blocks.
  - *Hammer Time*: narrow lanes between crash borders, with swinging hammers, boxing gloves and rotating walls.
  - *Sky Ramps*: ramps up to narrow roads high above the sea, with no fences and gloves that punch you off.
  - *Hidden Alleys*: a forest town full of dead-end alleys. Only three hide a parking spot.
  - **130 arenas** (*Tiny Overpass*, *Chaotic Overpass*, *Crazy Alley*, *Dizzy Yard*, ...): small multi-level arenas built for chaos. 8 to 10 parking spots are packed close together on plazas stacked up to three levels high, with ramps, bridges and lots of jumps over the sea (hit the jump pad at full speed!). Some spots hide under the upper decks or behind trees.

  With the map vote on, a few maps of the selected biomes that all players have (TheTrueMK's maps, or levels the host shared) join the vote: one or two of the vote cards are custom maps. The host can turn that off in the options.
- **Garage overview** (C in the garage): every car at once in two tabs, GAME CARS and MOD CARS, with NEW tags for cars you just got.
- **Mod cars**: 55 fun looks for your car (a dino on rollerblades, a rubber duck in a bathtub, a haunted coffin, Santa's sleigh, ...) in themes: Classic, Halloween, Christmas, Easter, Summer, Food, Animals, Space, Monsters and Sports. You start with the dino. **Every multiplayer match you finish unlocks a new one at random.** Every car can drop all year, but a seasonal theme's cars are 4x more likely in their season (Halloween 1 Oct - 7 Nov, Christmas 1 Dec - 6 Jan, Easter 15 Mar - 30 Apr, Summer Jun - Aug). When you win one, "Equip now" (Y on the controller, E on the keyboard) puts it on right away; otherwise pick it in the garage or the private lobby under the MOD CARS tab. Other players with the mod see your mod car, and players without it see your normal car. New themes arrive through this repository without a mod update.

Every player in a lobby needs the mod (except for joining through a Steam invite, which works without it).

## Install

Download `TheTrueMKs-mod-<version>.zip` from the [latest release](https://github.com/MartinKleinschrot/thetruemks-mod/releases/latest) and extract it into the game folder (Steam: right-click the game > Manage > Browse local files), next to `YSAP.exe`. See `INSTALL - TheTrueMK's mod.txt` in the zip for details.

## Updates

At every game start the mod checks this repository's latest release. If it is newer, it downloads `TheTrueMKsMod.dll`, verifies its SHA-256 against the release, replaces the installed plugin and offers to restart the game. To turn this off, set `AutoUpdate = false` in `BepInEx/config/thetruemk.mod.cfg`.

## Make your own mod car

Mod cars are JSON files made of simple shapes. Put yours in `BepInEx/config/thetruemk.cars/local/` and press F5 in the garage overview to reload. A car you make yourself is unlocked for you. Other players only see it if they have the same file.

```json
{
  "format": 1,
  "theme": "Mine",
  "cars": [{
    "id": "mine-ball",
    "name": "Bouncy Ball",
    "nodes": [{"name": "ball", "at": [0, 1.2, 0]}],
    "parts": [
      {"shape": "sphere", "node": "ball", "at": [0, 0, 0], "size": [2.4, 2.4, 2.4], "color": "#E24B3B", "paint": true},
      {"shape": "sphere", "node": "ball", "at": [0.4, 0.4, 1.0], "size": [0.4, 0.4, 0.4], "color": "#FFFFFF", "mirror": true},
      {"shape": "wheel", "at": [1.1, 0.1, 1.2], "radius": 0.3, "width": 0.14, "color": "#222222", "mirror": true},
      {"shape": "wheel", "at": [1.1, 0.1, -1.2], "radius": 0.3, "width": 0.14, "color": "#222222", "mirror": true}
    ],
    "hat": {"node": "ball", "at": [0, 1.2, 0], "scale": 0.5},
    "anim": [{"node": "ball", "pos": [0, 0.3, 0], "freq": 6, "wave": "up", "when": "moving"}]
  }]
}
```

- **Space**: +z is forward, the ground is at y -0.2, and the real wheels sit at x ±1.2, z ±1.3.
- **Shapes**: `sphere`, `cube`, `cylinder`, `capsule` (cylinders and capsules are 2 tall) and `wheel` (turns with the real wheels). Each part can also have `rot` (degrees), `"outline": false` and `"mirror": true` (adds the copy at -x).
- **Paint**: `"paint": true` uses the car's paint color, or the part's own color while the paint is grey. `"always"` uses the paint color even when it's grey.
- **Nodes** are groups that can move. `anim` adds to a node's position or rotation: amount × wave(time × `freq` + `phase`).
  - `wave`: `sin`, `up`, `down`, `const` or `spin`.
  - `when`: `always`, `moving` or `idle`.

The built-in cars are in [`cars/`](cars) and are good examples.

## Credits

Rating emoji: [Twemoji](https://github.com/jdecked/twemoji) by Twitter, Inc. and other contributors, licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).
