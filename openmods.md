# UE4SS

The official [RE-UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) script loader, unchanged, with one ready zip per tested
Unreal game: UE4SS plus that game's config.

## What it does

UE4SS (Unreal Engine 4/5 Scripting System) loads Lua and C++ mods into Unreal Engine games while they run. Many mods
need it. This listing republishes one official UE4SS build, so it can be found on openmods:

- UE4SS `v3.0.1-1181-g83330635`: the official `experimental-latest` build of 2026-10-17 (commit
  [`83330635`](https://github.com/UE4SS-RE/RE-UE4SS/commit/8333063595fa3c49ad307f3b0f732accbb760d25)). The stable
  UE4SS releases (v3.0.1 from 2024) are too old for many Unreal Engine 5 games.
- One ready zip per tested game: the official UE4SS files, plus the UE4SS team's own config for that game when the
  team has one (from `zCustomGameConfigs.zip` of the same build).
- Nothing else: no file is changed, and no mod is added. The official files of the build are attached to the release
  as well, so you can compare.

| Game | Zip | Config | Tested |
|---|---|---|---|
| The Blood of Dawnwalker | `dawnwalker_ue4ss_v3.0.1-1181-g83330635.zip` | `TheBloodOfDawnwalker` (the UE4SS team's) | Patch 2, 2026-10-22 |
| Clair Obscur: Expedition 33 | `expedition33_ue4ss_v3.0.1-1181-g83330635.zip` | none: the UE4SS team has none, and the default settings work | 1.5.6 (Steam), 2026-10-23 |
| Mortal Shell II | `mortalshell2_ue4ss_v3.0.1-1181-g83330635.zip` | `MortalShell2` (the UE4SS team's) | 1.12.0, 2026-10-23 |
| Phantom Blade Zero | none yet: use the official `UE4SS_v3.0.1-1181-g83330635.zip` | none: the UE4SS team has none in `zCustomGameConfigs.zip` of this build | not tested yet |

Phantom Blade Zero (release 2026-10-28, Unreal Engine 5, Steam app 4115450) is listed here, but not tested yet, and
the release has no zip for it yet. A tested zip follows when UE4SS works in the game. Until then, use the official
`UE4SS_v3.0.1-1181-g83330635.zip` from the release. `zCustomGameConfigs.zip` of this build has no config for the game,
so UE4SS runs with its default settings. It may not work with the game yet.

## Screenshots

![UE4SS](docs/cover.png)

## How to install

1. Close the game.
2. Download the zip for your game (table above) from the latest release on GitHub.
3. Unpack it into the game's `Binaries\Win64\` folder, next to the game's exe:
   - The Blood of Dawnwalker: `Dawnwalker\Binaries\Win64\`, next to `Dawnwalker.exe`.
   - Clair Obscur: Expedition 33: `Sandfall\Binaries\Win64\`, next to `SandFall-Win64-Shipping.exe`.
   - Mortal Shell II: `MortalShell2\Binaries\Win64\`, next to `MortalShell2-Win64-Shipping.exe`.
   - Phantom Blade Zero: not tested yet, so its folder and exe are not named here. Unpack the official zip into the
     game's `Binaries\Win64\` folder that holds the game's exe.

   You then have `Win64\dwmapi.dll` and the folder `Win64\ue4ss\`.
4. Start the game. UE4SS writes its log to `Win64\ue4ss\UE4SS.log`.

To remove UE4SS: close the game, delete `Win64\dwmapi.dll` and the folder `Win64\ue4ss\`.

If you already use another UE4SS package for the game, use only one of them: delete the other one's `dwmapi.dll` and
`ue4ss\` folder first, and keep your mods from its `ue4ss\Mods\` folder.

## How to use

UE4SS mods go into `Win64\ue4ss\Mods\<mod name>\`. A mod with an `enabled.txt` file in its folder starts by itself;
other mods are listed in `Win64\ue4ss\Mods\mods.txt`. The build comes with UE4SS's own helper mods: the game console
on `~`, `^` or `F10` (ConsoleEnablerMod), the cheat manager (CheatManagerEnablerMod), a loader for Blueprint mods in
the game's `Content\Paks\LogicMods\` folder (BPModLoaderMod; `Dawnwalker\Content\Paks\LogicMods\`,
`Sandfall\Content\Paks\LogicMods\` or `MortalShell2\Content\Paks\LogicMods\`), and keys for dumps (Keybinds).

## Compatibility

- The Blood of Dawnwalker: Patch 2 (`dw1-pc-258504-shipping-patch2-all-CL-258504`, Unreal Engine 5.5.4). Tested on
  2026-10-22: main menu, save loads, the helper mods, and a Lua mod.
- Clair Obscur: Expedition 33: 1.5.6 (`1.5.6.0`, Steam; Unreal Engine 5.4.4). Tested on 2026-10-23: game start, save
  load, the helper mods, and UE4SS's header and mapping dumps.
- Mortal Shell II: 1.12.0 (Unreal Engine 5.6). Tested on 2026-10-23: game start, save load, the helper mods, and
  UE4SS's header dump.
- Phantom Blade Zero: not tested yet (release 2026-10-28, Unreal Engine 5, Steam app 4115450). Until a tested zip
  follows, use the official `UE4SS_v3.0.1-1181-g83330635.zip`; the UE4SS team has no config for the game in
  `zCustomGameConfigs.zip` of this build.
- Other games are not tested here. For them, use the official `UE4SS_v3.0.1-1181-g83330635.zip` with your game's
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
- This is an experimental build of UE4SS. Report problems with UE4SS itself to the
  [UE4SS issues](https://github.com/UE4SS-RE/RE-UE4SS/issues), and problems with this package here.

## How to build

This package builds nothing: it repackages the official build. Building UE4SS from source needs Visual Studio and
access to Epic Games' Unreal source; see the [UE4SS documentation](https://github.com/UE4SS-RE/RE-UE4SS#build-requirements).
`FORK.md` lists exactly what this repository adds to UE4SS.

## Credits

UE4SS is made by the [UE4SS-RE team and its contributors](https://github.com/UE4SS-RE/RE-UE4SS/graphs/contributors),
MIT license. This listing and package: Kintaro. MIT license, as UE4SS. This package is unofficial: the UE4SS team did
not make it and does not support it.
