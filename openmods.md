# UE4SS

The official [RE-UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) script loader with one ready zip per tested Unreal
game: UE4SS plus that game's config.

## What it does

UE4SS (Unreal Engine 4/5 Scripting System) loads Lua and C++ mods into Unreal Engine games while they run. Many mods
need it. This listing republishes official UE4SS builds, so they can be found on openmods:

- UE4SS `v3.0.1-1183-gcdbc0b66`: the official `experimental-latest` build of 2026-10-25 (commit
  [`cdbc0b66`](https://github.com/UE4SS-RE/RE-UE4SS/commit/cdbc0b66cb2bb5b4a3d2f69b6e61a8460961e54c)), for Phantom
  Blade Zero.
- UE4SS `v3.0.1-1181-g83330635`: the official `experimental-latest` build of 2026-10-17 (commit
  [`83330635`](https://github.com/UE4SS-RE/RE-UE4SS/commit/8333063595fa3c49ad307f3b0f732accbb760d25)), for the games
  tested with it; their zips stay unchanged. The stable UE4SS releases (v3.0.1 from 2024) are too old for many Unreal
  Engine 5 games.
- One ready zip per tested game: the official UE4SS files, plus the UE4SS team's own config for that game when the
  team has one (from `zCustomGameConfigs.zip`), or our own config where the game needs one (Phantom Blade Zero, below).
- Nothing else: UE4SS itself is not changed, and no mod is added. The official files of both builds are attached to
  the release as well, so you can compare.

| Game | Zip | Config | Tested |
|---|---|---|---|
| The Blood of Dawnwalker | `dawnwalker_ue4ss_v3.0.1-1181-g83330635.zip` | `TheBloodOfDawnwalker` (the UE4SS team's) | Patch 2, 2026-10-22 |
| Clair Obscur: Expedition 33 | `expedition33_ue4ss_v3.0.1-1181-g83330635.zip` | none: the UE4SS team has none, and the default settings work | 1.5.6 (Steam), 2026-10-23 |
| Mortal Shell II | `mortalshell2_ue4ss_v3.0.1-1181-g83330635.zip` | `MortalShell2` (the UE4SS team's) | 1.12.0, 2026-10-23 |
| Phantom Blade Zero | `phantombladezero_ue4ss_v3.0.1-1183-gcdbc0b66.zip` | `PhantomBladeZero` (ours, below) | Release (Steam build 26266538), 2026-10-29 |

### Phantom Blade Zero

UE4SS 1183 does not run in Phantom Blade Zero as it is: the game's engine (Unreal Engine 5.7.4) keeps some of its
core structures in its own order, and UE4SS does not find two engine functions. The zip adds our config for the game
to `ue4ss\`, worked out with tests in the running game:

- `UE4SS_Signatures\GUObjectArray.lua` and `UE4SS_Signatures\GNatives.lua`: the UE4SS team's own patterns from their
  configs for Metal Gear Solid Delta and Split Fiction (GUObjectArray) and for Far Far West (GNatives), unchanged; each
  matches exactly once in the game's exe.
- `MemberVariableLayout.ini`: the game's own layout of the object list (`FUObjectArray`, `TUObjectArray`), of
  `UStruct` and the types built on it (`UClass`, `UFunction`, `UScriptStruct`), and of `FField` and `FFieldClass`. Every
  other type matches UE4SS's Unreal Engine 5.7 layout.
- `Mods\Keybinds\Scripts\main.lua`: one line changed. Ctrl+Num6 writes the mapping file without Blueprint-generated
  types (`DumpUSMAP(false)`): with them, UE4SS crashes this game, because two of the game's AI Blueprints have enum
  properties without an enum.

## Screenshots

![UE4SS](docs/cover.png)

## How to install

1. Close the game.
2. Download the zip for your game (table above) from the latest release on GitHub.
3. Unpack it into the folder that holds the game's exe:
   - The Blood of Dawnwalker: `Dawnwalker\Binaries\Win64\`, next to `Dawnwalker.exe`.
   - Clair Obscur: Expedition 33: `Sandfall\Binaries\Win64\`, next to `SandFall-Win64-Shipping.exe`.
   - Mortal Shell II: `MortalShell2\Binaries\Win64\`, next to `MortalShell2-Win64-Shipping.exe`.
   - Phantom Blade Zero: `platform\steam\`, next to the large `PBZ.exe` (about 500 MB). Not `steam\` (its small
     `PBZ.exe` only starts the game) and not `ProjectPBZ\Binaries\Win64\` (it holds no exe).

   You then have `dwmapi.dll` and the folder `ue4ss\` next to the game's exe.
4. Start the game. UE4SS writes its log to `ue4ss\UE4SS.log` in that folder.

To remove UE4SS: close the game, delete `dwmapi.dll` and the folder `ue4ss\` next to the game's exe.

If you already use another UE4SS package for the game, use only one of them: delete the other one's `dwmapi.dll` and
`ue4ss\` folder first, and keep your mods from its `ue4ss\Mods\` folder.

## How to use

UE4SS mods go into `ue4ss\Mods\<mod name>\` next to the game's exe. A mod with an `enabled.txt` file in its folder
starts by itself; other mods are listed in `ue4ss\Mods\mods.txt`. The build comes with UE4SS's own helper mods: the
game console on `~`, `^` or `F10` (ConsoleEnablerMod), the cheat manager (CheatManagerEnablerMod), a loader for
Blueprint mods in the game's `Content\Paks\LogicMods\` folder (BPModLoaderMod; `Dawnwalker\Content\Paks\LogicMods\`,
`Sandfall\Content\Paks\LogicMods\` or `MortalShell2\Content\Paks\LogicMods\`; not in Phantom Blade Zero, see Known
issues), and keys for dumps (Keybinds: Ctrl+H the C++ headers, Ctrl+Num6 the mapping file).

## Compatibility

- The Blood of Dawnwalker: Patch 2 (`dw1-pc-258504-shipping-patch2-all-CL-258504`, Unreal Engine 5.5.4). Tested on
  2026-10-22: main menu, save loads, the helper mods, and a Lua mod.
- Clair Obscur: Expedition 33: 1.5.6 (`1.5.6.0`, Steam; Unreal Engine 5.4.4). Tested on 2026-10-23: game start, save
  load, the helper mods, and UE4SS's header and mapping dumps.
- Mortal Shell II: 1.12.0 (Unreal Engine 5.6). Tested on 2026-10-23: game start, save load, the helper mods, and
  UE4SS's header dump.
- Phantom Blade Zero: the release version (Steam build 26266538, `PBZ.exe` `CL-301524_JKS-17219`; Unreal Engine
  5.7.4). The game shows no version number. Tested on 2026-10-29: game start, save load, the helper mods, UE4SS's
  header dump (Ctrl+H) and mapping dump (Ctrl+Num6), and a Lua test mod that reads and writes the player's health and
  calls one of the game's functions.
- Other games are not tested here. For them, use the official `UE4SS_v3.0.1-1183-gcdbc0b66.zip` with your game's
  config from `zCustomGameConfigs.zip`, if the UE4SS team has one.
- A game update can need a new UE4SS build or config. Then check the
  [UE4SS releases](https://github.com/UE4SS-RE/RE-UE4SS/releases/tag/experimental-latest) for a newer build.

## Known issues

- The UE4SS log shows optional engine functions that were not found: `FUObjectHashTables::Get` and
  `ConsoleManagerSingleton` in The Blood of Dawnwalker, `ConsoleManagerSingleton` in Clair Obscur: Expedition 33.
  UE4SS works without them; no problem was seen.
- Mortal Shell II: the mapping dump (Ctrl+Num6 of the Keybinds helper) fails inside UE4SS. UE4SS catches the error
  and the game keeps running, but no mapping file is made. The log also says that UE4SS's quick object lookup failed
  its self test; UE4SS then uses its slower lookup, which works.
- Phantom Blade Zero:
  - Blueprint mods (`ProjectPBZ\Content\Paks\LogicMods\`) do not load: BPModLoaderMod stops ("the directory structure
    is unknown"), because the game's exe is not in `<Game>\Binaries\Win64\`. Lua mods work.
  - The log says that UE4SS could not hook `ProcessConsoleExec`. Console commands that UE4SS mods add may not work
    (not tested).
  - The mapping file holds native types only (the Ctrl+Num6 change above).
  - A game update can change the exe; then the patterns or the layout in our config may need an update.
- This is an experimental build of UE4SS. Report problems with UE4SS itself to the
  [UE4SS issues](https://github.com/UE4SS-RE/RE-UE4SS/issues), and problems with these packages here.

## How to build

This package builds nothing: it repackages the official builds. Building UE4SS from source needs Visual Studio and
access to Epic Games' Unreal source; see the [UE4SS documentation](https://github.com/UE4SS-RE/RE-UE4SS#build-requirements).
`FORK.md` lists exactly what this repository and its release files add to UE4SS.

## Credits

UE4SS is made by the [UE4SS-RE team and its contributors](https://github.com/UE4SS-RE/RE-UE4SS/graphs/contributors),
MIT license; the Phantom Blade Zero signatures are theirs too (from their custom game configs). This listing, the
packages and the Phantom Blade Zero layout: Kintaro. MIT license, as UE4SS. These packages are unofficial: the UE4SS
team did not make them and does not support them.
