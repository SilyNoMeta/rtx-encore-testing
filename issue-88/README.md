# Issue 88 - The Witcher 3 NR fast-travel test

Download: [rtx-encore-issue88-nr-submission-142.zip](rtx-encore-issue88-nr-submission-142.zip)

Test version: 1.4.3+issue88-nr-submission-142
This is a diagnostic build, not a confirmed fix.

1. Close the game and back up the currently installed Encore version.dll.
2. Replace only that Encore version.dll with the version.dll from this archive, in the same folder as the DirectX 12 game executable. The archive also contains rtx-encore.dll for existing installations that use it; install only the Encore proxy you normally use. Keep the existing settings and the game's original files.
3. Start the game and check the Encore version shown in the menu.
4. Use the same save and NR settings as with the failing 1.4.3/1.4.4 build. Repeat the same fast travels at least three times and inspect the shadows.
5. Report whether flickering begins, after which trip, and whether disabling then re-enabling NR clears it. If it does, report whether it comes back after another trip.
6. Return the menu report and Hub diagnostic archive from this session, with the test version, NR preset, pass count, foveation setting and Pre-SR/Post-SR placement.

Compare with the official 1.4.3 using the same settings and route. Restore the backed-up DLL after testing. Avoid a Hub update/repair during the comparison because it may replace the test DLL.

Thanks to @Scarhead666 for the report: https://github.com/SilyNoMeta/rtx-encore/issues/88
This build has local automated validation only; no in-game result is claimed.

