# Code Signing & Distribution Tools

## notarytool

Submit macOS apps for Apple notarization.

```bash
# Store credentials (one time)
xcrun notarytool store-credentials "AC_PROFILE" --apple-id you@example.com --team-id XXXXXXXXXX

# Submit for notarization
xcrun notarytool submit MyApp.zip --keychain-profile "AC_PROFILE" --wait

# Check submission status
xcrun notarytool info <submission-id> --keychain-profile "AC_PROFILE"

# View notarization log
xcrun notarytool log <submission-id> --keychain-profile "AC_PROFILE"
```

## stapler

Attach the notarization ticket to your app so it works offline.

```bash
# Staple a notarized app
xcrun stapler staple MyApp.app

# Staple a disk image
xcrun stapler staple MyApp.dmg

# Validate stapling
xcrun stapler validate MyApp.app
```

## CreateIPA

Create IPA archives for App Store submission.

```bash
xcrun CreateIPA create --archive MyApp.xcarchive --output MyApp.ipa
```

## Typical distribution workflow

```bash
# 1. Archive
xcodebuild archive -scheme MyApp -archivePath MyApp.xcarchive

# 2. Export IPA
xcodebuild -exportArchive -archivePath MyApp.xcarchive -exportPath ./export -exportOptionsPlist ExportOptions.plist

# 3. For macOS: notarize and staple
xcrun notarytool submit MyApp.zip --keychain-profile "AC_PROFILE" --wait
xcrun stapler staple MyApp.app
```
