# Issue #13: Starfield crash when turning Frame Generation on

**Current candidate: [factory-upgrade-r1 — download and one-session instructions](factory-upgrade-r1/README.md).**

Use that candidate for the next test. It keeps the menu enabled and adds detailed diagnostics. Send the entire log folder and the configuration, whether it works or crashes.

## Previous comparison builds (already tested)

These files are retained as the record of the previous comparison for [issue #13](https://github.com/SilyNoMeta/rtx-encore/issues/13). There is no need to test them again.

| Build | What differs from 1.0.0-beta.2 |
| :--- | :--- |
| `rtx-encore-issue13-no-menu.zip` | The in-game menu is left out, as when the file is named `d3d12.dll`. Settings are still read from `rtx-encore.jsonc`. |
| `rtx-encore-issue13-diagnostics.zip` | The full mod with the menu. |

Both builds log extra lines each time the game creates its swap chain, and release the game's back buffers held by
the FPS/multiplier overlay before a new swap chain is created for the same window.

The tester reported working FG with `no-menu` and a startup crash with `diagnostics`, both installed as `version.dll`.

The `BUILD.txt` and `SHA256SUMS` in this directory identify those **previous** builds. The current candidate has its own files in `factory-upgrade-r1/`.
