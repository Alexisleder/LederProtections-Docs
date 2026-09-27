# LederProtections

A configurable protection-stone plugin for Minecraft servers. LederProtections uses WorldGuard regions and adds player-friendly protection management, configurable access rules, roles, GUIs, optional economy features, holograms, diagnostics, and migration tools.

**Current release:** 1.4.1
**Supported server families:** Spigot, Paper, Purpur, and compatible Bukkit forks
**Recommended:** Paper (where a supported build is available)

[Download on Modrinth](https://modrinth.com/plugin/lederprotections) · [Documentation Wiki](https://github.com/Alexisleder/LederProtections-Docs/wiki) · [Report a documentation issue](https://github.com/Alexisleder/LederProtections-Docs/issues)

## Features

- Configurable protection stones, region sizes, roles, and protection limits.
- Protection management GUI, administrative browser, and searchable public protection directory.
- Fine-grained protection rules and boundary safeguards.
- Optional shop, upgrades, and economy integration through Vault.
- Configurable per-protection and global holograms, including placeholders.
- PlaceholderAPI expansion and integrations with compatible plugins.
- Safe teleportation, visual borders, diagnostics, and update notifications.
- ProtectionStones migration and LederProtections data export/import tools.
- Public Java API for add-on developers: [LederAPI](https://github.com/Alexisleder/LederAPI).

## Compatibility and requirements

| Minecraft | Java | Notes |
|---|---:|---|
| 1.21.x | 21 | Use matching WorldEdit and WorldGuard builds. |
| 26.x | 25 | Use builds compatible with your exact server version. |

WorldEdit and WorldGuard are required. Paper is recommended; Spigot and compatible forks are supported for the listed game versions. Folia is not currently supported. Check the [Modrinth version list](https://modrinth.com/plugin/lederprotections/versions) for the exact game versions supported by each release.

Optional integrations:

- **Vault** plus a compatible economy plugin for paid features.
- **PlaceholderAPI** for external placeholders in supported displays and integrations.

## Installation

1. Stop the server and install compatible builds of WorldEdit and WorldGuard.
2. Download the LederProtections release for your Minecraft version from [Modrinth](https://modrinth.com/plugin/lederprotections).
3. Put the plugin JAR in the server's `plugins` folder and start the server.
4. Review `plugins/LederProtections/config.yml` and `stones.yml`.
5. Check the installation with `/lep version` and `/lep check`.

For detailed setup, see the [Installation](https://github.com/Alexisleder/LederProtections-Docs/wiki/Installation) and [Dependencies](https://github.com/Alexisleder/LederProtections-Docs/wiki/Dependencies) pages.

## Useful commands

| Command | Purpose |
|---|---|
| `/p` | Open your protection menu. |
| `/warps` | Browse public protections. |
| `/lep admin` | Open the administrative protection browser. |
| `/lep hooks` | Inspect detected integrations. |
| `/lep check` | Run diagnostics. |
| `/lep reload` | Reload supported configuration. |
| `/lep version` | Show plugin version information. |

Commands and permissions can vary by configuration and release; see the [Commands](https://github.com/Alexisleder/LederProtections-Docs/wiki/Commands) and [Permissions](https://github.com/Alexisleder/LederProtections-Docs/wiki/Permissions) pages.

## API for add-on developers

LederAPI is a separate public API contract for integrations; it does not make the LederProtections plugin source code public. See the [LederAPI repository](https://github.com/Alexisleder/LederAPI) and its [wiki](https://github.com/Alexisleder/LederAPI/wiki) for setup, examples, and compatibility details.

## Metrics and privacy

LederProtections uses bStats for aggregated server-level plugin statistics. It does not collect player names, UUIDs, protection contents, or chat. Server administrators can disable bStats for all plugins in `plugins/bStats/config.yml` by setting `enabled: false`.

## Documentation and support

The [wiki](https://github.com/Alexisleder/LederProtections-Docs/wiki) is the source for detailed installation, configuration, commands, compatibility, integrations, migration, and troubleshooting guidance.

When reporting a problem, include the LederProtections version (`/lep version`), server software and Minecraft version, WorldEdit/WorldGuard versions, relevant integration versions, and the related console error. Please do not attach server credentials or private player data.

- [Compatibility](https://github.com/Alexisleder/LederProtections-Docs/wiki/Compatibility)
- [Configuration](https://github.com/Alexisleder/LederProtections-Docs/wiki/Configuration)
- [PlaceholderAPI](https://github.com/Alexisleder/LederProtections-Docs/wiki/PlaceholderAPI)
- [Holograms](https://github.com/Alexisleder/LederProtections-Docs/wiki/Holograms)
- [Migration tools](https://github.com/Alexisleder/LederProtections-Docs/wiki/Migration-Tools)
- [Diagnostics](https://github.com/Alexisleder/LederProtections-Docs/wiki/Diagnostics)
- [FAQ](https://github.com/Alexisleder/LederProtections-Docs/wiki/FAQ)
- [Changelog](https://github.com/Alexisleder/LederProtections-Docs/wiki/Changelog)
