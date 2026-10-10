# Issue #17 — Cyberpunk startup / Reflex test

For [issue #17](https://github.com/SilyNoMeta/rtx-encore/issues/17).
Thanks to **naruto490610-alt** and **wisecase2** for the reports and logs.
wisecase2 reported that the crash stayed gone after restoring the original cache and removing the OTA variables;
no further cache manipulation is requested. A tester who still reproduces the crash can provide the stronger comparison.

**Test version:** `1.0.0-beta.3+issues14-17-reflex-r1`. Same binary for both reports.
**Purpose:** test a candidate fix for Cyberpunk 2077 startup crashes involving Reflex.
Windows CI and all 12 automated tests passed. In-game confirmation is pending.
This is a diagnostic test package, not a new official release.

[Download the ZIP](RTX-Encore-issues14-17-reflex-r1.zip?raw=true) · [SHA-256](SHA256SUMS) · [Build identity](BUILD.txt)

## Install

1. Close the game and keep a backup of your current RTX Encore proxy DLL and `rtx-encore.jsonc`.
2. Extract the ZIP **outside the game folder**. Rename its `rtx-encore.dll` to the name of
   your existing RTX Encore proxy, for example `VERSION.dll`, and replace that one file.
   Keep exactly one RTX Encore proxy installed. Do not replace any NVIDIA `sl.*` or `nvngx_*` DLL.
3. Copy the included **`rtx-encore.diagnostics`** file next to that proxy DLL. Keep its exact name
   (no extra `.txt`). This activates detailed logs automatically, including before startup finishes.
   Keep your existing configuration; no replacement configuration is supplied.
4. Start the game normally. The session log should show `1.0.0-beta.3+issues14-17-reflex-r1` and
   `[DIAGNOSTICS] support profile=verbose`. The profile applies only when the small file is present
   when the game starts.

## One short test

- Keep your current NVIDIA DLLs, driver, mods, settings and OTA/cache state unchanged for this comparison.
- Start Cyberpunk once. Report whether it reaches the menu and loads a save. If it does, play for about
  one minute and switch Frame Generation off/on once if that option is available. Report any new symptom.
- Tell us whether the previous build **still failed immediately before this test**, or whether the problem
  had already disappeared. Also mention any OTA/cache workaround still in effect.
- Exit normally when possible. If startup hangs and you must end the game process, mention that.

There is no need to delete NVIDIA's model cache, change global environment variables, or run a large test matrix.
If your original crash no longer reproduces, a successful launch is useful stability feedback but does not by itself
confirm the cause or the fix.

## Send back

Attach one ZIP containing the **complete `rtx-encore-logs` folder from that launch** and your active
`rtx-encore.jsonc`. Keep the individual files intact: the game and its error reporter have separate logs,
including `rtx-encore-<pid>.log` and PID/session-specific `.crash.log` files. Include `sl.log` if Streamline
created one elsewhere. Please do not merge the logs into one text file.

Send the logs even if the test succeeds: they show which Reflex DLL and initialization sequence were actually used.
If Windows says a log is still in use, copy the files into a separate temporary folder and ZIP the copies;
mention any game/error-reporter/updater processes left running.

The package records loaded component versions and paths, system/driver context, preset hints, Streamline and
Reflex lifecycle details, graphics operations, NR/HUD/motion diagnostics, and performance/GPU samples.
Repeated hot-path events are sampled or bounded; this build is intended for diagnosis, not FPS benchmarking.
It does not force OTA, NR, a Reflex cap or a DLSS preset. GPU profiling follows your existing setting.

## Restore

Put your backed-up proxy DLL back and remove `rtx-encore.diagnostics`. Restore your backed-up configuration
if you changed or saved settings during the test. Keep the captured logs until the report is resolved.
