# Issue #33: Star Wars Outlaws crashes on launch

[Issue #33](https://github.com/SilyNoMeta/rtx-encore/issues/33). One build, `1.0.0-rc.3+issue33-isolate`: rc.3 with
switches that leave out, part by part, everything RTX Encore does at launch. DLSSG-Transfusion 1.4.5.3 runs for you
and RTX Encore does not; these tests find which part makes the difference, in one go. Plan about 10 to 15 launches.

## What is in `rtx-encore-issue33-isolate.zip`

- `version.dll`: the test build.
- `tests\<name>\`: one folder per test, each with two files, `rtx-encore.compat` (what to leave out) and
  `rtx-encore.jsonc` (settings; the same as a fresh install except where a test turns an option off).

## Before you start

1. In the game folder (beside `Outlaws.exe`), **move your own `rtx-encore.jsonc` and RTX Encore DLL somewhere safe**.
2. Put the test `version.dll` there. If you normally use another name (`winmm.dll`, `dxgi.dll`, `dinput8.dll`),
   use that name instead, and keep it for every test.
3. Delete or move the `rtx-encore-logs` folder, so that it holds only these tests.

## How to run one test

1. Copy **both files** of the test folder into the game folder, replacing those of the previous test.
2. Start the game (from Ubisoft Connect as usual).
3. Note the result: **crash** (closes at launch) or **starts** (you reach the menu). If it starts, quit the game.

Each launch writes its own log in `rtx-encore-logs`; nothing is overwritten. The first lines of every log name
the test (`[COMPAT] rtx-encore.compat turns off: …`).

## Part 1 — do all seven

| Test | What is left out |
| :--- | :--- |
| `01-control` | Nothing: the build as it is. Should crash like rc.3. |
| `02-menu-off` | The in-game RTX Encore menu. |
| `03-load-hooks-off` | RTX Encore's watch on the game's DLL loading. |
| `04-streamline-off` | Everything that drives DLSS Frame Generation (Streamline, NVIDIA DLLs and driver). |
| `05-options-off` | UI recomposition, UI assist, HairWorks conversion and the image-quality options (settings file only). |
| `06-observer-off` | The exception log. |
| `07-all-off` | All of the above together. |

If `01-control` starts, stop there and tell us: the crash depends on something these tests do not cover.

## Part 2 — depends on Part 1

- **`02-menu-off` started:** run `M1-menu-exe-imports-off`, `M2-menu-interposer-relays-off`,
  `M3-menu-renderer-imports-off`.
- **`03-load-hooks-off` started:** run `L1-load-hooks-ansi-off`.
- **`04-streamline-off` started:** run `S1-streamline-hooks-off`, `S2-module-patches-off`, `S3-driver-hooks-off`,
  `S4-sl-arch-admission-off`.
- **`05-options-off` started:** run `O1-ui-options-off`, `O2-quality-options-off`.
- **`06-observer-off` started:** nothing more to run.
- **Several of 02 to 06 started:** run the part of each of them.
- **None of 02 to 06 started, but `07-all-off` started:** run `X1-only-menu-on`, `X2-only-load-hooks-on`,
  `X3-only-streamline-on`, `X4-only-options-on`, `X5-only-observer-on`.
- **`07-all-off` crashed too:** stop here; that result is the answer.

In the tests where the menu is left out, the RTX Encore menu does not open, and where Streamline is left out, Frame
Generation is not available. That is expected: these tests are only about whether the game starts.

## What to send back

In the issue:

1. The result of every test you ran, for example `01 crash, 02 starts, 03 crash, …, M1 crash, M2 starts, M3 crash`.
2. The whole `rtx-encore-logs` folder, zipped.

Then delete `rtx-encore.compat`, and put your own `rtx-encore.jsonc` and RTX Encore DLL back.

`BUILD.txt` names the source revision of this build, and `SHA256SUMS` the checksum of the zip.
