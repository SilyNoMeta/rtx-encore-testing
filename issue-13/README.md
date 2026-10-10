# Issue #13: Starfield crash when turning Frame Generation on

[Issue #13](https://github.com/SilyNoMeta/rtx-encore/issues/13). Two builds of the same code, to compare:

| Build | What differs from 1.0.0-beta.2 |
| :--- | :--- |
| `rtx-encore-issue13-no-menu.zip` | The in-game menu is left out, as when the file is named `d3d12.dll`. Settings are still read from `rtx-encore.jsonc`. |
| `rtx-encore-issue13-diagnostics.zip` | The full mod with the menu. |

Both builds log extra lines each time the game creates its swap chain, and release the game's back buffers held by
the FPS/multiplier overlay before a new swap chain is created for the same window.

The DLLs are about 20 MB instead of 93 MB: they leave out the open Ray Reconstruction engine (`"engine": "opendlss"`).
NVIDIA's engine, the one Starfield uses by default, is unchanged.

## What to test

Use `version.dll` from each zip, with BetterConsole and your other mods as usual.

1. **`no-menu`:** start the game and turn Frame Generation on (or load with it already on). Does it still crash?
   The log says `disabled by build` for the menu.
2. **`diagnostics`:** do the same. Does it still crash?

In both cases, send the `rtx-encore-logs` folder, crash or not: the new lines start with `[SWAPCHAIN]` and, in
`diagnostics` only, `MFG_PROXY_UI swapchain proxy`.

Then put your usual file back (`d3d12.dll` works in the meantime).

`BUILD.txt` names the commit and the CI run of these builds, and `SHA256SUMS` their checksums.
