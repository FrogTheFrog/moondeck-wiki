## General

All you have to do is to add a new app with the following:

* "**Application Name**" field set as **MoonDeckStream** (default). You can also customize which application name to use in MoonDeck settings in case you would like to have specialized "do/undo" logic.
* "**Command**" field set to the `MoonDeckStream` executable, using the installation folder created during Moondeck Buddy's setup.
  * On Windows, the default should be `<BuddyInstallDirectory>\bin\MoonDeckStream.exe` (replace `<BuddyInstallDirectory>` with the file path of where it is installed).
  * On Linux, it depends on the earlier setup, but it can be as simple as `/home/frog/Downloads/MoonDeckBuddy.AppImage --exec MoonDeckStream`.
* "**Continue streaming...**" - just disable both checkboxes.
* "**Exit Timeout**" - When you close the game on the host PC (via in-game menu or otherwise), Sunshine will wait a few seconds before ending the stream and running any "Undo" commands you may have setup. This field adjusts how long Sunshine will wait.
  * Note, if you close MoonDeck before this timer is up (via L1+R1+Select+Start or choosing "Exit Game" in the Steam menu), **Sunshine will merely pause the stream instead of ending it**. This means any Undo commands will not run, and your display resolution may not revert. In such scenarios, simply open Moonlight on your Steam Deck and stop the stream. You can also restart Sunshine on the host PC.

Bellow an example of the required settings using a non-standard installation path:

![image](images/sunshine-example.png)

## [Windows + Nvidia GPU] Toggle G-Sync

Sometimes there might be some strange behaviour caused by G-Sync:
- FPS locked to 58 FPS instead of 60;
- frame instability (not stuttering, but just does not feel "right").

If you notice such issues, you can toggle the G-Sync using this command line [tool](https://github.com/FrogTheFrog/gsync-toggle).

## [Windows + Nvidia GPU] Toggle Frame Rate Limiter

If you're using the Nvidia's built-in frame limiter, you can use this command line [tool](https://github.com/FrogTheFrog/frl-toggle) change it while streaming.
