# About this fork

This repository is a fork of [RE-UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) by the UE4SS-RE team and its
contributors (MIT license, see [LICENSE](LICENSE)). It exists so that official UE4SS builds, with a ready package for
each tested game, can be listed on [openmods](https://openmods.nexus), which reads `openmods.json` and `openmods.md`
from the default branch of a GitHub repository. Its first name was `dawnwalker_ue4ss`; since 2026-10-23 it is
`ue4ss`, one listing for all tested games.

- The branch `release` starts at upstream commit
  [`8333063595fa3c49ad307f3b0f732accbb760d25`](https://github.com/UE4SS-RE/RE-UE4SS/commit/8333063595fa3c49ad307f3b0f732accbb760d25)
  (2026-10-17), the source of the official `experimental-latest` build `UE4SS_v3.0.1-1181-g83330635.zip`. Since
  2026-10-29 it also holds upstream commit
  [`cdbc0b66cb2bb5b4a3d2f69b6e61a8460961e54c`](https://github.com/UE4SS-RE/RE-UE4SS/commit/cdbc0b66cb2bb5b4a3d2f69b6e61a8460961e54c)
  (merged; 2026-10-23), the source of `UE4SS_v3.0.1-1183-gcdbc0b66.zip`, and since 2026-10-31 upstream commit
  [`f885e8d2d4dd25258082538f1a9fd56a1c3b1bf1`](https://github.com/UE4SS-RE/RE-UE4SS/commit/f885e8d2d4dd25258082538f1a9fd56a1c3b1bf1)
  (merged; 2026-10-30), the source of `UE4SS_v3.0.1-1188-gf885e8d2.zip`.
- The UE4SS code is unchanged. This fork adds only `FORK.md`, `openmods.json`, `openmods.md` and the cover image
  `docs/cover.png`. It is unofficial: the UE4SS team did not make it and does not support it.
- The release `v3.0.1-1188-gf885e8d2` (2026-10-31) holds:
  - `UE4SS_v3.0.1-1188-gf885e8d2.zip` and `zCustomGameConfigs.zip`: the official files of that build, unchanged.
    (1188 differs from 1183 only in `dwmapi.dll` and `ue4ss\UE4SS.dll`; `zCustomGameConfigs.zip` holds the same 191
    files.)
  - `phantombladezero_ue4ss_v3.0.1-1188-gf885e8d2.zip`: the official UE4SS 1188 zip with our config
    `PhantomBladeZero` copied over its `ue4ss\` folder: the two signature files, `MemberVariableLayout.ini` and the
    Keybinds change, as in `v3.0.1-1183-gcdbc0b66` (below). No BPModLoaderMod change: 1188 finds this game's
    `LogicMods` folder itself.
  - The three 1181 game zips and `UE4SS_v3.0.1-1181-g83330635.zip`: byte for byte the files of the release
    `v3.0.1-1181-g83330635`.
  - `SHA256SUMS.txt`.
- The release `v3.0.1-1183-gcdbc0b66-r2` (2026-10-30) is the build 1183 with a second Phantom Blade Zero package:
  - `phantombladezero_ue4ss_v3.0.1-1183-gcdbc0b66-r2.zip`: the package of `v3.0.1-1183-gcdbc0b66` (below) plus
    `Mods\BPModLoaderMod\Scripts\main.lua`, the official file with a fallback for the game's folder layout (Changes).
  - All other files byte for byte the files of the release `v3.0.1-1183-gcdbc0b66`.
- The release `v3.0.1-1183-gcdbc0b66` (2026-10-29) holds:
  - `UE4SS_v3.0.1-1183-gcdbc0b66.zip` and `zCustomGameConfigs.zip`: the official files of that build, unchanged.
    (`zCustomGameConfigs.zip` of 1183 holds the same 191 files as the one of 1181; only the dates in the zip differ.)
  - `phantombladezero_ue4ss_v3.0.1-1183-gcdbc0b66.zip`: the official UE4SS 1183 zip with our config `PhantomBladeZero`
    copied over its `ue4ss\` folder:
    - `UE4SS_Signatures\GUObjectArray.lua` (from the official configs `MetalGearSolidDelta` and `Split Fiction`) and
      `UE4SS_Signatures\GNatives.lua` (from the official config `Far Far West`): the UE4SS team's code, unchanged,
      with a comment on top that names the source;
    - `MemberVariableLayout.ini` (ours): the game's layout of `FUObjectArray`, `TUObjectArray`, `UStruct`, `UClass`,
      `UFunction`, `UScriptStruct`, `FField` and `FFieldClass`, read from the running game;
    - `Mods\Keybinds\Scripts\main.lua`: the official file with one line changed (below).
  - `dawnwalker_ue4ss_v3.0.1-1181-g83330635.zip`, `expedition33_ue4ss_v3.0.1-1181-g83330635.zip`,
    `mortalshell2_ue4ss_v3.0.1-1181-g83330635.zip` and `UE4SS_v3.0.1-1181-g83330635.zip`: byte for byte the files of
    the release `v3.0.1-1181-g83330635`, for the games tested with that build.
  - `SHA256SUMS.txt`.
- The release `v3.0.1-1181-g83330635` holds:
  - `UE4SS_v3.0.1-1181-g83330635.zip` and `zCustomGameConfigs.zip`: the official files of that build, unchanged.
  - `dawnwalker_ue4ss_v3.0.1-1181-g83330635.zip`: the official UE4SS zip with the official `TheBloodOfDawnwalker`
    config of `zCustomGameConfigs.zip` copied over its `ue4ss\` folder, as the UE4SS team intends for this game.
  - `expedition33_ue4ss_v3.0.1-1181-g83330635.zip`: the files of the official UE4SS zip, unchanged (the UE4SS team
    has no config for Clair Obscur: Expedition 33, and the default settings work).
  - `mortalshell2_ue4ss_v3.0.1-1181-g83330635.zip`: the official UE4SS zip with the official `MortalShell2` config of
    `zCustomGameConfigs.zip` copied over its `ue4ss\` folder.
- Problems with UE4SS itself belong to the [UE4SS issues](https://github.com/UE4SS-RE/RE-UE4SS/issues). For the
  official builds, see the [UE4SS releases](https://github.com/UE4SS-RE/RE-UE4SS/releases).

## Changes

| Date | Version | Change | Files |
|---|---|---|---|
| 2026-10-22 | v3.0.1-1181-g83330635 | Fork made; openmods files added; no code change | `FORK.md`, `openmods.json`, `openmods.md` |
| 2026-10-22 | v3.0.1-1181-g83330635 | Cover image for the openmods page; no code change | `docs/cover.png`, `openmods.json`, `openmods.md` |
| 2026-10-23 | v3.0.1-1181-g83330635 | One listing for all tested games: Clair Obscur: Expedition 33 added, repository renamed to `ue4ss`; no code change | `FORK.md`, `openmods.json`, `openmods.md` |
| 2026-10-23 | v3.0.1-1181-g83330635 | A cover that fits every game page; no code change | `docs/cover.png` |
| 2026-10-23 | v3.0.1-1181-g83330635 | Mortal Shell II added; no code change | `FORK.md`, `openmods.json`, `openmods.md` |
| 2026-10-27 | v3.0.1-1181-g83330635 | Phantom Blade Zero listed, not tested yet and without a zip; no code change | `FORK.md`, `openmods.json`, `openmods.md` |
| 2026-10-29 | v3.0.1-1183-gcdbc0b66 | Upstream `cdbc0b66` merged (build 1183); Phantom Blade Zero tested, with its zip and our config; no code change | `FORK.md`, `openmods.json`, `openmods.md` |
| 2026-10-29 | v3.0.1-1183-gcdbc0b66 | In the Phantom Blade Zero zip only: the Keybinds helper's Ctrl+Num6 calls `DumpUSMAP(false)` instead of `DumpUSMAP()` (no Blueprint-generated types; with them UE4SS's mapping dump crashes this game), with a comment line above it | `ue4ss/Mods/Keybinds/Scripts/main.lua` in `phantombladezero_ue4ss_v3.0.1-1183-gcdbc0b66.zip` |
| 2026-10-30 | v3.0.1-1183-gcdbc0b66-r2 | In the Phantom Blade Zero zip only: BPModLoaderMod gets a fallback. When `IterateGameDirectories` returns nil (the game's exe is in `platform\steam\`, not in `<Game>\Binaries\Win64\`), the script finds `ProjectPBZ\Content\Paks` from its own path, checks `LogicMods` with `io.open` and lists it with `io.popen("dir /b /s /a-d ...")`, as a table of the same shape. The official code path is unchanged and runs first; comment lines name the reason | `ue4ss/Mods/BPModLoaderMod/Scripts/main.lua` in `phantombladezero_ue4ss_v3.0.1-1183-gcdbc0b66-r2.zip` |
| 2026-10-31 | v3.0.1-1188-gf885e8d2 | Upstream `f885e8d2` merged (build 1188, with the fixes of `IterateGameDirectories` and `UObject:CallFunction`); Phantom Blade Zero tested with it; no code change | `FORK.md`, `openmods.md` |
| 2026-10-31 | v3.0.1-1188-gf885e8d2 | In the Phantom Blade Zero zip: the BPModLoaderMod fallback of `-r2` removed, the official file again; the Keybinds change stays | `ue4ss/Mods/BPModLoaderMod/Scripts/main.lua` in `phantombladezero_ue4ss_v3.0.1-1188-gf885e8d2.zip` |
