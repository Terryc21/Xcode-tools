# Testing & Code Quality Tools

## xcresulttool

Parse `.xcresult` bundles -- the structured output from `xcodebuild test`.

```bash
# Get test summary as JSON
xcrun xcresulttool get test-results summary --path MyTests.xcresult

# Get detailed test results
xcrun xcresulttool get test-results tests --path MyTests.xcresult

# Export attachments (screenshots, logs)
xcrun xcresulttool export --path MyTests.xcresult --output-path ./exports --type file --id <attachment-id>
```

**Use case:** CI dashboards, automated test reporting, extracting failure screenshots.

## xctrace

Run Instruments profiles from terminal. No GUI needed.

```bash
# Record a Time Profiler trace
xcrun xctrace record --template "Time Profiler" --launch -- MyApp.app

# Record with a time limit
xcrun xctrace record --template "Allocations" --time-limit 30s --attach <pid>

# List available templates
xcrun xctrace list templates

# List available devices
xcrun xctrace list devices
```

**Use case:** CI performance regression testing, automated profiling.

## xccov

Extract code coverage without opening Xcode.

```bash
# View coverage report
xcrun xccov view --report MyTests.xcresult

# View coverage for a specific file
xcrun xccov view --file Sources/MyFile.swift MyTests.xcresult

# Export as JSON
xcrun xccov view --report --json MyTests.xcresult

# Get overall coverage percentage
xcrun xccov view --report MyTests.xcresult | head -1
```

**Use case:** CI coverage gates, tracking coverage over time.

## xctest

Run test bundles directly without xcodebuild.

```bash
# Run a specific test bundle
xcrun xctest <path-to-test-bundle.xctest>
```

**Use case:** Running tests in minimal environments.

## amlint

Validate asset catalogs for issues.

```bash
xcrun amlint <path-to-asset-catalog.xcassets>
```

**Use case:** CI validation of asset catalogs before build.
