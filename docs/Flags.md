# Flags & Upgrades

Economy-backed clan flags and unlocks.

## How Flags Work

Flags are purchased / upgraded from the clan GUI (Upgrades). Costs use Vault: **clan bank first**, then player balance.

Some flags are free/default. Others are gated as **advanced** or tied to premium feature keys (see [Free vs Premium](FreeVsPremium.md)).

Typical categories:

| Category | Examples |
|----------|----------|
| Protection | Build lock, container lock, explosion shield, animal / crop guards |
| Utility | Shared chest tiers, clan fly |
| Expansion | Claim boost, member boost (**Premium**) |
| Effects | Heal zone, XP boost (**Premium**) |

Exact ids, costs, and levels live under the flags section of `config.yml` — see [Configuration](Configuration.md).

## Clan Fly

```bash
/clan fly
```

Toggles the fly preference when the fly flag is unlocked. **Premium** gate: `clan_fly`. WorldGuard flag `relish-clans-fly` can deny fly in a region.

## Shared Chest

```bash
/clan chest
```

Opens shared clan storage. Higher chest tiers may be premium / paid unlocks depending on config.

## Claim Logs

```bash
/clan logs
```

Activity log GUI with optional movement replay (**Premium**: `claim_logs`). PacketEvents improves client-side replay; Paper Mannequin can work without it.

## Identity Tags

Free colors and free tags are always available. Paid / premium identity tags require the `premium_identity` gate.

```bash
/clan identity
/clan color <name>
/clan tag <symbol>
```

## Next Steps

- [Configuration](Configuration.md)
- [Free vs Premium](FreeVsPremium.md)
- [Commands](Commands.md)
