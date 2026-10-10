# RTX Encore test builds

Test builds for specific bug reports. They are **not releases**: a test build can be unstable, log more than usual,
or leave a feature out on purpose to narrow a problem down. Use one only when an issue asks you to; otherwise use the
releases at [SilyNoMeta/rtx-encore](https://github.com/SilyNoMeta/rtx-encore/releases).

## Builds

| Folder | For | Builds |
| :--- | :--- | :--- |
| [`issue-17`](issue-17) | [Cyberpunk startup crash](https://github.com/SilyNoMeta/rtx-encore/issues/17) | `issues14-17-reflex-r1`, automatic detailed diagnostics |
| [`issue-14`](issue-14) | [Cyberpunk startup / separate NR report](https://github.com/SilyNoMeta/rtx-encore/issues/14) | Same Reflex startup candidate; Witcher 3 NR error remains open |
| [`issue-13`](issue-13) | [Starfield crash when turning Frame Generation on](https://github.com/SilyNoMeta/rtx-encore/issues/13) | `diagnostics`, `no-menu` |

## Installing a test build

1. Keep a copy of the RTX Encore file you use now, to put it back afterwards.
2. Open the build's `.zip` here on GitHub and use **Download raw file** (the download button at the top right of the
   file).
3. Extract it outside the game folder and follow the issue-specific instructions. Keep only one RTX Encore proxy installed.
4. Start the game. The first lines of `rtx-encore-logs\rtx-encore.log` (or `rtx-encore-<number>.log`) show the test
   build's version, for example `1.0.0-beta.2+issue13-no-menu`.
5. Send back the whole `rtx-encore-logs` folder from that session, as the issue's folder asks.
