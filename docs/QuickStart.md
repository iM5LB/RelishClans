# Quick Start Guide

Get RelishClans running in a few minutes.

## Step 1: Install

1. Drop the JAR into `plugins/`
2. Restart the server
3. Confirm the RelishClans banner in console

## Step 2: Create a Clan

```bash
/clan create Relish
```

You become **Leader**. Default tag `⚔` and color `red` are applied automatically.

## Step 3: Claim Land

Stand in a chunk and run:

```bash
/clan claim
```

Your **clan core** is a beacon placed on the first claim. Upgrade tiers improve war defense without changing the block.

Optional:

```bash
/clan claim 1          # 3×3 area (Chebyshev radius)
/clan autoclaim        # claim while walking
/clan map              # chat map of nearby claims
```

## Step 4: Open the GUI

```bash
/clan gui
```

Java players get the chest inventory GUI. **Bedrock** players (Geyser + Floodgate) get native **forms** for the same menus. Clan chest still uses an inventory on both platforms.

From the menu you can manage roster, claims, bank, upgrades, war, identity, and visuals.

## Step 5: Invite Friends

```bash
/clan invite Steve
# Steve runs:
/clan join Relish
# or
/clan invites
```

## Step 6: Customize Identity (Admin+)

```bash
/clan identity
# or
/clan color gold
/clan tag ★
```

Names show as `★ Relish` with your color in holograms, titles, chat, and protection messages.

## Step 7: Upgrade the Core (optional, Premium)

In the GUI click **Upgrade Core** (Admin+). Tier 2+ requires a valid **license key**. Cost comes from the **clan bank** first, then the player's wallet.

Higher tiers:

- Stronger core block (Iron → Gold → Diamond → Netherite)
- More war capture time required
- Larger capture radius

## Step 8: War (optional, Premium)

Requires Premium (`wars`). Set `license-key` in config first — see [Free vs Premium](FreeVsPremium.md).

```bash
/clan war EnemyClan
```

Stand near the enemy core to capture. When protection falls, attackers can interact in that territory. Use `/clan surrender EnemyClan` to end early.

## You're Done!

Players can:

- Claim and protect land
- Share bank and chest
- Unlock flags / fly
- Fight wars over cores
- Show clan identity on scoreboards via PlaceholderAPI

## Next Steps

- [Configuration](Configuration.md) — limits, storage, cooldowns, flags
- [Commands](Commands.md) — full command list
- [Permissions](Permissions.md) — roles & nodes
- [PlaceholderAPI](PlaceholderAPI.md) — chat / TAB placeholders
