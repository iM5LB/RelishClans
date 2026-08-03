# Free vs Premium

RelishClans ships as one jar. Free features always work. Premium features unlock with a verified `license-key`.

## License Key

In `plugins/RelishClans/config.yml`:

```yaml
license-key: "YOUR-KEY-HERE"
```

Then restart or run `/clan reload` (admin). Check status with:

```bash
/clan license
```

Buy keys from the [M5LB Store](https://m5lb.run.place/?buy=relish-clans). Support: [Discord](https://discord.gg/jDr2KZcGXk).

If verification fails or the key is empty, **free features keep working**. Premium actions show an upgrade message instead of breaking the plugin.

## Free Features

| Area | Included |
|------|----------|
| Clan lifecycle | Create, disband, rename, description, leave, transfer |
| Roster | Invite, join, kick, promote, demote, roster GUI |
| Claims | Claim, unclaim, autoclaim, radius claim, map, contiguous mode |
| Core | First-claim core placement, teleport home (tier 1) |
| Bank | Deposit / withdraw (Vault) |
| Chest | Shared storage (base / free tier) |
| Allies | Request and accept alliances |
| Identity | Free colors and free icon tags |
| Flags | Default / free unlocks (basic protection) |
| Visuals | Titles, borders, preference toggles |
| Storage | YAML, SQLite, MySQL |
| Placeholders | Full `%relishclans_*%` set when PAPI is present |

## Premium Features

| Feature | What it unlocks |
|---------|-----------------|
| Wars | Declare war, surrender, war GUI / capture |
| Clan fly | Fly in claims |
| Core upgrades | Core tier 2+ |
| Core relocator | Move clan core |
| Expansion boosts | Claim / member boost flags |
| Claim effects | Heal zone, XP boost, and similar |
| Claim logs | Activity logs and movement replay |
| Advanced flags | Paid / non-default flag unlocks |
| Premium identity | Paid identity tags |

## Next Steps

- [Installation](Installation.md)
- [Configuration](Configuration.md) — `license-key` and economy settings
- [Flags & Upgrades](Flags.md)
- [Wars & Diplomacy](Wars.md)
