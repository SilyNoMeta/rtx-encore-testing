# Issue #53: experimental Smooth Motion test for RTX 20

This is **1.2.0+sm75-p4.1**, an experimental frame-generation test for
[issue #53](https://github.com/SilyNoMeta/rtx-encore/issues/53).
Unlike the earlier diagnostic, this build tries to generate frames on RTX 20.

I tested the candidate locally in Manor Lords and SurrounDead on an RTX 3070 Ti
Laptop. **It has not yet been validated on a physical RTX 20.** Performance and
image quality on RTX 20 are still unknown; this is not a stable release.

## Requirements

- An **RTX 20** card, including Super, Ti and laptop models.
- NVIDIA driver **621.01 exactly**. Other drivers are outside this test.
- A **Direct3D 12** game without anti-cheat. Select DX12 in the game if needed.

## Install

1. Download [rtx-encore-issue53-sm75test1.zip](rtx-encore-issue53-sm75test1.zip)
   using GitHub's download button, then extract it.
2. With the game closed, back up your existing RTX Encore DLL, settings and logs.
   Remove the previous diagnostic DLL from the game folder before installing this
   test. Do not run two RTX Encore proxy DLLs together or replace a game-owned DLL.
3. Copy the ZIP's files beside the game's actual executable. Use the same proxy
   name that worked for your diagnostic: rename `version.dll` to `dxgi.dll`,
   `winmm.dll` or `dinput8.dll` only if that is the name your game needs.
4. Use the included `rtx-encore.jsonc`. It already enables experimental RTX 20
   Smooth Motion and disables the old diagnostic. Do not reuse the diagnostic's
   settings. Restart the game after changing these settings.

The included Smooth Motion settings are:

```json
"smoothMotion": {
  "smoothMotionEnabled": true,
  "smoothMotionApi": "d3d12",
  "smoothMotionTuringDiagnostic": false,
  "smoothMotionTuring": true,
  "smoothMotionSm75Emulation": false,
  "smoothMotionCapture": false
}
```

## Test and report

1. Load a playable scene and play for **at least five minutes**. Move the camera,
   try an alt-tab round trip and, if supported, resize the window.
2. Report whether the picture and movement look correct, and any artifacts,
   stutter, black screen, freeze or crash. If it fails, stop and send the logs;
   repeated attempts are unnecessary.
3. If FrameView is available, record the same scene and settings for 60 seconds
   with Smooth Motion off, then restart with it on and record again. Attach both
   CSVs and state the resolution. This comparison is optional for the first test.
4. Quit normally and attach the **whole new `rtx-encore-logs` folder, zipped**,
   plus the exact `rtx-encore.jsonc` used. Give your GPU model, driver version,
   game and selected graphics API, even if the test failed.

Check that the new log reports **1.2.0+sm75-p4.1**. If it still reports
`issue53-sm75diag` or `issue53-sm75diag2`, the old DLL is still being loaded.

After testing, remove this test's files and restore your backed-up DLL/settings.
The earlier diagnostic remains available in the parent folder for reference.
`SHA256SUMS` identifies this ZIP; `BUILD.txt` identifies the tested binary.
