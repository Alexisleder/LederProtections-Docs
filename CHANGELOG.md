# Changelog

## 1.0.0-beta.2

### Compatibility
- Migrated the public build to a Bukkit/Spigot-compatible base.
- Removed the runtime requirement for Paper Adventure components from GUI, item and message layers.
- Verified compatibility on Minecraft 1.21.x with Spigot, Paper, Purpur and Pufferfish.
- Paper remains recommended for production servers.
- Folia is not supported yet.

### Security and hardening
- Hardened plugin GUIs against shift-click, number-key swaps, double-click, drag, drop and offhand swap interactions.
- Added extra inventory synchronization for Spigot ghost-item behavior when players close GUIs immediately after blocked clicks.
- Centralized GUI item creation and GUI context parsing to reduce duplicated logic and translation-sensitive comparisons.

### Support tools
- Added `/lep info`, `/lep status` and `/lep version` for quick runtime diagnostics.
- Added platform diagnostics for Spigot/Paper/Purpur/Pufferfish-like servers and Adventure runtime availability.
- Added a dedicated `lederprotections.info` permission for runtime information access.

## 1.0.0-beta.1

Initial beta with WorldGuard-backed protection stones, custom role-based rules, GUI management, Vault economy support, upgrades, borders, PlaceholderAPI support and audit/backups.
