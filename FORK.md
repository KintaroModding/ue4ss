# About this fork

This repository is a fork of [RE-UE4SS](https://github.com/UE4SS-RE/RE-UE4SS) by the UE4SS-RE team and its
contributors (MIT license, see [LICENSE](LICENSE)). It exists so that one official UE4SS build, with a ready package
for each tested game, can be listed on [openmods](https://openmods.nexus), which reads `openmods.json` and
`openmods.md` from the default branch of a GitHub repository. Its first name was `dawnwalker_ue4ss`; since
2026-10-23 it is `ue4ss`, one listing for all tested games.

- The branch `release` starts at upstream commit
  [`8333063595fa3c49ad307f3b0f732accbb760d25`](https://github.com/UE4SS-RE/RE-UE4SS/commit/8333063595fa3c49ad307f3b0f732accbb760d25)
  (2026-10-17), the source of the official `experimental-latest` build `UE4SS_v3.0.1-1181-g83330635.zip`.
- The UE4SS code is unchanged. This fork adds only `FORK.md`, `openmods.json`, `openmods.md` and the cover image
  `docs/cover.png`. It is unofficial: the UE4SS team did not make it and does not support it.
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
