# Nightfall Client

Client-side Fabric mod project targeting Minecraft Java **1.21.11** and **Java 21**.

## Current contents

- Purple Nightfall ClickGUI with module cards, keybinds, settings, and HUD.
- Player, entity, storage, and spawner ESP for data already present on the client.
- OG Base Finder and Chunk Explorer based on loaded chunks only. The score is an analysis score, **not** a probability.
- Selectable GUI click sounds (Soft, Mechanical, Digital, Minimal) and volume setting under **Misc → GUI Sounds**.
- Shared false-positive filter for spawners at the four chunk corners near the bottom of the world. It is enabled by default under **Base Finding → OG Base Finder → Ignore Bedrock Corner Spawners**. The vertical tolerance is configurable with **Decoy Y Range**.

## Fake-spawner filter

The filter matches a spawner block entity when both local chunk coordinates are on a corner (`x = 0 or 15` and `z = 0 or 15`) and its Y coordinate is no higher than `world minimum Y + Decoy Y Range`. The default tolerance is 4 blocks. The same shared rule is used by chunk analysis and Spawner ESP, so a matched spawner is not used as evidence and is not drawn by Spawner ESP.

This is a configurable heuristic based on client-visible block-entity data. It cannot identify every server-specific visual decoy, and it cannot inspect server-hidden blocks or data. The ESP and analyzer only work with chunks and block entities the client has received.

## Build

Requirements: JDK 21 and a Gradle installation compatible with the Fabric Loom plugin specified in `build.gradle`. From this directory run:

```sh
gradle --no-daemon clean build
```

On Windows, run `build.bat`. The resulting mod JAR is written to `build/libs/`.

## Important status note

The source ZIP was updated, but a Gradle build could not be run in the current environment because Gradle is not installed and external downloads are unavailable. The project has **not** been represented as compile-tested.
