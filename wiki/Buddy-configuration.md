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

### Close Steam Before Sleep
`default: true`

If set to `true`, the Buddy will try to close Steam before going to sleep or hibernation. Some games are able to recover after sleep, while others will just crash the OS and restart the PC. Use with caution!

### Mac Address Override
`default: ""`

If Buddy fails to select the correct MAC address, you can override it using this setting. Supported formats:
- `XX:XX:XX:XX:XX:XX`
- `XX-XX-XX-XX-XX-XX`

### Steam Exec Override
`default: ""`

Specify custom Steam executable location. Needed if running Steam from flatpak.

In case you're using flatpak:
1. Create a file that you want to use as binary.
2. Set the contents to:
```
#!/bin/sh
exec flatpak run com.valvesoftware.Steam "$@"
```
3. `chmod +x <file>`
4. Use the new file as Steam binary.

### Env Capture Regex
`default: "^(?:SUNSHINE|APOLLO).*"`

Environmental variables to be captured by `MoonDeckStream` and passed to `MoonDeckBuddy`.

They are then used when launching Steam or an app. Can be used with SpecialK for an automatic FPS limiter, however Steam must be started everytime for this to work. This can be partially achieved by configuring MoonDeck to close Steam after every sucessful stream.

For more details see https://github.com/FrogTheFrog/moondeck-buddy/pull/144.
