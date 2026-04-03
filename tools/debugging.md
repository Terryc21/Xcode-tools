# Debugging & Profiling Tools

## leaks

Detect memory leaks in a running process. Instant results, no trace file.

```bash
# Check a running app by name
xcrun leaks --process MyApp

# Check by PID
xcrun leaks 12345

# Analyze a memgraph file (from Xcode's Debug Memory Graph)
xcrun leaks MyApp.memgraph

# Show full stack traces for each leak
xcrun leaks --process MyApp --fullStacks
```

**Use case:** Quick leak checks during development without opening Instruments.

## heap

Inspect what's on the heap right now.

```bash
# Show heap summary by class
xcrun heap --process MyApp

# Show all instances of a specific class
xcrun heap --process MyApp --addresses=MyViewController

# Sort by size
xcrun heap --process MyApp --sortBySize

# Analyze a memgraph
xcrun heap MyApp.memgraph
```

**Use case:** Finding what's consuming memory without recording an Instruments trace.

## vmmap

Show virtual memory map of a process.

```bash
# Summary view
xcrun vmmap --summary MyApp.memgraph

# Full memory regions
xcrun vmmap MyApp.memgraph

# Filter by region type
xcrun vmmap --pages MyApp.memgraph
```

**Use case:** Understanding memory composition (dirty, clean, swapped).

## malloc_history

Track allocation history for specific memory addresses.

```bash
# Enable malloc logging first (set MallocStackLogging=1 in scheme)
# Then query a specific address
xcrun malloc_history <pid> <address>

# Show all allocations
xcrun malloc_history <pid> -allBySize
```

**Use case:** Tracing where a leaked object was allocated.

## stringdups

Find duplicate strings wasting memory. No GUI equivalent.

```bash
# Find duplicate strings in a running process
xcrun stringdups --process MyApp

# Analyze a memgraph
xcrun stringdups MyApp.memgraph
```

**Use case:** Reducing memory footprint from repeated string allocations.

## sample

Sample a running process for CPU profiling.

```bash
# Sample for 5 seconds
xcrun sample MyApp 5

# Sample by PID
xcrun sample 12345 5 -file output.txt
```

**Use case:** Quick CPU check without Instruments.

## atos

Translate memory addresses to symbol names (symbolication).

```bash
# Symbolicate an address from a crash log
xcrun atos -o MyApp.app/MyApp -l 0x100000000 0x100001234

# Using a dSYM
xcrun atos -o MyApp.app.dSYM -l 0x100000000 0x100001234
```

**Use case:** Manual crash log symbolication.

## crashlog

Parse and symbolicate crash logs.

```bash
# Symbolicate a crash log
xcrun crashlog MyCrash.ips

# Symbolicate with verbose output
xcrun crashlog --verbose MyCrash.crash
```

**Use case:** Symbolicating TestFlight/production crash logs from terminal.

## filtercalltree

Filter and transform Instruments call tree output.

```bash
# Invert a call tree (show hottest frames first)
xcrun filtercalltree -i calltree.txt

# Charge library costs to callers
xcrun filtercalltree -chargeLibrary=UIKitCore calltree.txt
```

**Use case:** Post-processing Instruments data for specific analysis.
