# Xcode's Hidden CLI Tools

![Visitors](https://komarev.com/ghpvc/?username=Terryc21&repo=Xcode-tools&label=visitors&color=blue) ![GitHub stars](https://img.shields.io/github/stars/Terryc21/Xcode-tools?style=flat) ![GitHub forks](https://img.shields.io/github/forks/Terryc21/Xcode-tools?style=flat)

<a href="https://buymeacoffee.com/stuffolio">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="150">
</a>

Xcode ships with **110 command-line tools** that most iOS developers never know exist. This repo documents all of them -- what they do, their Xcode GUI equivalent (if any), and real-world examples.

## How to find them on your Mac

```bash
ls "$(xcode-select -p)/usr/bin/"
```

Run any tool with `xcrun <tool>` or call it directly. No installation needed beyond Xcode.

> Based on Xcode 26.3. Tool count may vary by version.

---

## The Complete List

### Build & Compilation

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `xcodebuild` | Build, test, archive, export from CLI | Build/Test/Archive buttons |
| `actool` | Compile asset catalogs (.xcassets) | Asset Catalog editor |
| `ibtool` | Compile/lint/upgrade storyboards & XIBs | Interface Builder |
| `ibtoold` | ibtool daemon (background compilation) | Interface Builder (internal) |
| `momc` | Compile Core Data models (.xcdatamodeld) | Core Data model editor |
| `coremlc` | Compile and optimize CoreML models | CoreML model viewer |
| `intentbuilderc` | Compile App Intents definitions | Intents editor |
| `mapc` | Compile Core Data mapping models | Mapping model editor |
| `compileSceneKitShaders` | Precompile SceneKit Metal shaders | CLI only |
| `copypng` | Copy and optimize PNGs during build | Build phase (auto) |
| `copySceneKitAssets` | Copy SceneKit assets during build | Build phase (auto) |
| `iphoneos-optimize` | Convert plists to binary, optimize PNGs | Build phase (auto) |
| `ld` | Apple's linker | Build phase (auto) |
| `gcc` / `g++` | Clang C/C++/ObjC compiler | Build phase (auto) |
| `bitcode-build-tool` | Rebuild from bitcode (legacy) | CLI only |

[Detailed examples >>](tools/build.md)

### Testing & Code Quality

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `xcresulttool` | Parse .xcresult bundles as JSON | Test Report navigator |
| `xctest` | Run test bundles directly | Test navigator (Cmd+U) |
| `xctrace` | Record Instruments traces headlessly | Instruments app |
| `xccov` | Extract code coverage reports | Test Report > Coverage tab |
| `amlint` | Lint/validate asset catalogs | CLI only |

[Detailed examples >>](tools/testing.md)

### Debugging & Profiling

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `lldb` | The debugger | Debug navigator + console |
| `lldb-dap` | LLDB Debug Adapter Protocol (VS Code/editors) | CLI only |
| `leaks` | Detect memory leaks in a running process | Instruments > Leaks |
| `heap` | Inspect heap allocations | Instruments > Allocations |
| `vmmap` | Show virtual memory map | Instruments > VM Tracker |
| `malloc_history` | Track allocation history for addresses | Instruments > Allocations |
| `stringdups` | Find duplicate strings wasting memory | CLI only |
| `sample` | Sample a running process (CPU profiling) | Instruments > Time Profiler |
| `filtercalltree` | Filter/invert Instruments call tree output | Instruments call tree UI |
| `symbols` | Look up debug symbols for addresses | CLI only |
| `atos` | Translate memory addresses to symbol names | CLI only |
| `crashlog` | Symbolicate and parse crash logs | Organizer > Crashes |
| `logdump` | Dump and analyze log archives | Console.app |
| `xcdebug` | Xcode debugging utilities | CLI only |
| `xcdiagnose` | Collect diagnostic bundles for Apple support | Help > Collect Diagnostics |

[Detailed examples >>](tools/debugging.md)

### Simulator & Devices

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `simctl` | Control Simulator (boot, install, launch, screenshot) | Simulator menu bar |
| `devicectl` | Manage physical devices, install apps, capture logs | Devices & Simulators window |
| `xcdevice` | List and query connected devices | Devices & Simulators window |

[Detailed examples >>](tools/devices.md)

### Code Signing & Distribution

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `notarytool` | Submit apps for Apple notarization | Archive > Distribute |
| `stapler` | Staple notarization ticket to an app | CLI only |
| `altool` | Legacy upload/validate (deprecated) | Transporter app |
| `iTMSTransporter` | Upload to App Store Connect (now redirects to Transporter) | Transporter app |
| `xcsigningtool` | Code signing operations | Signing & Capabilities tab |
| `xarsigner` | Sign XAR archives | CLI only |
| `embeddedBinaryValidationUtility` | Validate embedded binaries | Build phase (auto) |
| `CreateIPA` | Create IPA archives for App Store | Product > Archive > Export |
| `ipatool` / `ipatool2` | Process and validate IPA files | CLI only |

[Detailed examples >>](tools/signing.md)

### Versioning & Project Management

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `agvtool` | Bump version/build numbers across a project | Target > General > Version |
| `xed` | Open files or projects in Xcode from terminal | CLI only (reverse direction) |
| `opendiff` | Launch FileMerge to diff/merge files | Source Control > FileMerge |
| `xcindex-test` | Test Xcode indexing | CLI only |

### Localization

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `genstrings` | Extract localizable strings from source | Export Localizations |
| `extractLocStrings` | Extract localized strings from binaries | CLI only |
| `xcstringstool` | Manage String Catalogs (.xcstrings) | String Catalog editor |
| `convertRichTextToAscii` | Convert rich text to ASCII | CLI only |

### Asset Processing

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `pngcrush` | Optimize PNG files (Apple's own optimizer) | CLI only |
| `TextureAtlas` | Create texture atlases for SpriteKit | SpriteKit atlas editor |
| `TextureConverter` | Convert texture formats | CLI only |
| `scntool` | Process SceneKit scene files (.scn) | SceneKit scene editor |
| `realitytool` | Process RealityKit assets (.usdz, .reality) | Reality Composer Pro |
| `referenceobjectc` | Compile ARKit reference objects | CLI only |
| `placeholderutil` | Generate placeholder app icons | CLI only |
| `ictool` | Process icon and image assets | CLI only |
| `compositeMD5` | Generate MD5 checksums for App Store assets | CLI only |

### CloudKit & Services

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `cktool` | Manage CloudKit schemas and records | CloudKit Console (web) |
| `mcpbridge` | Xcode MCP server -- lets AI tools interact with Xcode | CLI only |

### Background Assets

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `ba-package` | Package Background Assets into archives | CLI only |
| `ba-serve` | Serve dev asset packs over local network | CLI only |
| `backgroundassets-debug` | Simulate BackgroundAssets extension events | CLI only |

### Safari & Web Extensions

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `safari-web-extension-converter` | Convert browser extensions to Safari | CLI only |
| `safari-web-extension-packager` | Package Safari Web Extensions | CLI only |

### Resource Forks & Legacy

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `Rez` | Compile resource description files (.r) | CLI only |
| `DeRez` | Decompile resources back to .r format | CLI only |
| `ResMerger` | Merge resource fork files | CLI only |
| `SplitForks` | Split resource/data forks | CLI only |
| `GetFileInfo` | Get HFS file attributes | CLI only |
| `SetFile` | Set HFS file attributes | CLI only |

### Documentation

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `headerdoc2html` | Generate HTML docs from HeaderDoc comments | CLI only |
| `gatherheaderdoc` | Gather HeaderDoc output into a TOC | CLI only |
| `hdxml2manxml` | Convert HeaderDoc XML to man page XML | CLI only |
| `xml2man` | Convert XML to man pages | CLI only |

### Scripting & AppleScript

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `sdef` | Extract scripting definition from an app | CLI only |
| `sdp` | Convert scripting definitions between formats | CLI only |

### Siri & Intelligence

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `ssu-cli` | Siri/NLU development tool | CLI only |
| `ssu-cli-app` | Siri app integration testing | CLI only |
| `ssu-cli-nlu` | Siri NLU testing | CLI only |

### Gaming

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `gamepolicyctl` | Manage system game policy enforcement | CLI only |

### App Metadata

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `swinfo` | Display Swift compiler/runtime info | CLI only |
| `appleProductTypesTool` | Query Apple product type identifiers | CLI only |
| `desdp` | Extract scripting info from bundles | CLI only |
| `resolveLinks` | Resolve symbolic links | CLI only |
| `instrumentbuilder` | Build custom Instruments packages | CLI only |

### Git (Xcode-bundled)

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `git` | Version control | Source Control navigator |
| `git-receive-pack` | Git server-side receive | CLI only |
| `git-shell` | Restricted git shell | CLI only |
| `git-upload-archive` | Git archive over SSH | CLI only |
| `git-upload-pack` | Git fetch/clone server side | CLI only |
| `scalar` | Git performance optimizer for large repos | CLI only |

### Python (Xcode-bundled)

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `python3` / `python3.9` | Python interpreter | CLI only |
| `pip3` / `pip3.9` | Python package manager | CLI only |
| `pydoc3` / `pydoc3.9` | Python documentation viewer | CLI only |
| `2to3` / `2to3-3.9` | Convert Python 2 to Python 3 | CLI only |

### Build System

| Tool | What it does | GUI Equivalent |
|------|-------------|----------------|
| `make` / `gnumake` | GNU Make build tool | CLI only |

---

## How to learn more about any tool

```bash
xcrun <tool> --help     # most support this
man <tool>              # some have man pages
```

## Contributing

Found a tool I missed? Have a better description or useful example? PRs welcome.

## License

MIT
