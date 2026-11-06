# RTX Encore XeFG test build

Version: **2.0.1+xefg-provider-present** (experimental).

I fixed XeFG startup stalls, black screens and overlay/menu problems, including an FPS counter that could report half the expected rate. The SHARPENING status is now uppercase.

## Install

Close the game. Back up your existing RTX Encore `dxgi.dll`, then replace it with the `dxgi.dll` from the ZIP. This package is for installations that load RTX Encore as `dxgi.dll`; do not add a second RTX Encore proxy alongside `version.dll`, `winmm.dll` or another existing Encore DLL. Keep your current configuration and runtimes. This ZIP contains only the test proxy and third-party notices.

## Test

- Enable XeFG and check startup, loading and normal gameplay.
- Press Insert and check that the RTX Encore menu opens.
- Compare the FPS counter with FrameView if available, and check that the status text is readable.
- If you normally use Steam's overlay or RTSS, check their usual toggle shortcuts.

Please return the game name, GPU, driver, graphics API, settings, result, and the latest session log from `rtx-encore-logs`. Include a screenshot or crash log if a problem occurs. Review logs for personal paths before sharing them.

## Validation and limits

The Release DLL builds successfully and nine focused CPU tests pass. Black Flag gameplay worked with the preceding iteration; the final menu and FPS changes still need tester confirmation. The Forza RTSS crash could no longer be reproduced with a diagnostic build; it is not claimed fixed. This is not the 2.0.2 release.