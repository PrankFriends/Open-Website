# Scheduled URL Opener (macOS)

Opens a URL in Safari every 24 hours using `launchd`. Persists across reboots.

## Install

1. Create the plist:

```bash
cat > ~/Library/LaunchAgents/com.user.openurl.plist << 'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.user.openurl</string>
    <key>ProgramArguments</key>
    <array>
        <string>open</string>
        <string>-a</string>
        <string>Safari</string>
        <string>https://www.pornhub.com</string>
    </array>
    <key>StartInterval</key>
    <integer>86400</integer>
</dict>
</plist>
EOF
```

2. Load it:

```bash
launchctl load ~/Library/LaunchAgents/com.user.openurl.plist
```

## Uninstall

```bash
launchctl unload ~/Library/LaunchAgents/com.user.openurl.plist
rm ~/Library/LaunchAgents/com.user.openurl.plist
```

## Customize

- **URL** — change the `<string>` after `Safari`
- **Interval** — change `86400` (seconds). E.g. `3600` = 1 hour
