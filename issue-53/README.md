**New comparison test:** [test 2, 1.2.0+sm75-opt-rsrc1](sm75-test2/README.md).
Please compare it with [test 1, 1.2.0+sm75-p4.1](sm75-test1/README.md)
and report performance and your impressions using the comparison instructions.

**First frame-generation test:** [experimental RTX 20 Smooth Motion, 1.2.0+sm75-p4.1](sm75-test1/README.md).
That test attempts frame generation. The earlier driver-only diagnostic below is
retained for reference; use the comparison instructions above for a new report.

# Issue #53: Smooth Motion on RTX 20, driver diagnostic

[Issue #53](https://github.com/SilyNoMeta/rtx-encore/issues/53). Before trying to port NVIDIA's Smooth Motion to
RTX 20 cards, I need to know whether the NVIDIA driver itself gets far enough on an RTX 20. This build checks only
that. **It does not generate frames**: no extra FPS is expected. One launch of one game is enough.

The build is `1.2.0+issue53-sm75diag2`. It is RTX Encore 1.2.0 plus this diagnostic, which stays off unless you turn
it on below.

This corrects a bug in the first diagnostic build, which could ignore the diagnostic setting at startup.
If you tested the earlier build, please replace it and repeat the test. Those earlier logs do not decide whether
Smooth Motion can run on RTX 20. The included settings already enable the diagnostic.

## What you need

- An **RTX 20** card (2060, 2070, 2080, Super or Ti, or a laptop version).
- The NVIDIA **621.01** driver exactly. With any other driver the test is refused and tells nothing.
  You can check the version in the NVIDIA app or in Device Manager.
- A **Direct3D 12** game **without anti-cheat**. Any such game is fine; tell me which one you used.

## What is in `rtx-encore-issue53-sm75diag.zip`

- `version.dll`: the test build.
- `rtx-encore.jsonc`: the settings for this test (a fresh install with the test turned on).

## Before you start

1. In the game folder (beside the game's `.exe`), **move your own `rtx-encore.jsonc` and RTX Encore DLL somewhere
   safe**, if you have them. Do not touch the game's own files.
2. Copy both files of the zip there. If the game needs another name than `version.dll` with RTX Encore (`dxgi.dll`,
   `winmm.dll`, `dinput8.dll`), rename `version.dll` to that name.
3. Delete or move the `rtx-encore-logs` folder, so that it holds only this test.

The `rtx-encore.jsonc` of the zip already has, in its `smoothMotion` section:

```jsonc
"smoothMotionEnabled": true,
"smoothMotionApi": "d3d12",
"smoothMotionTuringDiagnostic": true
```

## The test

1. Start the game and load into gameplay (not just the menu).
2. Stay in game for **about one minute**, moving the camera a little.
3. Quit the game normally.

Any outcome is useful, including a crash, a black screen or a freeze: that is part of what the test measures.
If the game crashes or freezes, just close it (Task Manager if needed) and send the log anyway.

## What to send back

In the issue:

1. Your card model and the game you used.
2. What happened: the game ran normally, stuttered, showed a black screen, froze or crashed (and when).
3. The whole `rtx-encore-logs` folder, zipped, and the `rtx-encore.jsonc` used for the test.

The new log should begin with version `1.2.0+issue53-sm75diag2`. If it still shows the older version,
check that the old RTX Encore DLL was replaced in the correct game folder.

Then delete the test files and put your own `rtx-encore.jsonc` and DLL back.

`BUILD.txt` names the source revision of this build, and `SHA256SUMS` the checksum of the zip.
