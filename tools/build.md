# Build & Compilation Tools

## xcodebuild

The big one. Everything Xcode's GUI does, from terminal.

```bash
# Build for simulator
xcodebuild -scheme MyApp -destination 'platform=iOS Simulator,name=iPhone 16 Pro' build

# Run tests
xcodebuild test -scheme MyApp -destination 'platform=iOS Simulator,name=iPhone 16 Pro'

# Archive for distribution
xcodebuild archive -scheme MyApp -archivePath MyApp.xcarchive

# Export IPA from archive
xcodebuild -exportArchive -archivePath MyApp.xcarchive -exportPath ./export -exportOptionsPlist ExportOptions.plist

# List schemes
xcodebuild -list

# List available destinations
xcodebuild -showdestinations -scheme MyApp

# Clean build folder
xcodebuild clean -scheme MyApp
```

## agvtool

Manage version and build numbers without clicking through Xcode.

```bash
# Get current version
xcrun agvtool what-marketing-version

# Get current build number
xcrun agvtool what-version

# Bump build number
xcrun agvtool next-version -all

# Set specific build number
xcrun agvtool new-version -all 42

# Set marketing version
xcrun agvtool new-marketing-version 2.0
```

**Use case:** CI/CD scripts that auto-increment build numbers.

## actool

Compile asset catalogs. Xcode runs this automatically, but you can use it to validate or debug.

```bash
# Compile an asset catalog
xcrun actool --compile ./build --platform iphoneos --minimum-deployment-target 17.0 Assets.xcassets

# Generate app icon set
xcrun actool --app-icon AppIcon --output-partial-info-plist ./build/assetcatalog_generated_info.plist Assets.xcassets
```

## coremlc

Compile and optimize CoreML models.

```bash
# Compile a model
xcrun coremlc compile MyModel.mlmodel ./build

# Generate Swift model class
xcrun coremlc generate MyModel.mlmodel ./Sources --language Swift
```

## momc

Compile Core Data models.

```bash
xcrun momc --sdkroot $(xcrun --show-sdk-path) MyModel.xcdatamodeld ./build/MyModel.momd
```

**Use case:** Validating Core Data models in CI without a full Xcode build.
