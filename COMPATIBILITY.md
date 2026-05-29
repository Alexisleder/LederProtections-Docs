# LederProtections compatibility notes

## Official target for `1.0.0-beta.2`

- **Minecraft:** 1.21.x
- **Server software:** Spigot, Paper, Purpur and Pufferfish
- **Recommended server:** Paper
- **Build API base:** Spigot API 1.21.1
- **Java:** 21
- **Folia:** not supported yet

LederProtections now uses a Bukkit/Spigot-compatible base for commands, messages, GUI item names/lore and inventory titles. Paper remains the recommended production server because of its performance and ecosystem, but it is no longer a hard runtime requirement for the public build.

## Tested platforms

The `1.0.0-beta.2` compatibility build has been tested successfully on the Minecraft 1.21.x branch with:

- Spigot
- Paper
- Purpur
- Pufferfish

This means the public compatibility text may state support for **Spigot/Paper/Purpur/Pufferfish on Minecraft 1.21.x**.

## Unsupported platforms

The following platforms are not officially supported by this build:

- **Folia:** not supported yet. Folia requires explicit scheduler and region-thread compatibility work.
- **Fabric / Forge / NeoForge:** not Bukkit/Spigot plugin platforms.
- **Sponge:** different plugin API.
- **Velocity / BungeeCord / Waterfall:** proxy platforms, not world servers.
- **Mohist / Magma / Arclight:** hybrid mod/plugin servers are not officially supported because event, inventory and protection behavior can differ from standard Bukkit/Paper servers.

## Required dependencies

- WorldGuard
- WorldEdit

## Optional dependencies

- Vault
- PlaceholderAPI
- LuckPerms
- CoreProtect
- Dynmap
- BlueMap
- ItemsAdder
- Oraxen
- MythicMobs
- Citizens

Optional hooks are detected defensively and should not prevent the plugin from starting when missing, unless a feature explicitly needs that plugin.

## Public compatibility text

### English

```text
Compatible with Minecraft 1.21.x on Spigot, Paper, Purpur and Pufferfish.
Paper is recommended for production servers.
Folia is not supported yet.
Requires WorldGuard and WorldEdit. Vault and PlaceholderAPI are optional.
```

### Español

```text
Compatible con Minecraft 1.21.x en Spigot, Paper, Purpur y Pufferfish.
Paper es recomendado para servidores en producción.
Folia no está soportado todavía.
Requiere WorldGuard y WorldEdit. Vault y PlaceholderAPI son opcionales.
```

## Support command

Use this command when testing or reporting problems:

```text
/lep info
```

It reports the plugin version, platform, Java version, dependencies, loaded protection data and optional hooks.
