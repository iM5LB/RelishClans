# Claims & Core

Territory and clan core reference.

## Claiming

| Command | Role | Description |
|---------|------|-------------|
| `/clan claim` | Officer+ | Claim current chunk |
| `/clan claim <radius>` | Officer+ | Chebyshev radius (`0` = 1 chunk, `1` = 3×3) |
| `/clan unclaim` | Officer+ | Unclaim current chunk |
| `/clan unclaim <radius>` | Officer+ | Radius unclaim |
| `/clan unclaim all` | Leader | Unclaim all (never removes core chunk) |
| `/clan autoclaim` | Officer+ | Toggle walk-to-claim |
| `/clan map` | Member+ | 11×11 chat map + particle borders |

Limits come from `settings.max-claims` plus premium expansion boosts. Optional `contiguous-claims` forces new claims to touch existing territory.

WorldGuard region flag `relish-clans-claim` can deny claiming in protected regions.

## Clan Core

On the **first claim**, RelishClans places the clan **core** (beacon block used as the clan home / war objective — not a vanilla beacon pyramid).

| Action | Notes |
|--------|-------|
| Teleport home | `/clan teleport` (aliases: `home`, `tp`) |
| Upgrade core | GUI — **Premium** for tier 2+ (`core_upgrades`) |
| Move core | `/clan movecore` or GUI — **Premium** (`core_relocator`) |

Higher tiers (configured under `core.levels` in `config.yml`):

- Stronger display block (Iron → Gold → Diamond → Netherite by default)
- Longer war capture time (`extra-capture-seconds`)
- Larger capture radius (`radius-bonus`)

Upgrade cost is paid from the **clan bank** first, then the player's wallet (Vault).

## Visuals

Players can toggle claim particles, titles, and boss bars via `/clan toggle` or the Visuals GUI. Claim particles default to **off**.

## Next Steps

- [Wars & Diplomacy](Wars.md)
- [Flags & Upgrades](Flags.md)
- [Free vs Premium](FreeVsPremium.md)
- [Configuration](Configuration.md)
