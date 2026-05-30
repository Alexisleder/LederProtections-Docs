# LederProtections

**LederProtections** is a premium-style protection stone plugin for **Minecraft Paper servers**, focused on security, performance, clean GUI management, and anti-exploit protection.

> Current version: **v1.0.0-beta.1**  
> Target compatibility: **Paper 1.21.x**  
> Tested on: **Paper 1.21.8**  
> Required Java version: **Java 21**

---

## About

LederProtections allows players to protect their lands, bases, chests, builds, and gameplay areas using configurable protection stones.

The plugin uses **WorldGuard** as the region backend, but includes its own custom role-based rule engine for more precise control over player actions inside protections.

---

## Wiki

LederProtections wiki: https://github.com/Alexisleder/LederProtections-Docs/wiki

---

## Main Features

- Configurable protection stones
- WorldGuard and WorldEdit integration
- Clean GUI management with `/p`
- Vault economy support
- Protection shop
- Protection upgrades
- Members, co-owners, visitors, blocked players, and admin roles
- Custom rule engine by role and action
- Visual protection borders with particles
- PlaceholderAPI support
- Safe protection backups
- Audit logs
- Repair and diagnostic tools
- Anti-exploit protection against common bypasses

---

## Required Dependencies

- **Paper 1.21.x**
- **Java 21**
- **WorldEdit**
- **WorldGuard**

Optional dependencies:

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

---

## Basic Commands

| Command | Description |
|---|---|
| `/p` | Open the protection list GUI |
| `/p border` | Toggle visual protection border |
| `/lep shop` | Open the protection stone shop |
| `/lep check` | Run diagnostics |
| `/lep hooks` | Show optional plugin hooks |
| `/lep reload` | Reload configuration |
| `/lep repair` | Use repair tools |

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

---

## Documentation

Full documentation is available in the **GitHub Wiki**:

```text
Open the Wiki tab of this repository.
```

Recommended Wiki pages:

- Installation
- Dependencies
- Commands
- Permissions
- Configuration
- Protection Stones
- PlaceholderAPI
- Shop and Economy
- Roles and Members
- Rules System
- Upgrades
- Borders
- Audit Logs and Backups
- Repair Commands
- Anti-Exploit Protection
- Compatibility
- FAQ
- Changelog

---

## Project Status

LederProtections is currently in **beta**.

This version is suitable for:

- closed beta testing
- private server testing
- server-owner testing

Older Minecraft versions before **1.21** are not officially supported in this beta.

---

## Source Code

The source code is currently **not public**.

This repository is currently used for:

- plugin information
- documentation
- GitHub Wiki
- changelogs
- issue tracking if enabled

---

## License

LederProtections is currently distributed as a private-source project.

Unless a license is explicitly provided, all rights are reserved by the author.
---
## Why isn’t LederProtections open source yet?

Good question! LederProtections may become open source in the future, but for now I want to keep polishing the plugin until it is more stable, secure and complete.

My goal is to build a premium-quality protection plugin that server owners can use for free, with strong performance, anti-exploit checks, clean GUIs, WorldGuard support, economy features and a simple experience for players.

Since the project is still in beta, I also want to protect the work from being copied, reuploaded, sold, or modified in a low-quality way before it is fully ready.

For now, LederProtections is free to use but not open source yet. In the future, once the project is more mature, I may consider releasing the source code under clear terms.
---

## Brand

LederProtections is part of the **Leder** plugin ecosystem, focused on creating polished, optimized, secure, and high-quality Minecraft plugin experiences.
