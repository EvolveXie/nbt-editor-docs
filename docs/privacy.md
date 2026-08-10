# Privacy and local processing

Chunkweave is designed around browser-local file processing for its current NBT editing workflow.

When you select a supported Minecraft Java Edition file, the file is parsed and rebuilt in your browser. The file contents are not uploaded to Chunkweave for editing, and the editor exports a separate copy for download.

This model is useful for world files that contain private builds, server data, player inventories, coordinates, or other information that should not be sent to an online file-processing service.

Local processing does not remove the need for backups. A browser-local editor can preserve file boundaries and types, but it cannot guarantee that every value is valid for a particular Minecraft version, mod, datapack, or server configuration.

See the [safe editing checklist](safe-editing.md) before replacing a file in a world or server.
