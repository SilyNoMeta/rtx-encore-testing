# Issue #13: candidate with the menu enabled

Experimental build `1.0.0-beta.2+issue13-factory-upgrade-r1` for [the Starfield report](https://github.com/SilyNoMeta/rtx-encore/issues/13). This candidate addresses startup with Frame Generation and keeps the RTX Encore menu enabled. It still needs confirmation in the game.

[Download the ZIP](rtx-encore-issue13-factory-upgrade-r1.zip). Use the **`version.dll` already named in the ZIP**. The other DLL is the universal alternative; it is not needed for this test.

## One test session

1. Close Starfield and SFSE. Back up your current RTX Encore DLL and `rtx-encore.jsonc`. Install this ZIP's `version.dll` next to `Starfield.exe`. Move any other **RTX Encore** proxy copy out of the game folder, including the working `d3d12.dll` workaround. Keep BetterConsole, Steam overlay and your other mods as usual. Do not replace the game's `sl.*` DLLs.
2. Before launching, edit these entries in the **top-level `diagnostics` section** of your existing `rtx-encore.jsonc` (not `overlay.diagnostics`). Add `logGraphics` if missing; replace the values of existing entries rather than duplicating them. Keep your other settings:

   ```json
   "logGraphics": true,
   "logNr": true,
   "logHudUi": true,
   "logFilesKept": 20
   ```

   Preserve commas between entries. Do not replace the whole configuration with this fragment.
3. Launch through your usual SFSE route. If it reaches gameplay, check whether **Insert** opens the RTX Encore menu, close it, then turn the game's Frame Generation off and back on once. If FG starts off, enable it first. Play for one or two minutes, then exit normally. If it crashes, stop there; no need to repeat the run or remove more mods.
4. Whether it works or crashes, zip and send the **entire `rtx-encore-logs` folder** and the **`rtx-encore.jsonc` used for this session**. Say whether startup, FG and the Insert menu worked, or at which step it stopped. Keep every log filename: SFSE and the game can write separate files, and an existing crash log does not necessarily mean the game crashed.

The game log should show `1.0.0-beta.2+issue13-factory-upgrade-r1` near the top and `[GRAPHICS ...]` lines. These traces cover graphics startup, interface changes, object lifetimes, swapchain creation, the first presentations and resize operations; crash records also identify loaded binaries more precisely.

After collecting the logs, restore your backed-up DLL/configuration. This is a diagnostic test build, not a release or a performance benchmark.

## Build identification

`BUILD.txt` records the exact source commit, CI run and validation. `SHA256SUMS` contains the ZIP checksum and individual DLL checksums. Matching debugging symbols are retained privately for analysis.

The distributed components' notices are in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).
