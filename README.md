# RTX Encore test builds

Test builds for specific bug reports. They are **not releases**: a test build can be unstable, log more than usual,
or leave a feature out on purpose to narrow a problem down. Use one only when an issue asks you to; otherwise use the
releases at [SilyNoMeta/rtx-encore](https://github.com/SilyNoMeta/rtx-encore/releases).

## Builds

| Folder | For | Builds |
| :--- | :--- | :--- |
| [`issue-13`](issue-13) | [Starfield crash when turning Frame Generation on](https://github.com/SilyNoMeta/rtx-encore/issues/13) | `diagnostics`, `no-menu` |
| [`issue-33`](issue-33) | [Star Wars Outlaws crashes on launch](https://github.com/SilyNoMeta/rtx-encore/issues/33) | `isolate` (22 test configurations, one round) |
| [`issue-33-trace`](issue-33-trace) | [Star Wars Outlaws crashes on launch](https://github.com/SilyNoMeta/rtx-encore/issues/33) | `trace` (3 test configurations) |
| [`issue-41`](issue-41) | [Forza Horizon 6 closes after its startup logos](https://github.com/SilyNoMeta/rtx-encore/issues/41) | `isolate` from issue 33 (3 to 4 launches) |

## Installing a test build

1. Keep a copy of the RTX Encore file you use now, to put it back afterwards.
2. Open the build's `.zip` here on GitHub and use **Download raw file** (the download button at the top right of the
   file).
3. Extract it. Each zip holds `rtx-encore.dll` and `version.dll`: use the one you normally use, under the same name.
4. Start the game. The first lines of `rtx-encore-logs\rtx-encore.log` (or `rtx-encore-<number>.log`) show the test
   build's version, for example `1.0.0-beta.2+issue13-no-menu`.
5. Send back the whole `rtx-encore-logs` folder from that session, as the issue's folder asks.
