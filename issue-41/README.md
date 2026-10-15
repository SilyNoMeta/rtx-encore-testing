# Issue #41: Forza Horizon 6 closes after its startup logos

[Issue #41](https://github.com/SilyNoMeta/rtx-encore/issues/41). Your rc.1 and rc.3 logs show the same pattern each
time: the game creates its window and starts presenting, then closes about 15 to 20 seconds after launch, with no
error. DLSSG-Transfusion 1.4.5.3 runs for you and RTX Encore does not, so these tests check which part of RTX Encore
makes the difference. Three to four launches.

The build is `1.0.0-rc.3+issue33-isolate`, the same one made for a Star Wars Outlaws crash
([issue #33](https://github.com/SilyNoMeta/rtx-encore/issues/33)): rc.3 with switches that leave out, part by part,
what RTX Encore does at launch. The `README.md` inside the zip describes the Outlaws tests; **follow this page
instead**.

## What is in `rtx-encore-issue33-isolate.zip`

- `version.dll`: the test build.
- `tests\<name>\`: one folder per test, each with two files, `rtx-encore.compat` (what to leave out) and
  `rtx-encore.jsonc` (settings, the same as a fresh install). Only the tests listed below are needed.

## Before you start

1. In the game folder (beside `forzahorizon6.exe`), **move your own `rtx-encore.jsonc` and RTX Encore `dxgi.dll`
   somewhere safe**. Do not touch the game's own files, such as `sl.interposer.dll`.
2. Copy the test `version.dll` there and **rename it `dxgi.dll`**, the name you use now. Keep it for every test.
3. Delete or move the `rtx-encore-logs` folder, so that it holds only these tests.

## How to run one test

1. Copy **both files** of the test folder into the game folder, replacing those of the previous test.
2. Start the game from Steam.
3. **Wait at least 60 seconds**, even when the logos play normally: the game used to close 15 to 20 seconds after
   launch.
4. Note the result: **closes** or **starts** (still running after 60 seconds). If it starts, quit the game.

Each launch writes its own log in `rtx-encore-logs`; nothing is overwritten. The first lines of every log name the
test (`[COMPAT] rtx-encore.compat turns off: …`).

## The tests

| Order | Test folder | Before you start the game | What it checks |
| :--- | :--- | :--- | :--- |
| 1 | `01-control` | Nothing to change. | The build as it is. Should close like rc.3. |
| 2 | `02-menu-off` | Nothing to change. | The in-game RTX Encore menu left out. Frame generation should stay available in the game's own settings; the RTX Encore menu does not open. |
| 3 | `01-control` again | **Close MSI Afterburner and RivaTuner Statistics Server** completely (right-click their icons near the clock, then Exit). | Whether the RivaTuner overlay is involved. |
| 4 | `07-all-off` | Afterburner and RivaTuner can run again. **Only if test 2 closed.** | Everything RTX Encore does at launch left out. Frame generation is not available in this test; that is expected. |

If test 1 starts, still run test 2 and 3, and tell us.

## What to send back

In the issue:

1. The result of each test, for example `1 closes, 2 starts, 3 closes`.
2. The whole `rtx-encore-logs` folder, zipped.
3. If Windows recorded an error for `forzahorizon6.exe` (Win+R, `perfmon /rel`, then the red crosses at the time of
   the tests), its faulting module and exception code. Say so if there is none.

Then delete `rtx-encore.compat`, and put your own `rtx-encore.jsonc` and `dxgi.dll` back.

`BUILD.txt` names the source revision of this build, and `SHA256SUMS` the checksum of the zip.
