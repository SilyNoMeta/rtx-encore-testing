# Issue #33: Star Wars Outlaws crashes on launch

[Issue #33](https://github.com/SilyNoMeta/rtx-encore/issues/33). One build, `1.0.0-rc.3+issue33-compat`: rc.3 plus a
way to leave out two parts of RTX Encore that DLSSG-Transfusion did not have, one at a time, to find which one the
game does not accept.

`rtx-encore-issue33-compat.zip` holds:

| File | Use |
| :--- | :--- |
| `version.dll` | The test build. Put it in the game folder, beside `Outlaws.exe`, in place of your RTX Encore file. If you normally use another name (`winmm.dll`, `dxgi.dll`, `dinput8.dll`), rename it to that name. |
| `A-menu-off\rtx-encore.compat` | Leaves the in-game RTX Encore menu out. |
| `B-load-hooks-off\rtx-encore.compat` | Leaves out RTX Encore's watch on the game's DLL loading. |
| `C-both-off\rtx-encore.compat` | Leaves out both. |

`rtx-encore.compat` is a small text file. It goes **beside the DLL**, in the game folder. Only one at a time: copy
the one of the test over the previous one. Without it, the build behaves like rc.3.

## What to test

Start the game once for each test, then note whether it crashes at launch:

1. **A:** copy `A-menu-off\rtx-encore.compat` into the game folder. Start the game.
2. **B:** replace it with `B-load-hooks-off\rtx-encore.compat`. Start the game.
3. **C:** replace it with `C-both-off\rtx-encore.compat`. Start the game.

If one of them starts, you can stop there and tell us which one. In test A and C the RTX Encore menu does not open;
that is expected. The FPS/multiplier overlay may be missing too.

After each launch, keep the `rtx-encore-logs` folder (or rename it, for example `logs-A`), and send the folders back
in the issue with the result of each test. The first lines of each log show `1.0.0-rc.3+issue33-compat` and a line
starting with `[COMPAT]` that names what was left out.

Then delete `rtx-encore.compat` and put your usual RTX Encore file back.

`BUILD.txt` names the source revision of this build, and `SHA256SUMS` the checksums.
