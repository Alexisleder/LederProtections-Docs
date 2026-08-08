Outdated Wiki, 1.2.0

# LederProtections

**LederProtections** is a modern protection-stone plugin for Minecraft servers.

It lets players protect their bases by placing configurable protection stones, using **WorldGuard** and **WorldEdit** as the region backend while adding its own rule engine, GUIs, roles, upgrades, economy support, anti-exploit checks and migration tools.

---

## Version

| Version | Status |
|---|---|
| `v1.1.0` | Stable feature release |

`v1.1.0` adds **Migration Tools**, including ProtectionStones migration and native LederProtections export/import.

---

## Features

- Protection stones with configurable sizes.
- WorldGuard-backed protection regions.
- Internal protection rule engine.
- Personal protection GUI with `/p`.
- Dedicated admin protection browser with `/lep admin`.
- Owner, co-owner and member roles.
- Protection transfer support.
- Protection upgrades.
- Optional shop and economy support through Vault.
- Protection teleport support.
- Visual protection borders.
- PlaceholderAPI support.
- Modrinth update checker.
- Runtime diagnostics.
- ProtectionStones migration tools.
- Native LederProtections export/import tools.
- Anti-exploit protection for common bypass methods.

---

## Compatibility

| Platform | Status |
|---|---|
| Spigot 1.21.x | Supported |
| Paper 1.21.x | Supported and recommended |
| Purpur 1.21.x | Supported |
| Pufferfish 1.21.x | Supported |
| Paper 26.1.x | Tested |
| Spigot 26.2 | Tested |

Paper is recommended for production servers.

---

## Requirements

| Dependency | Required | Description |
|---|---:|---|
| Java 21+ | Yes | Required to run the plugin. |
| WorldEdit | Yes | Required by WorldGuard and region operations. |
| WorldGuard | Yes | Region backend for protections. |
| Vault | No | Required only for economy/shop/paid features. |
| PlaceholderAPI | No | Required only for placeholders. |

For Minecraft 26.x servers, use the Java version required by that server version and compatible WorldGuard/WorldEdit builds.

---

## Installation

1. Stop your server.
2. Install **WorldEdit**.
3. Install **WorldGuard**.
4. Place `LederProtections.jar` in your `plugins` folder.
5. Start the server.
6. Check the console for startup messages.
7. Run:

```text
/lep version
/lep check
```

8. Configure `config.yml` and `stones.yml`.
9. Set permissions with your permissions plugin.
10. Test placing a protection stone.

---

## Main Commands

| Command | Description |
|---|---|
| `/p` | Opens the personal protection GUI. |
| `/protections` | Alias for the personal protection GUI. |
| `/protecciones` | Spanish alias for the personal protection GUI. |
| `/p border` | Shows a visual border preview. |
| `/lep admin` | Opens the admin protection browser. |
| `/lep shop` | Opens the protection shop. |
| `/lep give <player> <radius> <amount>` | Gives protection stones. |
| `/lep check` | Runs protection diagnostics. |
| `/lep version` | Shows plugin version and update-checker status. |
| `/lep info` | Shows runtime/plugin information. |
| `/lep status` | Shows plugin/server status. |
| `/lep reload` | Reloads supported configuration files. |

---

## ProtectionStones Migration

LederProtections `v1.1.0` includes migration tools for moving from **ProtectionStones** to **LederProtections**.

Main commands:

| Command | Description |
|---|---|
| `/lep migrate protectionstones scan` | Scans for ProtectionStones regions. |
| `/lep migrate protectionstones import --dry-run` | Shows what would be imported without changing anything. |
| `/lep migrate protectionstones import` | Imports compatible ProtectionStones regions. |
| `/lep migrate protectionstones suggest-stones` | Generates suggested `stones.yml` tiers for missing radii. |
| `/lep migrate protectionstones import --region <regionId>` | Imports a single ProtectionStones region. |

---

## Migration Behavior

ProtectionStones migration is strict by default.

| Case | Default behavior |
|---|---|
| Exact matching radius exists in `stones.yml` | Imported |
| Radius does not exist in `stones.yml` | Skipped with `MISSING_TIER` |
| Source block differs from LederProtections material | Converted safely |
| Source stone is missing | Skipped unless `--place-stones` is used |
| Old greeting/farewell flags exist | Cleaned by default |
| ProtectionStones custom name exists | Imported from `ps-name` when available |

LederProtections does **not** silently resize protections by default.

Use nearest mode only if you intentionally want approximate radius mapping:

```text
/lep migrate protectionstones import --mode nearest
```

Nearest mode may resize imported protections.

---

## Recommended Migration Workflow

Before migrating:

1. Back up your server.
2. Back up your worlds.
3. Back up `plugins/WorldGuard/`.
4. Back up `plugins/LederProtections/`.
5. Remove or disable ProtectionStones.
6. Keep WorldGuard and WorldEdit installed.
7. Install LederProtections.
8. Run scan.
9. Run dry-run.
10. Review the generated report.
11. Import one region first.
12. Run `/lep check`.
13. Import the rest.

Recommended commands:

```text
/lep migrate protectionstones scan
/lep migrate protectionstones import --dry-run --verbose
/lep migrate protectionstones suggest-stones
/lep migrate protectionstones import --region <regionId>
/lep check
```

---

## Native Export and Import

LederProtections can export and import its own protection data.

| Command | Description |
|---|---|
| `/lep export protections` | Exports all LederProtections protections. |
| `/lep import protections <file> --dry-run` | Tests an import file without changing anything. |
| `/lep import protections <file>` | Imports protections from a file. |

Exports are useful for:

- backups;
- server transfers;
- support reports;
- testing migrations.

---

## Protection Stones

Protection stones are configured in:

```text
plugins/LederProtections/stones.yml
```

Common default sizes:

| Stone | Radius |
|---|---:|
| x4 | 4 |
| x8 | 8 |
| x16 | 16 |
| x32 | 32 |
| x64 | 64 |

Server owners can configure:

- material;
- radius;
- display name;
- price;
- upgrade path;
- permission;
- shop visibility.

---

## Roles

LederProtections uses role-based access.

| Role | Description |
|---|---|
| Owner | Main owner of the protection. |
| Co-owner | Trusted user with management access. |
| Member | Allowed user with normal access. |
| Visitor | Default outsider role. |
| Blocked | Restricted player, if supported by configuration. |

---

## Personal and Admin GUIs

Players can open their protections with:

```text
/p
```

The `/p` GUI only shows protections where the player has a normal role, such as owner, co-owner or member.

Administrators do **not** automatically see every protection in `/p`.

For global admin browsing, use:

```text
/lep admin
```

---

## Economy Support

Vault is optional.

Economy features require:

- Vault;
- a Vault-compatible economy plugin.

Economy can be used for:

- protection shop purchases;
- upgrade costs;
- teleport costs.

If Vault is not installed, economy features are disabled.

---

## PlaceholderAPI Support

PlaceholderAPI is optional.

When PlaceholderAPI is installed, LederProtections registers its internal expansion.

Example placeholder:

```text
%lederprotections_version%
```

Use placeholders in compatible plugins such as scoreboards, tab lists, menus and holograms.

---

## Update Checker

LederProtections includes an informational update checker.

The update checker:

- checks for new versions;
- can notify admins on join;
- does not download updates;
- does not install files;
- does not replace plugin jars.

Update notifications require:

```text
lederprotections.update
```

---

## Diagnostics

Useful diagnostic commands:

| Command | Description |
|---|---|
| `/lep version` | Shows plugin version and update-checker status. |
| `/lep info` | Shows runtime/plugin information. |
| `/lep status` | Shows plugin/server status. |
| `/lep check` | Checks protection data consistency. |

Run `/lep check` after:

- installing the plugin;
- updating the plugin;
- changing `stones.yml`;
- migrating protections;
- restoring from backup.

---

## Anti-Exploit Protection

LederProtections includes protection checks for common bypass methods.

Examples:

| Area | Protection |
|---|---|
| Pistons | Blocks cross-border block movement. |
| Hoppers | Prevents unauthorized item extraction. |
| Dispensers | Blocks protected boundary abuse. |
| Dispenser arrows | Prevents projectile damage across protection borders. |
| TNT/explosions | Protects protected blocks. |
| Lava/water | Prevents unwanted boundary flow depending on rules. |
| PvP/knockback | Blocks denied combat interactions. |
| GUIs | Prevents inventory extraction tricks. |

---

## Permissions

Common permissions:

| Permission | Description |
|---|---|
| `lederprotections.use` | Allows access to basic features. |
| `lederprotections.shop` | Allows using the protection shop. |
| `lederprotections.border` | Allows showing visual borders. |
| `lederprotections.sethome` | Allows setting teleport points when enabled. |
| `lederprotections.upgrade` | Allows upgrading protections. |
| `lederprotections.info` | Allows viewing runtime information. |
| `lederprotections.update` | Allows receiving update notifications. |
| `lederprotections.admin` | Main admin permission. |
| `lederprotections.admin.protections` | Allows opening the admin protection browser. |
| `lederprotections.admin.migrate` | Allows using migration tools. |
| `lederprotections.admin.export` | Allows exporting protection data. |
| `lederprotections.admin.import` | Allows importing protection data. |
| `lederprotections.bypass.rules` | Allows bypassing the internal rule engine. |

Do not give admin, migration, import, export or bypass permissions to normal players.

---

## Example LuckPerms Setup

Basic player group:

```text
lp group default permission set lederprotections.use true
lp group default permission set lederprotections.shop true
lp group default permission set lederprotections.border true
lp group default permission set lederprotections.sethome true
lp group default permission set lederprotections.upgrade true
lp group default permission set lederprotections.stone.4 true
lp group default permission set lederprotections.stone.8 true
lp group default permission set lederprotections.stone.16 true
lp group default permission set lederprotections.limit.3 true
```

Admin group:

```text
lp group admin permission set lederprotections.admin true
lp group admin permission set lederprotections.admin.protections true
lp group admin permission set lederprotections.admin.migrate true
lp group admin permission set lederprotections.admin.export true
lp group admin permission set lederprotections.admin.import true
lp group admin permission set lederprotections.info true
lp group admin permission set lederprotections.update true
```

---

## Configuration Files

Common files:

| File | Description |
|---|---|
| `config.yml` | Main plugin configuration. |
| `stones.yml` | Protection stone tiers and upgrade paths. |
| `lang/en.yml` | English messages. |
| `lang/es.yml` | Spanish messages. |
| `data/` | Saved protection data. |
| `migrations/` | Migration reports and suggested tiers. |
| `exports/` | Exported LederProtections protection data. |

---

## Safety Recommendations

Recommended production practices:

- Back up your server regularly.
- Test updates on a staging server first.
- Run `/lep check` after updates.
- Do not edit data files while the server is running.
- Review migration reports before importing.
- Do not run ProtectionStones and LederProtections managing the same regions at the same time.
- Give admin permissions only to trusted staff.

---

## Support Checklist

When reporting an issue, include:

| Information | Command or source |
|---|---|
| LederProtections version | `/lep version` |
| Runtime information | `/lep info` |
| Protection diagnostics | `/lep check` |
| Server software | `/version` |
| WorldGuard version | Plugin list or console |
| WorldEdit version | Plugin list or console |
| Vault version, if used | Plugin list or console |
| PlaceholderAPI version, if used | Plugin list or console |
| Console errors | Server logs |
| Migration report, if relevant | `plugins/LederProtections/migrations/` |

---

## Documentation

Recommended Wiki pages:

- Installation
- Dependencies
- Commands
- Permissions
- Configuration
- Protection Stones
- Roles and Members
- Rules System
- Shop and Economy
- Upgrades
- Teleportation
- Borders
- PlaceholderAPI
- Migration Tools
- Update Checker
- Diagnostics
- Anti-Exploit Protection
- Compatibility
- FAQ
- Changelog

---

## License

Check the project repository or distribution page for the current license and distribution terms.

---

## Notes

LederProtections is built with a focus on:

- security;
- efficiency;
- clean server administration;
- player-friendly protection management;
- safe migration from older protection-stone systems.
