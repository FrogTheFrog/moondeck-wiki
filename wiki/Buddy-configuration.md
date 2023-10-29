## Overview

Everytime the app is started, a configuration file called `settings.json` is read or created. After modifying the file, the app must be restarted for changes to apply.

On Windows the configuration file is located next to the executable.

On Linux the configuration file is located in `$XDG_CONFIG_HOME/moondeckbuddy` or `~/.config/moondeckbuddy`.

## Settings

### Port
`default: 59999`

The port to be opened by the app for communication.

### Logging rules
`default: ""`

Can be used to enable/disable logging for various categories.

By default, Buddy logs information that is of severity **INFO** or above. To enable Buddy's debug logs, set the parameter value to `"buddy.*.debug=true"`.

### Handled displays
`default: []`

#### Windows

By default, Buddy will change resolution for display(-s) that is marked as primary.

Here you can override this choice, with a list of display names that you want to change resolution for instead.

#### Linux (X11)

By default, Buddy will change resolution for the **default** screen of the **default** display.

Here you can override the screen choice, with a list of screen names that you want to change resolution for instead.

Note: in the Buddy's configuration the screen is referred to as a display due to different concepts between X11 and Windows. Buddy will always work with the default display from the environment.

#### Linux (Wayland)

Resolution change not supported yet as the [API](https://wayland.app/protocols/wlr-output-management-unstable-v1) is not mature enough and the compositor support is lacking.

##### Finding the display names

You can enable the debug mode to check what displays are available as they are printed when trying to change resolution.

### Sunshine apps filepath
`default: ""`

Specifies where to find the `apps.json` file from Sunshine.

If the value is left empty (default):
* on Windows the registry will be checked for possible Sunshine installation directory;
* on Linux the default config location is used as a fallback (`$XDG_CONFIG_HOME/sunshine` or `~/.config/sunshine`).

### Prefer hibernation
`default: false`

If set to `true`, the Buddy will try to put the PC into hibernation mode if it is available. Otherwise it will try to suspend the PC as usual.

### Ssl Protocol
`default: "SecureProtocols"`

Allows to set the SSL protocol that is used by Buddy server. Some systems have problems when using the latest TLS version, so with this option one can downgrade the version.

Possible values:
- `SecureProtocols` - whatever the Qt Framework deems as secure;
- `TlsV1_2`;
- `TlsV1_2OrLater`;
- `TlsV1_3`;
- `TlsV1_3OrLater`.

### Force Big Picture
`default: true`

If set to `true`, the Buddy will try open Steam in Big Picture mode before launching the game.
If set to `false`, it is up to the user to ensure that the game is launched in time (by clliking on launcher or by other means) before MoonDeck times out!

### Close Steam Before Sleep
`default: true`

If set to `true`, the Buddy will try to close Steam before going to sleep or hibernation. Some games are able to recover after sleep, while others will just crash the OS and restart the PC. Use with caution!

### [LINUX ONLY] Registry file override
`default: ""`

Specify custom `registry.vdf` location. Needed if running Steam from flatpak.

Example location: `/home/frog/.var/app/com.valvesoftware.Steam/.steam/registry.vdf`.

### [LINUX ONLY] Steam binary override
`default: ""`

Specify custom Steam binary location. Needed if running Steam from flatpak.

In case you're using flatpak:
1. Create a file that you want to use as binary.
2. Set the contents to:
```
#!/bin/sh
exec flatpak run com.valvesoftware.Steam "$@"
```
3. `chmod +x <file>`
4. Use the new file as Steam binary. 
