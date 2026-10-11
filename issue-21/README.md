# Issue #21 — Starfield exit and Reflex frame-limit test

For [issue #21](https://github.com/SilyNoMeta/rtx-encore/issues/21).
Thanks to **Avictuu** for the multiplier tests and shutdown logs.

**Test version:** `1.0.0-beta.3+issue21-reflex-r1`, with Open NR enabled.
This package combines a candidate fix for the shutdown exception, extended Reflex frame-limit compatibility,
and the **Suggested source cap** button. It is a diagnostic test build, not an official release.
Windows compilation and all **22 automated tests passed**, including discovery and unloading of the official Reflex 2.12 DLL.
In-game validation is pending.

[Download the ZIP](RTX-Encore-issue21-reflex-r1.zip?raw=true) · [SHA-256](SHA256SUMS) · [Build identity](BUILD.txt)

## Install

1. Close Starfield and back up your current RTX Encore proxy DLL and `rtx-encore.jsonc`.
2. Keep the **Streamline 2.12 and `nvngx_dlssg.dll` files that already enabled 3x–6x** for this comparison.
   Do not change NVIDIA DLLs, the driver, mods, OTA settings or caches during this test.
3. Extract the ZIP outside the game directory. Rename its `rtx-encore.dll` to your existing Encore proxy name
   (`dxgi.dll` in the supplied log) and replace that one file. Keep only one Encore proxy installed.
4. Copy **`rtx-encore.diagnostics`** next to the proxy, with that exact filename and no extra `.txt`.
   Keep your current configuration; this ZIP does not include a replacement configuration.
5. Start the game normally. The log should show `1.0.0-beta.3+issue21-reflex-r1` and
   `[DIAGNOSTICS] support profile=verbose`.

## One short session

Keep Frame Generation in a **fixed** mode, such as 3x or 4x, in a playable scene.

1. In **Frames → Frame pacing**, start with **Render-frame limit → Game** and observe the source/rendered FPS.
2. Choose a manual cap clearly below those source FPS (for example **40** if the scene renders above 50).
   Wait about 15 seconds and note whether the rendered FPS settle near the requested limit.
3. Try **Suggested source cap → Apply** if available, wait about 15 seconds, then return to **Game**
   and check that the manual cap is released. If the suggestion is unavailable, just report the reason shown.
4. Exit normally. Check whether `Starfield.exe` disappears from Task Manager without being ended manually.
   Please mention any regression in the working MFG multipliers or any new symptom.

The cap applies to **source/rendered frames**, not the displayed total after Frame Generation.
The suggestion is `(display Hz - 3) / observed multiplier`, rounded down: 240 Hz at 3x gives 79 source FPS.
If that is above the FPS the scene can produce, no slowdown is expected from applying it.
**accepted** means Reflex accepted an options call; the measured FPS are the actual check.
**Game** restores the game's own Reflex settings, which may include its own cap.

The suggestion is deliberately unavailable in Dynamic mode, with Smooth Motion, or when current display/FG data
is missing or stale. It never adjusts the cap automatically. No CPU-wait fallback or forced Reflex mode is added.

## Send back

Attach one ZIP containing the **complete `rtx-encore-logs` folder from this session** and your active
**`rtx-encore.jsonc`**. Include `sl.log` if Streamline creates one elsewhere. Keep the files separate and intact;
the game and any error reporter can have different PID/session logs. Send the logs even if everything works.

In a few words, tell us whether the manual cap worked, whether the suggestion applied, and whether the game
exited cleanly. If it hangs, mention that before ending the process; a new dump is not requested for this first test.
If files are locked, copy them into another directory and ZIP the copies.

Detailed logs include loaded versions/paths, system and driver context, Reflex discovery and lifetime,
requested/applied/restored intervals, graphics events, NR/HUD/motion diagnostics and performance/GPU samples.
Frequent events are sampled or bounded. This package is for diagnosis, not precise FPS/latency benchmarking.
It does not change NVIDIA's OTA policy, your chosen rendering settings or hardware settings.

## Compatibility and validation

The limiter admits the public Reflex API family from **2.10 through 2.14.1**. The published NVIDIA sources
for 2.10.0, 2.10.3, 2.11.1, 2.12.0 and 2.14.1 were checked. There is no public 2.13 SDK in the repository;
its intermediate version has synthetic contract-test coverage, not verification on an official 2.13 DLL.
Actual support still depends on the game's integration and the driver.

`BUILD.txt` records the exact compiled revision and automated validation. Automated tests do not run Starfield
or establish that this final build fixes its shutdown symptom. The earlier 3x–6x success was reported with beta.3
and the updated NVIDIA files; it is not a completed in-game test of this package.

## Restore

Restore your backed-up proxy and remove `rtx-encore.diagnostics`. Restore the backed-up configuration if you
changed/saved settings during the test. Retain the logs until the issue is resolved.
