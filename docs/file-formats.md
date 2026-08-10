# Minecraft Java Edition world file formats

Minecraft Java Edition stores different parts of a world in different files. Identifying the file first helps prevent editing the wrong data.

## `level.dat`

`level.dat` stores world-level metadata such as the world name, game mode, difficulty, spawn coordinates, time, game rules, and other settings. In a singleplayer save it also contains the `Player` compound for the local player.

Typical location:

```text
.minecraft/saves/<world-name>/level.dat
```

For a dedicated server, it is normally inside the configured world folder.

Open the [level.dat editor](https://nbteditor.org/level-dat-editor) or read the [level.dat editing guide](https://nbteditor.org/blog/how-to-edit-level-dat).

## Playerdata `.dat` files

Dedicated servers usually store each player's state in a UUID-named file:

```text
<world>/playerdata/<player-uuid>.dat
```

These files can contain position, dimension, health, inventory, Ender Chest contents, selected hotbar slot, and other player state. Singleplayer player data is generally inside `level.dat` under `Player`, not in the server-style `playerdata` folder.

See the [Minecraft playerdata editor](https://nbteditor.org/minecraft-playerdata-editor) and the [playerdata guide](https://nbteditor.org/blog/how-to-edit-playerdata).

## `.nbt` files

`.nbt` is the file extension commonly used for standalone Named Binary Tag data, including structure files and other Minecraft data payloads. The meaning of the tags depends on the feature or tool that created the file.

## `.mca` region files

Anvil region files use the `.mca` extension and contain a grid of chunks. A file such as `r.0.0.mca` represents a region, not a single block or entity. Editing a region file requires extra care because one file can contain many chunks.

## `.mcr` region files

`.mcr` is the older McRegion format used by earlier Java Edition versions. Treat it as legacy world data and keep a complete backup before attempting a change.

## `.schematic` files

`.schematic` is associated with older schematic workflows, especially older WorldEdit-compatible tools. Compatibility depends on the exact producer and version, so verify the exported result in a duplicate world.

## Java Edition scope

This documentation and Chunkweave are focused on Minecraft Java Edition. Do not assume that a Java Edition `.dat`, `.nbt`, or region workflow applies to Bedrock Edition.
