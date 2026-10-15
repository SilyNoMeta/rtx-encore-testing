# Issue #33: Star Wars Outlaws crashes on launch — trace build

[Issue #33](https://github.com/SilyNoMeta/rtx-encore/issues/33). Your isolation tests showed that the game closes
whenever the RTX Encore menu attaches to its swap chain. This build, `1.0.0-rc.3+issue33-trace`, records everything
the game does with the menu's DXGI objects up to the crash, so we can see what goes wrong. Three launches.

## What is in `rtx-encore-issue33-trace.zip`

- `version.dll`: the trace build.
- `tests\<name>\`: one folder per test, each with `rtx-encore.compat` (what to record or change) and
  `rtx-encore.jsonc` (settings; a fresh install with the graphics trace on and 60 logs kept).

## Before you start

1. In the game folder (beside `Outlaws.exe`), **move your own `rtx-encore.jsonc`, `rtx-encore.compat` (if any) and
   RTX Encore DLL somewhere safe**.
2. Put the trace `version.dll` there. If you normally use another name (`winmm.dll`, `dxgi.dll`, `dinput8.dll`), use
   that name instead, and keep it for every test.
3. Delete or move the `rtx-encore-logs` folder, so that it holds only these tests.

## The three tests

For each test, copy **both files** of its folder into the game folder (replacing those of the previous test), start
the game from Ubisoft Connect, and note **crash** or **starts**. If it starts, wait in the main menu for about
30 seconds, then quit.

| Test | What changes |
| :--- | :--- |
| `1-trace` | The menu as in rc.3, with every call recorded. Expected to crash. |
| `2-trace-no-menu-drawing` | The menu is attached but never draws. |
| `3-trace-no-menu-renderer` | The menu is attached without its drawing engine. |

Do all three, even if one starts. The menu does not open in tests 2 and 3; that is expected.

## What to send back

In the issue:

1. The result of each test, for example `1 crash, 2 crash, 3 starts`.
2. The whole `rtx-encore-logs` folder, zipped. When the game crashes, the folder also holds one or two `.dmp` files
   (a snapshot of the game's memory at the crash, to analyse it). They are usually 5 to 50 MB. If the zip is too
   large for GitHub (25 MB), upload it to a file-sharing service and post the link, or send the logs and the
   `.dmp` files in separate zips.

The `.dmp` files contain the game's memory at the moment of the crash: graphics data, the game's own state and the
paths of the loaded files on your PC (such as your user folder name). No passwords are expected there, but if you
prefer not to share them, send the `.log` files only and say so.

Then delete `rtx-encore.compat`, and put your own `rtx-encore.jsonc` and RTX Encore DLL back.

`BUILD.txt` names the source revision of this build, and `SHA256SUMS` the checksum of the zip.
