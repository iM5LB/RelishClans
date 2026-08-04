# Permissions

Complete permission and clan-role reference.

## Plugin Permissions

| Permission | Default | Description |
|------------|---------|-------------|
| `relishclans.command` | `true` | Use `/clan` commands |
| `relishclans.admin` | `op` | Admin bypass, `/clan reload`, `/clan admin`, claim for others |
| `relishclans.cooldown.bypass` | `op` | Bypass action cooldowns |

> `settings.bypass-permission` in config defaults to `relishclans.admin` and is also treated as a full bypass for cooldowns and many role checks.

## Clan Roles

Roles are stored per clan member (not LuckPerms groups). Higher roles inherit lower abilities.

| Role | Typical powers |
|------|----------------|
| **Member** | Use chest (if unlocked), fly (if unlocked), view info/GUI |
| **Officer** | Claim / unclaim / autoclaim, bank withdraw, invite |
| **Admin** | War, ally, move core, identity (color/tag), core upgrade, kick/promote (below self) |
| **Leader** | Rename, description, disband, transfer, unclaim all |

Exact checks live in managers; when in doubt, Officer+ for land, Admin+ for war/identity, Leader for destructive clan actions.

## LuckPerms Quick Setup

**Everyone:**
```bash
/lp group default permission set relishclans.command true
```

**Staff:**
```bash
/lp group admin permission set relishclans.admin true
/lp group admin permission set relishclans.cooldown.bypass true
```

## WorldGuard

When WorldGuard is installed, RelishClans registers region flags:

| Flag | Purpose |
|------|---------|
| `relish-clans-claim` | Allow/deny claiming in a region |
| `relish-clans-fly` | Allow/deny clan fly |
| `relish-clans-war` | Allow/deny war actions |

Set a flag to `deny` on a region to block that action there.

## Next Steps

- [Commands](Commands.md)
- [Configuration](Configuration.md)
- [Troubleshooting](Troubleshooting.md)
