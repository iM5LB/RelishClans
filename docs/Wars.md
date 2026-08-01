# Wars & Diplomacy

War capture and alliance reference. **War actions require Premium** (`wars` license gate). Ally requests remain available on free.

## Alliances

```bash
/clan ally <clan>
```

Request or accept an alliance (Admin+). Allies appear in info and placeholders (`%relishclans_allies%`).

## Declaring War

```bash
/clan war <clan>
/clan surrender <clan>
```

**Role:** Admin+  
**Premium:** required

Cooldown: `cooldowns.war` in config. WorldGuard flag `relish-clans-war` can deny war actions in a region.

## Capture

1. Attackers enter the enemy core capture radius.
2. Standing near the core fills the capture progress (boss bar / titles when enabled).
3. When capture completes, **protection drops** in that territory for the war window.
4. War can end via surrender, capture window expiry, or admin force-end.

Core tier increases capture time and radius — see [Claims & Core](Claims.md).

## Admin Tools

```bash
/clan admin wars
/clan admin endwar <clanA> <clanB>
```

Requires `relishclans.admin`.

## Placeholders

| Placeholder | Meaning |
|-------------|---------|
| `%relishclans_at_war%` | `true` / `false` |
| `%relishclans_wars%` | Active war count |
| `%relishclans_enemies%` | Enemy clan names |

## Next Steps

- [Free vs Premium](FreeVsPremium.md)
- [Commands](Commands.md)
- [Claims & Core](Claims.md)
