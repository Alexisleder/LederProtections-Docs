# LederProtections

**LederProtections** is a premium-style protection stone plugin for **Minecraft 1.21.x servers**, focused on security, performance, clean GUI management, WorldGuard integration, and anti-exploit protection.

> Current version: **v1.0.0**
> Target compatibility: **Minecraft 1.21.x**
> Tested on: **Spigot, Paper, Purpur and Pufferfish 1.21.x**
> Required Java version: **Java 21**
> Recommended server software: **Paper**

---

## About

LederProtections allows players to protect their lands, bases, chests, builds, farms and gameplay areas using configurable protection stones.

The plugin uses **WorldGuard** as the region backend, but includes its own custom role-based rule engine for more precise control over player actions inside protections.

LederProtections is designed to provide a polished, secure and server-owner-friendly protection experience while keeping the player interface simple and clean.

---

## Download

Official Modrinth page:

```text
https://modrinth.com/plugin/lederprotections
```

---

## Wiki

LederProtections wiki:

```text
https://github.com/Alexisleder/LederProtections-Docs/wiki
```

---

## Main Features

* Configurable protection stones.
* WorldGuard and WorldEdit integration.
* Personal protection GUI with `/p`.
* Dedicated administrative protection browser with `/lep admin`.
* Members, co-owners, owners and visitors.
* Protection transfer support.
* Protection rename support.
* Custom role-based rule engine.
* Visual protection borders with particles.
* Protection upgrades.
* Optional Vault economy support.
* Optional protection shop.
* Protection teleport support with cooldown and movement checks.
* PlaceholderAPI support.
* Runtime diagnostics and repair-friendly tools.
* Safe persistence handling.
* Protection index for efficient lookups.
* Modrinth-based update checker.
* Anti-exploit protection against common bypasses.

---

## Compatibility

LederProtections v1.0.0 has been tested on:

* **Spigot 1.21.x**
* **Paper 1.21.x**
* **Purpur 1.21.x**
* **Pufferfish 1.21.x**

Paper remains recommended for production servers.

### Unsupported

* **Folia is not supported yet.**
* Minecraft versions before **1.21** are not officially supported.

---

## Requirements

### Required

* Java 21
* Minecraft server 1.21.x
* WorldEdit
* WorldGuard

### Optional

* Vault
* PlaceholderAPI

Vault is only needed if you want economy-based features such as shop purchases, upgrades or teleport costs.

PlaceholderAPI is only needed if you want to use LederProtections placeholders in other plugins.

---

## Basic Commands

| Command        | Description                                             |
| -------------- | ------------------------------------------------------- |
| `/p`           | Open the player's personal protection menu.             |
| `/p border`    | Show or hide the visual border of a protection.         |
| `/lep admin`   | Open the administrative protection browser.             |
| `/lep shop`    | Open the protection stone shop, if enabled.             |
| `/lep check`   | Run protection diagnostics.                             |
| `/lep version` | Show the plugin core version and update-checker status. |
| `/lep info`    | Show runtime plugin information.                        |
| `/lep status`  | Show server and plugin status information.              |
| `/lep reload`  | Reload plugin configuration, if permitted.              |

Some commands require administrative permissions.

---

## Update Checker

LederProtections includes a simple Modrinth-based update checker.

It can:

* check for new versions on server startup;
* notify the console when a newer version is available;
* notify administrators when they join the server;
* show update-checker status through `/lep version`.

It does **not**:

* download updates automatically;
* install updates automatically;
* replace plugin files;
* modify server files.

Default configuration:

```yml
update-checker:
  enabled: true
  check-on-startup: true
  notify-admins-on-join: true
```

---

## PlaceholderAPI

LederProtections includes an internal PlaceholderAPI expansion.

Example placeholders:

```text
%lederprotections_version%
%lederprotections_player_protections_total%
%lederprotections_current_id%
%lederprotections_current_owner%
%lederprotections_current_role%
```

PlaceholderAPI must be installed if you want to use these placeholders in other plugins.

---

## Protection Rules

LederProtections includes protection checks for common actions and bypass attempts, including:

* block breaking;
* block placing;
* container access;
* doors, trapdoors, buttons and levers;
* item pickup behavior;
* PvP and knockback;
* pistons;
* hoppers;
* dispensers and droppers;
* TNT and explosions;
* fire, lava and water behavior;
* dispenser-fired projectiles crossing protection borders;
* fake-player edge cases.

The plugin is designed to prevent common protection bypasses while keeping normal gameplay behavior when actions do not cross protection boundaries.

---

## Documentation

Full documentation is available in the **GitHub Wiki**.

Recommended Wiki pages:

* Installation
* Dependencies
* Commands
* Permissions
* Configuration
* Protection Stones
* PlaceholderAPI
* Shop and Economy
* Roles and Members
* Rules System
* Upgrades
* Borders
* Update Checker
* Diagnostics
* Anti-Exploit Protection
* Compatibility
* FAQ
* Changelog

---

## Project Status

LederProtections is currently in its first stable release:

```text
v1.0.0
```

This version is suitable for:

* public servers;
* private servers;
* survival servers;
* SMP servers;
* server-owner testing;
* production use with proper configuration.

Paper is recommended for production environments.

---

## Source Code

The source code is currently **not public**.

This repository is currently used for:

* plugin information;
* documentation;
* GitHub Wiki;
* changelogs;
* release notes;
* issue tracking if enabled.

LederProtections is free to use, but it is not open source at this time.

---

## Why isn’t LederProtections open source yet?

LederProtections may become open source in the future, but for now the source code remains private while the plugin continues to mature.

The goal is to build a premium-quality protection plugin that server owners can use for free, with strong performance, anti-exploit checks, clean GUIs, WorldGuard support, economy features and a simple experience for players.

Keeping the source private during the early stable stage helps protect the project from being copied, reuploaded, sold or modified in low-quality ways before it is fully ready.

In the future, once the project is more mature, the source code may be released under clear terms.

---

## License

LederProtections is currently distributed as a private-source project.

Unless a license is explicitly provided, all rights are reserved by the author.



---

## Brand

LederProtections is part of the **Leder** plugin ecosystem, focused on creating polished, optimized, secure and high-quality Minecraft plugin experiences.
