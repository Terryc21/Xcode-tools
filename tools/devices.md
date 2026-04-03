# Simulator & Device Tools

## simctl

Control iOS/watchOS/tvOS Simulators.

```bash
# List all simulators
xcrun simctl list devices

# Boot a simulator
xcrun simctl boot "iPhone 16 Pro"

# Take a screenshot
xcrun simctl io booted screenshot ~/Desktop/screenshot.png

# Record video
xcrun simctl io booted recordVideo ~/Desktop/recording.mp4

# Install an app
xcrun simctl install booted MyApp.app

# Launch an app
xcrun simctl launch booted com.example.myapp

# Open a URL (deep link testing)
xcrun simctl openurl booted "myapp://settings"

# Send a push notification
xcrun simctl push booted com.example.myapp notification.json

# Simulate location
xcrun simctl location booted set 37.7749,-122.4194

# Erase a simulator (factory reset)
xcrun simctl erase "iPhone 16 Pro"

# Get app container path
xcrun simctl get_app_container booted com.example.myapp data

# Set appearance (dark/light mode)
xcrun simctl ui booted appearance dark
```

**Notification payload (notification.json):**
```json
{
  "aps": {
    "alert": {
      "title": "Test",
      "body": "Hello from simctl"
    }
  }
}
```

## devicectl

Manage physical devices (replaced the old `idevice*` tools).

```bash
# List connected devices
xcrun devicectl list devices

# Install an app on device
xcrun devicectl device install app --device <udid> MyApp.app

# Launch an app
xcrun devicectl device process launch --device <udid> com.example.myapp

# Take a screenshot
xcrun devicectl device info screenshot --device <udid> --output screenshot.png

# View device logs
xcrun devicectl device info syslog --device <udid>
```

## xcdevice

Query connected devices.

```bash
# List all visible devices
xcrun xcdevice list
```

**Use case:** CI scripts that need to discover available devices.
