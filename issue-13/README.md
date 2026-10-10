# Issue #13: Starfield crash when turning Frame Generation on

[Issue #13](https://github.com/SilyNoMeta/rtx-encore/issues/13). One build to test:

| Build | What differs from 1.0.0-beta.2 |
| :--- | :--- |
| `rtx-encore-issue13-fix-r1.zip` | The fix: when the game hands its DXGI factory to Streamline (`slUpgradeInterface`), Streamline now receives the real DXGI factory instead of RTX Encore's wrapper, which DLSS Frame Generation then used as if it were DXGI's own object. The menu is included. |

The earlier `diagnostics` and `no-menu` builds are superseded and were removed from this folder.

## What to test

Use `version.dll` from the zip, with BetterConsole, the Steam overlay and your other mods as usual.

1. Start the game with Frame Generation **on** (it stayed on after the `no-menu` test). Does the game start and run
   with Frame Generation, and does the RTX Encore menu open (**Insert**)?
2. In the game's settings, turn Frame Generation **off**, then **on** again. Does the game survive both changes?

Send back the whole `rtx-encore-logs` folder from that session, whether it crashes or not. The new line to look for
starts with `MFG_PROXY_UI interface upgrade`.

`BUILD.txt` names the commit and the CI run of this build, and `SHA256SUMS` its checksum. The first lines of the log
show the version `1.0.0-beta.2+issue13-fix-r1`.
