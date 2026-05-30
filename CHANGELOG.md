# Changelog

## LederProtections v1.0.0-beta.3

Production-hardening beta for Minecraft 1.21.x servers.

## Compatibility

- Spigot 1.21.x
- Paper 1.21.x
- Purpur 1.21.x
- Pufferfish 1.21.x

Paper remains recommended for production servers.

Folia is not supported yet.

## Added

- Added `/lep admin`, a dedicated administrative protection browser.
- Added `lederprotections.admin.protections` permission for viewing all server protections through the admin GUI.
- Added clearer Folia diagnostics while keeping Folia marked as unsupported.
- Added `.gitattributes` line-ending normalization for cleaner Git diffs.

## Changed

- `/p` is now a personal player protection menu, even for administrators.
- Administrators no longer automatically see every server protection in `/p`.
- Global protection browsing is now separated into `/lep admin`.
- Improved command permission routing so `/lep info`, `/lep status`, and `/lep version` can use `lederprotections.info` without granting normal player management access.
- Improved optional protection ID handling for commands such as rename, transfer, member, co-owner, block, and debug helpers.
- Improved persistence handling so commands and GUIs do not report success if protection saving fails.

## Fixed

- Fixed PvP-denied interactions applying knockback in protected areas.
- Reduced spam from repeated PvP-denied messages.
- Prevented shop purchases when the player inventory is full.
- Prevented purchased protection stones from being dropped on the ground when inventory space is unavailable.
- Hardened economy transactions for shop purchases, upgrades, and teleport costs.
- Hardened protection update persistence after rename, transfer, member changes, blocked-player changes, rule changes, debug changes, and GUI changes.
- Improved safe handling of invalid explicit protection IDs to avoid accidentally falling back to the current protection.

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
