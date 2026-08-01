# Troubleshooting

Common RelishClans issues and fixes.

---

## Plugin will not enable

**Symptoms:** Missing from `/plugins`, red in console.

**Checks:**
1. Java 21+ (`java -version`)
2. Paper / Purpur 1.21+ (not Spigot)
3. Console errors on enable — fix stack traces first
4. Ensure the JAR is the **shadowJar** build (bundled JDBC drivers)

---

## Claims not working

| Issue | Fix |
|-------|-----|
| “Need Officer” | Promote the player or use an Officer+ account |
| “Already claimed” | `/clan map` to see owners |
| “Too close to …” | Raise or lower `settings.claim-buffer` (default 1). Allies can claim next to each other. |
| “Limit reached” | Raise `settings.max-claims` or unlock `claim_boost` |
| “Not contiguous” | Disable `contiguous-claims` or claim adjacent chunks |
| WorldGuard deny | Allow `relish-clans-claim` in that region |

---

## Core / teleport issues

| Issue | Fix |
|-------|-----|
| No core | Claim at least one chunk — core places on first claim |
| Can't move core | Unlock & activate `beacon_relocator`; need Admin+ |
| Move fails | Destination must be claimable (limit, region, contiguous) |
| Teleport on cooldown | Wait or grant `relishclans.cooldown.bypass` |
| Old core block left behind | `/clan reload` runs migration; ensure chunk is loaded |

The core is an **upgradable beacon**. Tiers improve war defense (capture time / radius); the block stays a beacon.

---

## War “already at war”

1. `/clan admin wars` — list active wars  
2. `/clan admin endwar <clanA> <clanB>` — force clear  
3. `/clan reload` — reloads wars from storage and purges invalid entries  

Ghost wars (missing clans / self-wars) are cleaned on load.

---

## Economy / flag costs

| Issue | Fix |
|-------|-----|
| “Economy not available” | Install Vault + an economy provider (paid actions always require economy) |
| Can't afford | Deposit to clan bank or earn money |
| Core upgrade fails | Bank first, then player wallet; check Admin+ role |

---

## PlaceholderAPI empty

1. Install PlaceholderAPI and restart  
2. Look for `Registered PlaceholderAPI expansion: relishclans`  
3. Test: `/papi parse me %relishclans_in_clan%`  
4. Join a clan for name/tag/bank values  

---

## Storage / data loss

| Storage | Tips |
|---------|------|
| YAML | Backup `clans.yml` / `wars.yml` before edits |
| SQLITE | Backup `clans.db` |
| MYSQL | Check credentials; ensure the plugin can create the DB |

Always stop the server or `/clan reload` after hand-editing YAML.

---

## GUI / messages broken

- Run `/clan reload` after editing `lang/en.yml`
- Ensure MiniMessage tags are valid
- Clan color placeholders should not be wrapped in `<white>` if you want clan color to show

---

## Performance tips

- Keep `visuals.particles.refresh-ticks` reasonable (20+)
- Disable holograms if unused: `visuals.holograms.enabled: false`
- Use SQLITE/MYSQL for large networks instead of huge YAML files

---

## Still stuck?

1. Enable `debug-mode: true` in `config.yml`, then `/clan reload` (or restart)
2. Reproduce the issue — look for `[Debug]` lines (cores, claims, wars, saves, disable steps)
3. Collect the full console log
4. Ask on [Discord](https://discord.gg/jDr2KZcGXk)

## Related

- [Installation](Installation.md)
- [Configuration](Configuration.md)
- [Commands](Commands.md)
