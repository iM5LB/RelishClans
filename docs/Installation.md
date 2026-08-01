# Installation Guide

Quick installation guide for RelishClans.

## Requirements

| Component | Requirement | Notes |
|-----------|-------------|-------|
| **Minecraft** | 1.21+ | Paper API target |
| **Server** | Paper, Purpur, or Paper-based forks | Spigot not officially supported |
| **Java** | 21+ | Required for modern Paper |
| **Soft Dependencies** | Vault, WorldGuard, PlaceholderAPI, PacketEvents | Auto-detected if present |

## Installation Steps

1. Download `RelishClans-x.x.x.jar` (use the shadowed JAR from `shadowJar`)
2. Place it in your server's `plugins/` folder
3. (Optional) Install [Vault](https://www.spigotmc.org/resources/vault.34315/) + an economy provider
4. (Optional) Install [WorldGuard](https://enginehub.org/worldguard) for region claim/fly/war flags
5. (Optional) Install [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/)
6. (Optional) Install [PacketEvents](https://modrinth.com/plugin/packetevents) for client-side fake-player replay (Paper Mannequin works without it)
7. Restart the server
8. Edit `plugins/RelishClans/config.yml` and `lang/en.yml` as needed
9. (Optional Premium) Set `license-key: "..."` from the [M5LB Store](https://m5lb.run.place/), then restart or `/clan reload`

## Verify Installation

Check console for the RelishClans startup banner:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  RELISH CLANS  v1.0.0
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  ▶ Status: Enabled
  ▶ Storage: YAML
  ▶ Economy: Connected / Not available
  ▶ Region Hook: ...
  ▶ PlaceholderAPI: Registered / Not available
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Or run: `/plugins`

## First-Time Files

After first start you should see:

```
plugins/RelishClans/
├── config.yml
├── lang/
│   └── en.yml
├── clans.yml          # when storage.type: YAML
├── wars.yml
└── preferences.yml
```

With `SQLITE` / `MYSQL`, clan & war data live in the database instead of (or in addition to) YAML files.

## Quick Setup

```bash
# Grant base command access (default true for all players)
/lp group default permission set relishclans.command true

# Admin bypass + reload
/lp group admin permission set relishclans.admin true

# In-game
/clan help
/clan create MyClan
/clan claim
```

## Troubleshooting

**Plugin not loading?**
- Check Java: `java -version` (must be 21+)
- Confirm Paper-based server
- Read console stack traces

**Economy costs not working?**
- Install Vault + an economy plugin (e.g. RelishEconomy) — paid unlocks always require economy

**Placeholders empty?**
- Install PlaceholderAPI and restart
- Use `%relishclans_name%` etc. (see [PlaceholderAPI.md](PlaceholderAPI.md))

## License (Premium)

```yaml
license-key: ""
```

Empty or invalid keys keep **free** features online. See [Free vs Premium](FreeVsPremium.md). Status: `/clan license`.

## Next Steps

- [Quick Start](QuickStart.md)
- [Free vs Premium](FreeVsPremium.md)
- [Configuration](Configuration.md)
- [Permissions](Permissions.md)
