# Compatibility

LP does not include or deliver a resource pack. Server-provided themes use ordinary
model keys/CMD and optional tracking of an exact external pack UUID. This is not a
native item-registry adapter or certification of third-party pack managers. See
[external pack setup and limits](https://github.com/Alexisleder/LederProtections-Docs/wiki/External-Resource-Packs).

## Release 1.5.0 verification — 2026-11-07

| Target | Evidence for this release | Server Java |
|---|---|---|
| Spigot API 1.21.1 | Final build and automated tests; release bytecode target | 21 |
| Spigot API 26.2 | Final sources compiled successfully | 25 |
| Spigot API 26.3 | Final sources compiled successfully | 25 |
| Other 1.21.x / 26.1 patches | Compatibility targets, not individually verified in this closeout | Match server |
| Paper / Purpur / Pufferfish | Bukkit/Spigot-compatible targets; no separate final runtime matrix recorded | Match server |
| Geyser / Floodgate | Optional detection/fallback implemented; actual crossplay testing pending | Match Java backend |
| Folia / future snapshots | Not supported claims | — |

The user reported successful local testing during development. Earlier context named
26.2 as the test environment, but a fresh exact server/Java/WG/WE version capture and
a checklist of tested actions were not supplied. Do not turn this into a claim that
all versions or integrations have been tested in-game. The final config cleanup also
needs checking on each administrator's own configuration.

WorldEdit and WorldGuard are required. Vault, PlaceholderAPI and Head Database by
Arcaniax are optional. Use dependency builds compatible with the actual server.
The release JAR is built with Java 21 bytecode and `api-version: 1.21`; newer servers
may require a newer JVM independently of the plugin's bytecode level.

[Minecraft 26.3 is a released version](https://www.minecraft.net/en-us/article/minecraft-java-edition-26-3).
[Paper's Java matrix](https://docs.papermc.io/paper/getting-started/) lists Java 21 for
1.20–1.21.11 and Java 25 for 26.1+. These upstream requirements do not certify LP.

The final source compilation matrix uses:

- Baseline: Spigot API `1.21.1-R0.1-SNAPSHOT`, WG `7.0.14`, WE `7.3.14`, Java 21.
- Modern: Spigot API `26.2-R0.1-SNAPSHOT` and `26.3-R0.1-SNAPSHOT`, WG `7.0.19`,
  WE `7.4.5`, Java 25. These are compile inputs, not a universal dependency recommendation.

Reproduce the modern compile in PowerShell:

```powershell
./gradlew clean compileJava '-PtargetJavaVersion=25' '-PspigotApiVersion=26.3-R0.1-SNAPSHOT' '-PworldGuardVersion=7.0.19' '-PworldEditVersion=7.4.5'
```

Then rebuild the distribution with `./gradlew clean test shadowJar` using the default
Java 21 target. Do not distribute a Java 25 test build as the Java 21 baseline JAR.
See the [runtime checklist](https://github.com/Alexisleder/LederProtections-Docs/wiki/GUI-Release-Checklist) for remaining checks.

## Optional integrations

### Geyser / Floodgate preview

LP detects Bedrock players through the optional public Floodgate 2 API or Geyser API,
never by username prefixes. With the API available on the backend, Bedrock users
receive ordinary inventory menus, readable fallback titles and vanilla state items;
the Java resource pack is not offered to them. Custom player-head menu icons use a
plain item fallback with their names/lore. Authorization stays on the Java server
and uses the connected player's UUID.

Install/configure Floodgate on the backend when it lives behind a proxy; merely
installing it on the proxy does not expose its API to LP. This integration does not
implement native Bedrock forms or a Bedrock resource pack. Automated tests cover
disabling Java theme rendering for detected Bedrock players; real crossplay tests,
including linked accounts and permission checks, are pending.

Sources: [Floodgate API](https://geysermc.org/wiki/floodgate/api/),
[Geyser API](https://geysermc.org/wiki/geyser/api/),
[resource pack limitations](https://geysermc.org/wiki/geyser/faq/).

`/lep hooks` reports detected and enabled optional plugins. Detection does not
mean every feature is automatically integrated: Vault and PlaceholderAPI have
active integrations, while other detected plugins may currently provide only
compatibility status or a foundation for future work.

## Third-party protection-aware actions

LederProtections cannot safely intercept every action performed entirely inside
another plugin. For example, a sell-wand plugin may read and empty a chest
without firing a normal inventory-open event.

The other plugin should load [Public API](https://github.com/Alexisleder/LederProtections-Docs/wiki/Public-API) and call `canOpenContainer` before
reading, selling or removing items. It can similarly use `canBreakBlock`,
`canPlaceBlock` and `canInteractWithBlock`. Invalid/unloaded inputs fail closed.

If an integration does not call the API, cooperation from that plugin's author
is required; there is no reliable global listener that can infer every custom
plugin action after the fact.

## Production checks

After an update, run `/lep version`, `/lep hooks` and `/lep check`, then test
stone creation/removal, GUIs, rules, public visits, holograms and each optional
integration used by the server.
