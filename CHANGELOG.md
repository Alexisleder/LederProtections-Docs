# LederProtections Changelog

## 1.5.0 — Customizable Menus & Protection Insights

- Customizable layouts for all 22 menus, optional heads and external-pack presentation.
- Simpler protection/public menus and paginated role rules without the Source line.
- New `/p home <name or ID>` and immediate movement-based entry/exit notices.
- Interactive inspection, stale-context checks and safer confirmation sessions.
- Bounded LRU icon caching and reduced repeated GUI work.
- Configuration cleanup with backed-up gui-style migration to menus.yml.
- No integrated resource pack or automatic pack delivery.

[Complete English/Spanish changelog](https://github.com/Alexisleder/LederProtections-Docs/wiki/Release-1.5.0) · [Compatibility](https://github.com/Alexisleder/LederProtections-Docs/wiki/Compatibility)

---

## v1.4.1

GUI and hologram presentation improvements.

- Updated the project version to `1.4.1`.
- Replaced repeated icons in the protection menu with more distinct materials.
- Added optional Minecraft skin textures for directory categories, with configured material icons as fallback.
- Removed the large default background panel behind protection holograms while retaining text shadows.
- Changed the default hologram lines to show a welcome, protection name, owner (`{owner}`), description, world and stone coordinates.
- Made `{user}` identify the player viewing the hologram and `{owner}` identify the protection owner. Holograms containing `{user}` are rendered as private per-viewer TextDisplays.
- Added event-driven proximity reconciliation on block movement, join, respawn and chunk load; displays are cleaned up on exit and quit without periodic scans or forced chunk loads.
- Documented all native hologram variables in `config.yml`, including the distinct `{owner}` and `{user}` meanings; PlaceholderAPI expansions in private holograms use the viewer's context and refresh without per-tick polling.
- Existing custom hologram lines are preserved; replace `{user}` with `{owner}` when an old line intended to display the protection owner.
- Documented legacy `&` colors and formatting for hologram lines.
- Added a `head-texture` category option. It accepts only a 64-character texture hash from `textures.minecraft.net`; blank keeps the category material.
- Integrated bStats using plugin ID `34348` for aggregate server and version statistics. LederProtections adds no custom charts or player/protection data.
- Relocated bStats classes into LederProtections' namespace to avoid conflicts with other plugins.

See [Minecraft-Heads](https://minecraft-heads.com/custom-heads) for a browsable head catalogue. LederProtections does not query this site at runtime.

---

## v1.4.0

Public protection directory, holograms, and native environmental policies.

See the [complete 1.4.0 release notes](https://github.com/Alexisleder/LederProtections-Docs/wiki/Release-1.4.0) for behavior, customization, security, upgrade guidance, and future improvement areas.

### Added

- Added opt-in public protection profiles with configurable titles, descriptions, categories, icons, welcome messages, visit points, and visibility.
- Added the `/warps` public directory with search, category filtering, sorting, favorites, visit counters, and pagination.
- Added configurable public-visit warmups, cooldowns, movement/damage cancellation, cross-world control, and safe destination validation.
- Added administrator controls for featured and hidden directory entries.
- Added Bukkit `TextDisplay` holograms with configurable lines, placeholders, range, height, and per-protection state.
- Added inheritable per-protection environmental policies for hostile spawning, TNT, creepers, other explosions, and fire spread.
- Added `LederProtectionsApi#canOpenContainer` so sell-wand and inventory addons can enforce the same container rules before mutating contents.
- Added `canBreakBlock`, `canPlaceBlock`, and `canInteractWithBlock` public API checks for broader plugin integration.
- Added complete public-directory, hologram, role, bounds, limit, and compatibility placeholders.
- Moved the public API source into the standalone `LederAPI` project and versioned artifact `com.alexisleder:lederprotections-api:1.0.0`.

### Changed

- Environmental explosion and fire decisions now use LederProtections policies while protection-boundary barriers remain enforced independently.
- Existing bundled configuration and language files receive missing 1.4.0 keys through the safe merge and backup system.
- Existing protections remain private by default until their public profile is explicitly changed.
- `/lep reload` now refreshes optional compatibility hooks and safely replaces the internal PlaceholderAPI expansion.
- Placeholder requests from asynchronous consumers now use bounded main-thread resolution, short-lived caches and deduplicated work.
- Native imports, update responses, addon tab completions and audit writes now enforce defensive limits.

### Fixed

- Fixed `directory.favorite.yes` and `directory.favorite.no` being parsed as YAML boolean keys during upgrades.
- Removed raw material identifiers from public icon selector item titles while retaining lore, PDC identification, and whitelist validation.
- Updated the default hologram heading to `PROTECCIÓN` in Spanish and `PROTECTION` in the English fallback.

### Notes

- No manual protection-data migration is required.
- Existing administrator customizations are preserved; missing keys are added without replacing entire YAML files.
- Customized `holograms.lines` lists are not overwritten.
- The public API contract remains version `1.0`.

### Quality of life

- Public destinations now include search, categories, sorting, favorites, visit counters, and pagination.
- Protection publication is opt-in; existing protections stay private after upgrading.
- Public icon names are player-friendly and no longer expose raw Bukkit material identifiers.
- `/lep reload` applies compatibility, directory, hologram, and PlaceholderAPI changes without requiring a complete server restart.
- New configuration and language keys use the backup-aware merge system and preserve customized values.

### Customization

- Server owners can configure public categories, allowed icons, visit behavior, directory rules, and safe-teleport controls.
- Players can customize public titles, descriptions, welcome messages, visibility, visit points, and hologram state within configured limits.
- Holograms support global, default, and per-protection state plus configurable lines, height, view distance, line width, and colors.
- Environmental defaults can be inherited or overridden per protection.

### Structure and performance

- The public API contract now lives in the standalone `LederAPI` project while private implementations remain in LederProtections.
- Addons obtain the API through Bukkit's `ServicesManager` and consume immutable snapshots instead of private classes.
- Directory, hologram, compatibility, and placeholder responsibilities are isolated in dedicated services.
- Holograms avoid per-tick world scans and use targeted loaded-chunk cleanup.
- Placeholder work is cached, deduplicated, bounded, and safely transferred to the primary thread when required.
- Protection mutation events are coalesced so consumers observe coherent repository and spatial-index state.

### Compatibility

- The default release continues to compile against Spigot API 1.21.1 and Java 21 for the widest 1.21.x compatibility.
- The same sources also compile against Spigot API 26.3, WorldGuard 7.0.19, and WorldEdit 7.4.5 using Java 25.
- The plugin does not require Paper-only, Adventure, CraftBukkit, or NMS classes at runtime.
- Bukkit/Spigot `TextDisplay` is used for holograms.
- Spigot, Paper, Purpur, and Pufferfish 1.21.x and compatible 26.x builds are supported targets; Paper remains recommended when a stable build exists.
- Java 21 is required for 1.21.x; Minecraft 26.1+ and its current WorldGuard/WorldEdit builds require Java 25.
- Folia is not supported yet.

### Areas for future improvement

The following are roadmap candidates, not 1.4.0 promises:

- Automated runtime regression tests on real Spigot, Paper, Purpur, and Pufferfish servers.
- A complete Folia scheduler and region-thread audit.
- Public Maven hosting, CI releases, signed API artifacts, and binary compatibility checks.
- Deeper optional integrations for hooks that currently provide detection or limited compatibility.
- Configurable PlaceholderAPI boolean and empty-value output styles.
- Additional timings, profiling, and large-network integration tests.

---

## v1.3.0

Public addon API release.

### Added

- Added the versioned `LederProtectionsApi` service, obtainable through Bukkit's `ServicesManager`.
- Added immutable protection, bounds, and teleport-home snapshots with stable protection IDs.
- Added stored and effective role queries, member-feature checks, and addon-setting management checks.
- Added bounded safe-location searches that reuse the protection teleport safety policy and support an interior margin.
- Added snapshot-based safe-location searches for landing after a protection is removed.
- Added non-cancelable create, change, and removal lifecycle events with change categories.
- Added a formal registry for addon subcommands under `/p`, including permissions, tab completion, reserved-name validation, and automatic cleanup when the addon is disabled.
- Added developer integration documentation in `docs/API.md`.
- Added a dedicated API jar and Maven Local publication configuration under `com.alexisleder:lederprotections-api:1.0`.

### Changed

- Protection mutations in one server cycle are coalesced before lifecycle events are published, preventing transient import rollback states from leaking to addons.
- Coalesced removal events retain the last record actually deleted, so snapshot-based safety uses the correct final bounds and home.
- Lifecycle events are published on the next main-thread cycle so the repository and spatial index are coherent when listeners receive them.
- Public effective roles now reserve `ADMIN` for `lederprotections.admin`; rule-engine bypass permissions never grant addon membership.
- `BLOCKED` now has explicit precedence in member-feature checks, including over the global administrator permission.
- Stored-role resolution also gives `BLOCKED` precedence over accidentally overlapping owner, co-owner, or member entries.

### Notes

- The public API contract version is `1.0`; it is intentionally independent from the plugin version `1.3.0`.
- No protection-data or configuration migration is required.
- Existing security listeners and rules are unchanged.

---

## v1.2.1

Protection-boundary and automation security hotfixes.

### Added

- Added `container-open` as an independent rule for dispensers, droppers, hoppers, furnaces, brewing stands, crafters, and other functional containers.
- Added persistent origin tracking for falling blocks and dispenser projectiles without resident projectile maps.
- Added authoritative dispenser projectile checks for impacts, entity damage, fire, explosions, splash potions, and lingering potion clouds.

### Changed

- Purely environmental block formation is allowed inside protections while entity-caused formation is validated separately.
- `pressure-plate-use` now also documents and controls tripwire and redstone ore for backward-compatible configuration keys.
- New installations deny visitor physical-trigger use by default. Existing configured values remain preserved during updates.
- Redstone boundary checks now compare direct power per face and retain legitimate internal power when internal and external signals coexist.
- Ender chests are governed by `chest-open`; other functional containers use `container-open`.

### Fixed

- Fixed natural snow, ice, fluid generators, concrete hardening, snow golems, and authorized Frost Walker being blocked by the environmental listener.
- Fixed automatic bone meal and moss growth crossing from outside or between different protections.
- Fixed pressure plates, farmland trampling, turtle eggs, tripwire, and redstone ore bypassing physical-interaction rules.
- Fixed exterior pressure plates and foreign redstone sources activating protected mechanisms.
- Fixed visitors opening dispensers, droppers, hoppers, furnaces, and similar containers without a dedicated rule.
- Fixed Endermen, falling blocks, villagers, sheep, and other entity block changes not enforcing protection boundaries consistently.
- Fixed dispenser projectiles relying only on a short trajectory prediction and allowing distant secondary effects.
- Fixed protected dispensers firing when their only direct power source belonged to the exterior or another protection.
- Fixed duplicate entity-interaction message cooldown entries remaining after players disconnected.

### Notes

- No protection-data migration is required.
- Missing `container-open` keys and translations are merged automatically without overwriting customized values.
- Existing `pressure-plate-use` values are intentionally preserved; administrators upgrading from an older config should review that rule for visitors.

---

## v1.2.0

Entity protection rules and safer configuration updates.

### Added

- Added `entity-interact` to control interactions with villagers, animals, and other living entities inside protections.
- Added `entity-damage` to protect villagers, golems, mobs, and other non-animal living entities from unauthorized player damage.
- Added automatic bundled configuration updates for `config.yml`, `stones.yml`, `lang/es.yml`, and `lang/en.yml`.
- Added backup and default-snapshot handling so new config keys can be merged without overwriting user customizations.

### Changed

- Existing `animal-damage`, PvP, and decorative entity rules remain separate to preserve existing behavior.
- `/lep reload` now applies safe bundled config/language updates before reloading registries.

### Fixed

- Fixed villagers and other non-animal living entities not having dedicated native protection rules.
- Fixed duplicated denied-action chat messages when right-clicking protected entities such as villagers.

### Notes

- No protection data migration is required.
- Existing user config values are preserved. Missing bundled keys are added automatically on startup or `/lep reload`.
- Server owners should still back up before updating and test on a staging server when possible.

---

## v1.0.0

First stable release.

### Changed

- Promoted the plugin version from `1.0.0-beta.8` to `1.0.0`.
- Cleaned `/lep version` so it only shows the plugin core version and update checker status.
- Kept detailed runtime diagnostics in `/lep info` and `/lep status`.

### Notes

- This release includes the beta.8 dispenser projectile boundary fix.
- Public documentation updates remain pending for the final documentation pass.

---

## v1.0.0-beta.8

Security and protection-boundary fix.

### Fixed

- Blocked dispenser/dropper projectiles from damaging entities across protection borders.
- Prevented arrows and similar projectiles from being used as protected-area turrets from inside to outside.
- Prevented arrows and similar projectiles from being used to damage entities inside protections from outside.

### Notes

- Projectiles fired by machines are still allowed when both source and target are inside the same protection, or when both are outside protections.

---

## v1.0.0-beta.7

Release polish and startup diagnostics.

### Changed

- Improved update checker startup logging when the installed version is already up to date.
- Improved update checker startup logging when the installed version is newer than the current Modrinth release.
- Replaced deprecated PvP knockback event handling with a short PlayerVelocityEvent-based cancellation window.

### Notes

- The update checker still only notifies; it does not download or install updates automatically.
- The PvP change keeps blocked hits from applying knockback while avoiding Paper's deprecated event warning.

---

## v1.0.0-beta.6

Update checker integration and release polish.

### Added

- Added a lightweight update checker with the official Modrinth source built in.
- Added async version checks against the public Modrinth project versions endpoint.
- Added admin join notifications for newer versions.
- Added `lederprotections.update` permission.
- Added Spanish and English update notification messages.

### Notes

- The checker does not download or install anything automatically.
- The public update source is built into the plugin; config only controls whether startup checks and admin join notices are enabled.
- Update notices redirect admins to the public Modrinth page.

---

## v1.0.0-beta.4

Quality-of-life, admin browser and player notification update.

### Added

- Added filters and sorting to the `/lep admin` protection browser.
- Added creation date display in the admin protection browser.
- Added permission-based protection limits for server ranks.
- Added action bar notices when entering or leaving protections.
- Added per-player preferences to enable or disable entry/exit notices.

### Changed

- Polished Spanish and English chat messages to be shorter and clearer.
- Improved localization for admin browser filters and sorting labels.
- Improved `/p` player menu usability with a notification preference button.
- Improved admin protection browsing with clearer filter and sort feedback.

### Fixed

- Fixed missing Spanish notification preference messages.
- Fixed the admin browser player-head button so it shows the viewer skin.
- Fixed leftover documentation and support-template cleanup before release.

### Supported

- Spigot 1.21.x
- Paper 1.21.x
- Purpur 1.21.x
- Pufferfish 1.21.x
- Java 21
- WorldGuard
- WorldEdit
- Vault
- PlaceholderAPI

### Notes

- Paper is recommended for production servers.
- Folia is not supported yet.
- Older Minecraft versions before 1.21 are not officially supported.
- This is still a beta release. Testing on a staging server is recommended before production usage.

---

## v1.0.0-beta.3

Production hardening and admin tools update.

### Added

- Added `/lep admin`, a dedicated admin GUI to browse all server protections.
- Added `lederprotections.admin.protections` permission.
- Added owner, location, type, size and member information to the admin protection browser.
- Added safer persistence handling for protection updates.
- Added better protection data recovery behavior through safer save handling.

### Changed

- `/p` now only shows protections where the player has a normal relationship, such as owner, co-owner or member.
- Admins no longer see every server protection in the normal player menu.
- Global protection browsing is now separated into `/lep admin`.
- Improved command permission handling.
- Improved optional protection ID behavior in commands.
- Improved economy transaction safety for shop purchases, upgrades and teleport costs.

### Fixed

- Fixed shop purchases with full inventory. The player is no longer charged and the item is no longer dropped on the ground.
- Fixed PvP denial behavior to prevent unwanted knockback.
- Reduced PvP denial message spam.
- Improved protection update handling so commands and GUIs no longer show success if saving fails.
- Improved consistency between protection data, lookup index and WorldGuard updates.

### Supported

- Spigot 1.21.x
- Paper 1.21.x
- Purpur 1.21.x
- Pufferfish 1.21.x
- Java 21
- WorldGuard
- WorldEdit
- Vault
- PlaceholderAPI

### Notes

- Paper is recommended for production servers.
- Folia is not supported yet.
- Older Minecraft versions before 1.21 are not officially supported.
- This is still a beta release. Testing on a staging server is recommended before production usage.

---

## v1.0.0-beta.2

Compatibility update for Minecraft 1.21.x servers.

### Added

- Added tested support for Spigot 1.21.x.
- Confirmed compatibility with Paper 1.21.x.
- Confirmed compatibility with Purpur 1.21.x.
- Confirmed compatibility with Pufferfish 1.21.x.
- Added `/lep info`, `/lep status` and `/lep version` diagnostic commands.
- Added runtime platform detection.

### Changed

- Migrated the visual layer to Bukkit/Spigot-compatible APIs.
- Removed mandatory Paper/Adventure runtime requirements from messages, GUIs and items.
- Updated compatibility target from Paper-only to Spigot/Paper/Purpur/Pufferfish 1.21.x.
- Paper became recommended instead of required.

### Fixed

- Fixed startup failure on Spigot caused by missing Adventure classes.
- Improved GUI protection against shift-click, drag, hotbar swap, double click and ghost items.
- Improved inventory synchronization when closing GUIs quickly on Spigot.

---

## v1.0.0-beta.1

Initial public beta release.

### Added

- Protection stones.
- Configurable protection sizes.
- WorldGuard region integration.
- WorldEdit dependency support.
- Protection creation by placing stones.
- Protection removal when breaking stones.
- Configurable return of protection stones.
- Configurable protection shop.
- Vault economy support.
- Teleport system.
- Teleport warmup.
- Teleport movement cancellation.
- Protection border preview.
- GUI-based protection management.
- Protection list GUI.
- Protection management GUI.
- Members GUI.
- Co-owner support.
- Visitor rules.
- Blocked player support.
- Role-based protection rules.
- Protection upgrades.
- PlaceholderAPI support.
- English language file.
- Spanish language file.
- Configuration validation.
- Anti-exploit protections.
- Protection diagnostics.
- Repair commands.
- Debug logging options.

### Supported

- Java 21
- Minecraft 1.21.x
- WorldGuard
- WorldEdit
- Vault
- PlaceholderAPI
