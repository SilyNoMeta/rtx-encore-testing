# Issue 94 - Microsoft Flight Simulator 2024 menu test

Download: [rtx-encore-issue94-menu.zip](rtx-encore-issue94-menu.zip)

Test version: 1.5.2+issue94
This build carries a fix for the menu never attaching in this game. It is not a confirmed fix until it is tested in the game.

1. Close the game and keep a copy of the RTX Encore `version.dll` currently installed in the game folder.
2. Replace only that `version.dll` with the `version.dll` from this archive, in the same folder as `FlightSimulator2024.exe`. The archive also contains `rtx-encore.dll` for installations that use it; install only the proxy you normally use. Keep your settings and the game's files as they are, including the Glass Cockpit DLSS Fix `dxgi.dll` if you use it.
3. Keep `logGraphics` and `logDxgiWrappers` on in `rtx-encore.jsonc`, as in the traced session of the report.
4. Start the game, reach the main menu, then press Insert. The menu should open and show version 1.5.2+issue94. Also try it during a flight, with frame generation on.
5. Report whether the menu opens, whether frame generation still runs as before, and anything unusual (a crash, a black screen, a freeze when the swap chain is recreated after changing a graphics setting).
6. Return the whole `rtx-encore-logs` folder from that session either way, plus the menu report if the menu opened.

Restore the backed-up DLL after testing. Avoid a Hub update or repair during the test: it may replace the test DLL.

Thanks to @jtsorlinis for the report and the traced logs: https://github.com/SilyNoMeta/rtx-encore/issues/94
This build has local automated validation only; no in-game result is claimed.
