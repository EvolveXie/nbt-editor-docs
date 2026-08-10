# Safe Minecraft NBT editing

NBT changes are safest when every step is reversible. A file that is structurally valid can still contain a value that the game, a mod, or a server version does not expect.

## Before opening the file

1. Close Minecraft, the launcher, or the server process that may write the world.
2. Copy the entire world folder to a separate backup location.
3. Keep the original file and record the Minecraft version, modpack, or server version.
4. Work on the copy, not the live world.

## Identify the correct file

- World settings and global metadata: `level.dat`
- Singleplayer player state: `level.dat/Player`
- Dedicated-server player state: `<world>/playerdata/<uuid>.dat`
- Terrain and chunk data: `region/*.mca` or legacy `region/*.mcr`

Replacing `level.dat` will not repair a corrupted region file, and editing a server `playerdata` file will not change a singleplayer character stored in `level.dat`.

## Edit and export

Open the copy in [Chunkweave](https://nbteditor.org/), inspect the complete path to the target tag, and change only the value you understand. Download the result as a separate file. Chunkweave does not overwrite the source file selected from disk.

## Verify the result

Before replacing anything in a live save:

- Reopen the exported file and check the edited tag.
- Keep the old file as a dated backup.
- Test the edited file in a duplicate world or test server.
- Confirm that no player is online and the server is fully stopped before replacement.
- Keep a rollback copy until the world has started, saved, and restarted normally.

## Common mistakes

### Editing while the server is running

The server can write its in-memory state back to disk and erase your manual change. Stop it fully first.

### Editing the wrong player file

Server player files use UUIDs, not usernames. Check `usercache.json`, server logs, or another trusted UUID source before choosing a file.

### Deleting `level.dat_old`

Keep `level.dat_old` and all other original files until recovery has been tested on a copy.

### Changing modded data without version context

Unknown tags may be required by a mod, datapack, or custom dimension. Do not remove them just because they are unfamiliar.
