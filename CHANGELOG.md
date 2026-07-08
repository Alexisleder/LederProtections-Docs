# Changelog

## LederProtections v1.0.0

First stable release of LederProtections for Minecraft 1.21.x servers.

This release includes all protection, GUI, economy, role-management, diagnostics, update-checker and security hardening work completed during the beta cycle.

### Compatibility

* Spigot 1.21.x
* Paper 1.21.x
* Purpur 1.21.x
* Pufferfish 1.21.x

Paper remains recommended for production servers.

Folia is not supported yet.

### Highlights

* WorldGuard-backed protection stones.
* Custom internal rule engine for protection actions.
* Personal protection GUI through `/p`.
* Dedicated administrative protection browser through `/lep admin`.
* Protection member, co-owner and owner role management.
* Protection transfer support.
* Protection rename support.
* Protection upgrades.
* Optional Vault economy support.
* Optional protection shop.
* Protection teleport support with cooldown and movement checks.
* PlaceholderAPI expansion.
* Runtime diagnostics through `/lep info`, `/lep status`, `/lep version` and `/lep check`.
* Modrinth-based update checker.
* Full beta-cycle hardening for GUIs, permissions, persistence and protection bypasses.

### Changed

* Promoted the plugin from beta to the first stable `v1.0.0` release.
* Cleaned up `/lep version` so it now focuses on the plugin core version and update-checker status.
* Kept `/lep check` focused on protection diagnostics instead of version information.
* Kept `/lep info` and `/lep status` as broader runtime diagnostic commands.

### Notes

* The update checker does not download, install, replace or modify plugin files automatically.
* The update checker only checks Modrinth and notifies administrators when a newer version is available.
* Documentation updates for the stable release are handled separately in the public documentation repository.

---

## LederProtections v1.0.0-beta.8

Security fix beta for dispenser projectile protection bypasses.

### Fixed

* Fixed a protection bypass where dispensers could shoot arrows across protection borders and damage players.
* Blocked dispenser-fired projectile damage when crossing from outside into a protection.
* Blocked dispenser-fired projectile damage when crossing from inside a protection to outside.
* Blocked dispenser-fired projectile damage when crossing between different protections.
* Preserved normal projectile behavior when the dispenser and target are in the same protection context.

### Notes

* Projectiles that do not cross protection boundaries keep their normal behavior.
* This version became the final beta base for the first stable release.

---

## LederProtections v1.0.0-beta.7

Polish beta for update-checker visibility and PvP knockback handling.

### Changed

* Improved Modrinth update-checker console output.
* The update checker now reports when the installed version is already up to date.
* The update checker now reports when the installed version is newer than the latest version currently published on Modrinth.
* Reworked PvP knockback handling to avoid deprecated Bukkit/Paper event usage.

### Fixed

* Removed the startup warning caused by the deprecated `EntityKnockbackByEntityEvent`.
* Preserved PvP/knockback protection behavior after replacing the deprecated event handling.

### Notes

* The update checker remains informational only.
* It does not download or install updates automatically.

---

## LederProtections v1.0.0-beta.6

Update-checker beta.

### Added

* Added a Modrinth-based update checker.
* Added startup update checking.
* Added administrator join notifications when a newer version is available.
* Added `lederprotections.update` permission for update notifications.
* Added update-checker messages to the language files.

### Changed

* Update source is handled internally by the plugin.
* Download redirection points to the public Modrinth project page.
* Simplified update-checker configuration.

### Configuration

```yml
update-checker:
  enabled: true
  check-on-startup: true
  notify-admins-on-join: true
```

### Notes

* The update checker only checks Modrinth for available versions.
* The update checker does not download, install or replace files automatically.
* This version is the first version capable of detecting future updates.

---

## LederProtections v1.0.0-beta.5

Stability and compatibility beta.

### Compatibility

* Confirmed compatibility across Minecraft 1.21.x.
* Confirmed compatibility with Spigot.
* Confirmed compatibility with Paper.
* Confirmed compatibility with Purpur.
* Confirmed compatibility with Pufferfish.

Paper remains recommended for production servers.

Folia is not supported yet.

### Changed

* Continued polishing the separation between the personal protection GUI and the admin protection browser.
* Improved GUI behavior across Spigot-compatible servers.
* Improved compatibility behavior for Paper forks.
* Improved protection listing behavior for administrators.
* Improved internal handling for translated role/group names.
* Improved general runtime stability before the update-checker integration.

### Fixed

* Fixed additional missing-message cases.
* Improved GUI extraction protection for Spigot behavior.
* Reduced unwanted feedback from fake-player combat interactions.
* Improved protection border particle behavior so border previews are shown only to the requesting player.
* Improved shop behavior when player inventory state changes.
* Improved upgrade validation and protected-area checks.

### Notes

* This beta focused on stability and compatibility before adding the update checker.

---

## LederProtections v1.0.0-beta.4

GUI, command and rule-engine polish beta.

### Changed

* Improved `/p` personal GUI behavior.
* Improved `/lep admin` administrative GUI behavior.
* Improved protection member-management GUI interactions.
* Improved protection role handling for owner, co-owner, member and visitor contexts.
* Improved command routing for protection management commands.
* Improved internal rule checks for protected interactions.
* Improved validation for protection upgrades and region changes.

### Fixed

* Fixed additional GUI interaction edge cases.
* Fixed protection-management actions that could behave inconsistently after persistence failures.
* Fixed more command paths involving explicit protection IDs.
* Fixed additional edge cases around protected interactions.
* Improved handling of fake players and automated interactions.

### Notes

* This beta focused on polishing the systems introduced in earlier betas and reducing edge-case bypasses.

---

## LederProtections v1.0.0-beta.3

Production-hardening beta for Minecraft 1.21.x servers.

### Compatibility

* Spigot 1.21.x
* Paper 1.21.x
* Purpur 1.21.x
* Pufferfish 1.21.x

Paper remains recommended for production servers.

Folia is not supported yet.

### Added

* Added `/lep admin`, a dedicated administrative protection browser.
* Added `lederprotections.admin.protections` permission for viewing all server protections through the admin GUI.
* Added clearer Folia diagnostics while keeping Folia marked as unsupported.
* Added `.gitattributes` line-ending normalization for cleaner Git diffs.

### Changed

* `/p` is now a personal player protection menu, even for administrators.
* Administrators no longer automatically see every server protection in `/p`.
* Global protection browsing is now separated into `/lep admin`.
* Improved command permission routing so `/lep info`, `/lep status`, and `/lep version` can use `lederprotections.info` without granting normal player management access.
* Improved optional protection ID handling for commands such as rename, transfer, member, co-owner, block and debug helpers.
* Improved persistence handling so commands and GUIs do not report success if protection saving fails.

### Fixed

* Fixed PvP-denied interactions applying knockback in protected areas.
* Reduced spam from repeated PvP-denied messages.
* Prevented shop purchases when the player inventory is full.
* Prevented purchased protection stones from being dropped on the ground when inventory space is unavailable.
* Hardened economy transactions for shop purchases, upgrades and teleport costs.
* Hardened protection update persistence after rename, transfer, member changes, blocked-player changes, rule changes, debug changes and GUI changes.
* Improved safe handling of invalid explicit protection IDs to avoid accidentally falling back to the current protection.

---

## LederProtections v1.0.0-beta.2

Spigot compatibility and GUI hardening beta.

### Compatibility

* Migrated the public build to a Bukkit/Spigot-compatible base.
* Removed the runtime requirement for Paper Adventure components from GUI, item and message layers.
* Verified compatibility on Minecraft 1.21.x with Spigot, Paper, Purpur and Pufferfish.
* Paper remains recommended for production servers.
* Folia is not supported yet.

### Security and hardening

* Hardened plugin GUIs against shift-click, number-key swaps, double-click, drag, drop and offhand swap interactions.
* Added extra inventory synchronization for Spigot ghost-item behavior when players close GUIs immediately after blocked clicks.
* Centralized GUI item creation and GUI context parsing to reduce duplicated logic and translation-sensitive comparisons.

### Support tools

* Added `/lep info`, `/lep status` and `/lep version` for quick runtime diagnostics.
* Added platform diagnostics for Spigot/Paper/Purpur/Pufferfish-like servers and Adventure runtime availability.
* Added a dedicated `lederprotections.info` permission for runtime information access.

---

## LederProtections v1.0.0-beta.1

Initial public beta.

### Added

* Added WorldGuard-backed protection stones.
* Added configurable protection stone types.
* Added protection creation by placing configured stones.
* Added protection removal behavior when breaking protection stones.
* Added owner-based protection management.
* Added role-based protection access with visitor, member, co-owner and owner contexts.
* Added custom internal rule checks for protected actions.
* Added GUI-based protection management.
* Added member management.
* Added Vault economy support.
* Added protection upgrades.
* Added protection border preview support.
* Added PlaceholderAPI support.
* Added audit and backup foundations.

### Notes

* This was the first public beta foundation for LederProtections.
