# Issue #53: compare the two RTX 20 Smooth Motion tests

**Test 2: 1.2.0+sm75-opt-rsrc1** is an optimized experimental candidate.
Compare it with [test 1: 1.2.0+sm75-p4.1](../sm75-test1/README.md).
Performance on a physical RTX 20 is still unknown. Neither is a stable release.

## Requirements and installation

Use an **RTX 20**, NVIDIA **621.01 exactly**, and a **DirectX 12 game without
anti-cheat**. Keep the same resolution, graphics settings and scene for all runs.
Disable the game's other frame-generation options.

1. Download [test 2 ZIP](rtx-encore-issue53-sm75test2.zip) and the
   [test 1 ZIP](../sm75-test1/rtx-encore-issue53-sm75test1.zip).
2. Close the game and back up your existing RTX Encore DLL, configuration and
   logs. Do not replace game-owned files. Keep only one RTX Encore proxy active.
3. Install one ZIP beside the actual game executable. Rename its `version.dll`
   to the same proxy name that previously worked for you, if needed.
   Use its included `rtx-encore.jsonc`; do not reuse diagnostic settings.
4. Both ZIPs use identical settings: experimental RTX 20 Smooth Motion on,
   diagnostic off, Ampere emulation off, research capture off.
   Restart the game after changing the DLL or configuration.

## Comparison and report

Use FrameView, or the RTX Encore overlay if FrameView is unavailable. Keep the
same measurement tool for every run and say which tool/counters you used.

1. Establish a baseline with `smoothMotionEnabled` set to `false` in the
   included configuration, then restart. Record the same scene for 60 seconds.
2. Set it back to `true`, restart, and test **test 1**, then **test 2** separately.
   Play each for at least five minutes and record the same 60-second scene.
   Check the version in each new log to confirm which DLL was loaded.
3. Save FrameView CSVs, or overlay screenshots and FPS readings for all three
   runs. Include average FPS and 1% low if available. If the overlay shows both
   game/base FPS and generated/displayed FPS, report both with their labels.
   A counter that does not include generated frames cannot establish their gain.
4. Describe your impressions for each build: smoothness, responsiveness, image
   quality, artifacts and stutters. Try an alt-tab round trip. If a build crashes
   or freezes, stop that test and send its logs anyway.
5. Send your GPU model, driver, game, resolution, graphics settings and API,
   measurements and impressions. Attach **separately labelled zipped logs and
   the exact configuration used for each run**, plus CSVs/screenshots. Move old
   logs somewhere safe between runs so results cannot be mixed.

After testing, restore your backed-up DLL and settings. The earlier diagnostic
and test 1 remain available. `BUILD.txt` and `SHA256SUMS` identify test 2.
